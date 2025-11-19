🤝 The purpose of this eval suite to tests whether an engineering agent (e.g., Archie) can perform quantitative and spatial reasoning in a thermal-management domain

### OVERVIEW:

LLM Reasoner
  - Receives tasks from YAML files
  - Performs task decomposition, tool/model selection, and chain-of-thought reasoning
  - Integrates outputs from neural models, non-neural tools, and human feedback

Neural Models:
  - Neural Model 1 Vision / CAD analysis
  - Neural Model 2 Quantitative Solver
  - Neural Model 3 Spatial / Physics reasoning

Non-Neural Tools & Human Feedback
  - Non-Neural Tools: APIs or CAD software invoked as needed
  - Human Feedback: advisory or validation for ambiguous or complex tasks

YAML Micro-Eval Suite
  - Structured task definitions: inputs, constraints, expected outputs, and evaluation checks
  - Defines the expected reasoning depth and validates hallucinations, units, and numerical consistency
  - Supports CI/CD integration for automated, repeatable evaluation

### What it does
The YAML micro-eval suite is the structured test layer sitting at the end of the pipeline. Each YAML file defines a task, for example: a cooling-system problem — 
with inputs, constraints, expected outputs, and checks for hallucinations, units, and reasoning depth.
When we run an eval:
- The LLM reasoner receives the task from YAML, interprets it, and decides which neural model or non-neural tool to use.
- Neural models perform their specialized computations (quantitative, spatial, CAD/vision).
- Any external tools or human feedback are invoked as needed.
- The outputs flow back to the LLM, which integrates them, ensures consistency, and generates a solution with reasoning steps.
- Finally, the validator checks the outputs against the expectations in the YAML file and reports pass/fail results.
- This setup allows us to test Archie end-to-end: we can feed thousands of structured tasks, ensure correct reasoning and outputs, and continuously benchmark performance in a CI/CD pipeline.

Written by Anna Gudkova on 11/18/2025
