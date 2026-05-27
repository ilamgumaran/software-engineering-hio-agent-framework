# Meta — Agentic Development Practices

## Agent Tooling

- **CodeCompose**: Internal AI code-completion tool (not public), 22% acceptance rate across 9 languages
- **Confucius Code Agent (CCA)**: Open-sourced, 59% resolve rate on SWE-Bench-Pro
- **Llama Stack**: Standardized interfaces for building agentic apps with Llama models
- **Prompt Guard**: Classifier model for detecting prompt injection attacks
- **Llama Guard 3**: Multi-class content safety classifier

## Repository Configuration

### No Standard File Convention
Meta does not publish a standardized agent-instruction file (no AGENTS.md equivalent). Their approach is **SDK-driven**: the Confucius SDK's Agent Experience (AX) layer programmatically structures what context the agent receives.

### Confucius SDK Architecture
Three axes of separation:
- **Agent Experience (AX)**: Structured context for the model — concise, relevant, avoids distraction
- **User Experience (UX)**: Human-readable logs and traces
- **Developer Experience (DX)**: Observability, prompt control, memory management

Includes persistent note-taking system for cross-session learning and a meta-agent for automated build-test-improve cycles.

### Llama Stack
Standard API layer across the development lifecycle:
- Model endpoints, safety shields, tool definitions in YAML/JSON configuration
- Safety shields attachable to agent configurations
- Integration with LlamaIndex for RAG and orchestration

## Security Approach

### Agents Rule of Two
An agent must not simultaneously:
1. Process untrusted input
2. Access sensitive data
3. Mutate state

If all three are needed, human-in-the-loop is required. Inspired by Chromium's security model.

### Safety Models
- **Prompt Guard**: Detects both direct jailbreaks and indirect injection in LLM inputs
- **Llama Guard 3**: Content safety classification for filtering inputs and outputs
- **CyberSecEval**: Benchmarks for evaluating AI code generation security risks
- **Purple Llama**: Security-focused tools for responsible AI deployment
- **AutoPatchBench**: Benchmark for AI security patching of C/C++ fuzzing bugs

## Sources
- Confucius Code Agent: https://arxiv.org/abs/2512.10398
- CodeCompose: https://arxiv.org/abs/2305.12050
- Agents Rule of Two: https://ai.meta.com/blog/practical-ai-agent-security/
- AutoPatchBench: https://engineering.fb.com/2025/04/29/ai-research/autopatchbench-benchmark-ai-powered-security-fixes/
- Llama Stack Apps: https://github.com/meta-llama/llama-stack-apps
