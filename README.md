# Artifact-Based Diagnostic Learning Analytics via LLMs (The MCD-FO Framework)



## Overview
This repository contains the full prompt engineering implementation and evaluative knowledge base for the **Multidimensional Cognitive Diagnosis–Feedback–Orchestration (MCD-FO) framework**. 

As presented in our manuscript, this framework utilizes a rubric-constrained Large Language Model (LLM) to systematically derive cognitive-diagnostic profiles from students' programming artifacts and deliver adaptive pedagogical scaffolding. By making this implementation openly available, we aim to ensure methodological transparency, address prompt engineering nuances, and maximize transferability for future educational technology research.

## Repository Structure
To maintain a strict boundary between diagnostic reasoning and pedagogical intervention, the LLM agent is governed by a **Dual-Stage Prompting Architecture**:

* 📂 **`System_Prompts/`**
  * `Stage1_Internal_Diagnosis.md`: The Chain-of-Thought (CoT) system prompt forcing the agent to execute a hidden internal analysis and output a structured JSON diagnostic profile (Indicator, Status, Root Cause) before generating any visible feedback.
  * `Stage2_Adaptive_Scaffolding.md`: The pedagogical system prompt that translates the JSON diagnosis into natural language feedback using the Modeling-Coaching-Reflection (MCR) strategy gradient.
* 📂 **`Knowledge_Base/`**
  * `Evaluative_Knowledge_Base.md`: The absolute "ground truth" injected into the LLM. It strictly defines the 29 observable indicators across 4 dimensions (SU, AR, DS, MR) and the proficiency level progression (Deficit, Emerging, Consolidated). The LLM is strictly constrained to infer states *only* from behavioral traces (e.g., source code, runtime traces, submission intervals).
* 📂 **`Few_Shot_Exemplars/`**
  * `Exemplar_Modeling.md`: Example of a High-Support intervention.
  * `Exemplar_Coaching.md`: Example of a Medium-Support (localization hint) intervention.
  * `Exemplar_Reflection.md`: Example of a Low-Support (Socratic questioning) intervention.

## Core Dimensions Addressed
The evaluative knowledge base constraints the LLM to diagnose across four cognitive dimensions:
1. **Syntactic Understanding (SU):** Mastery of language grammar and formal code expression.
2. **Algorithmic Reasoning (AR):** Procedural cognitive skills, logic structuring, and control flow.
3. **Debugging Strategies (DS):** Efficiency and systematicity of error resolution processes.
4. **Metacognitive Regulation (MR):** Internal regulatory processes inferred *strictly* from observable behavioral traces (e.g., temporal spacing, reflection notes).

## Adaptive Scaffolding Gradient (MCR)
The Stage 2 agent is deterministically triggered by the Stage 1 JSON output to apply one of three support levels:
* **Incorrect $\rightarrow$ Modeling (High Support):** Provides abstract structural patterns or counter-examples.
* **Partial $\rightarrow$ Coaching (Medium Support):** Provides localization hints to guide attention.
* **Correct $\rightarrow$ Reflection (Low Support):** Withdraws explicit scaffolding and initiates Socratic questioning.

## How to Use
Researchers and educators can replicate this diagnostic pipeline by integrating these markdown prompts into any standard LLM API (e.g., OpenAI GPT-4o). 
1. Inject the `Evaluative_Knowledge_Base.md` into the developer/system message.
2. Provide the `Stage1_Internal_Diagnosis.md` along with the specific student's artifact data (code, compiler error, submission interval).
3. Pass the resulting JSON directly into `Stage2_Adaptive_Scaffolding.md` to generate the final pedagogical intervention.

## Citation
If you utilize this prompt architecture or the evaluative knowledge base in your research, please cite our corresponding paper:

> [Kai liang]. (2026). Artifact-Based Diagnostic Learning Analytics via Large Language Models: A Case Study in Programming Classroom. *Educational Technology Research and Development (ETR&D)*. [Status: Under Review].

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
