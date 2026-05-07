# batch-order-processing (template)

## What This Repo Does
Processes daily order fulfillment in two batch jobs:
- `OrderValidationJob`: Validates pending orders against inventory (runs 02:00 UTC)
- `OrderFulfillmentJob`: Sends validated orders to warehouse API (runs 03:00 UTC)

`OrderFulfillmentJob` depends on `OrderValidationJob` completing successfully.

## How to Build and Test
- Build: `./gradlew build`
- Test: `./gradlew test`
- Run locally: `./gradlew bootRun --args='--spring.profiles.active=local'`
- Run specific job: `./gradlew bootRun --args='--job=orderValidation'`

## Key Design Decisions
- Chunk size is 500 (tuned for our order volume ~50K/day)
- Uses cursor-based reader to avoid loading all orders into memory
- Dead letter queue: `order-processing-dlq` in SQS
- Checkpoint table: `batch_processing_checkpoint` in orders DB

## What Agents Need to Know
- The warehouse API has a rate limit of 50 req/s. The writer uses a token
  bucket to stay under this.
- Order amounts are in cents (integer), never floating point dollars.
- PII fields (customer_name, address) are encrypted at rest. Use
  `EncryptionService` for any new PII fields.
- NEVER modify the job schedule without updating the runbook AND notifying
  the on-call channel (`#ops-batch-jobs`).

## Override: Logging
This repo uses JSON-structured logging (logstash-logback-encoder),
not the org default plain text format.
