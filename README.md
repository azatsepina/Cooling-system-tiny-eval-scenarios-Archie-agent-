The purpose of this eval suite to tests whether an engineering agent (e.g., Archie) can perform quantitative and spatial reasoning in a thermal-management domain

### OVERVIEW:


                ┌─────────────────────┐
                │  LLM Reasoner       │
                │  - Task decomposition
                │  - Tool selection
                │  - Chain-of-thought reasoning
                │  - Output integration
                └─────────┬───────────┘
                          │
          ┌───────────────┼─────────────────┐
          │               │                 │
┌─────────▼────────┐ ┌────▼──────────┐ ┌────▼─────────┐
│ Neural Model 1   │ │ Neural Model 2│ │ Neural Model 3│
│ (Vision / CAD)   │ │s(Performans e)│ │ (Spatial /    │
│                  │ │ estimatio)    | │ Physics)      │
└─────────┬────────┘ └────┬──────────┘ └────┬─────────┘
          │               │                 │
          └──────┬────────┴────────┬────────┘
                 │                 │
         ┌───────▼─────────┐ ┌─────▼─────────┐
         │ Non-Neural Tool │ │ Human Feedback│
         │ (APIs / CAD     │ │ Advisory /    │
         │ software)       │ │ Validation)   │
         └─────────┬───────┘ └───────────────┘
                   │
                   ▼
        ┌─────────────────────────┐
        │ YAML Micro-Eval Suite   │
        │ - Task definitions      │
        │ - Input parameters      │
        │ - Expected outputs      │
        │ - Checks & validations  │
        │ - CI/CD integration     │
        └─────────────────────────┘
### What it does
The YAML micro-eval suite is the structured test layer sitting at the end of the pipeline. Each YAML file defines a task, for example: a cooling-system problem — 
with inputs, constraints, expected outputs, and checks for hallucinations, units, and reasoning depth.
When we run an eval:
The LLM reasoner receives the task from YAML, interprets it, and decides which neural model or non-neural tool to use.
Neural models perform their specialized computations (quantitative, spatial, CAD/vision).
Any external tools or human feedback are invoked as needed.
The outputs flow back to the LLM, which integrates them, ensures consistency, and generates a solution with reasoning steps.
Finally, the validator checks the outputs against the expectations in the YAML file and reports pass/fail results.
This setup allows us to test Archie end-to-end: we can feed thousands of structured tasks, ensure correct reasoning and outputs, and continuously benchmark performance in a CI/CD pipeline.”
