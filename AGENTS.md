# AGENTS

This repository: **deeplearning.ai** contains short courses from DeepLearning.AI presented as Jupyter notebooks. The repo's primary contents are instructional notebooks (tutorials, exercises, and demos) focused on Generative AI, tools, and practical skills.

Purpose of this file
- Give Copilot/agents quick orientation about the repository, how to run and test notebooks, and repository conventions.

Repository overview
- Language: Jupyter Notebook (.ipynb)
- Content: course notebooks, exercises, datasets (if any), and supporting assets (images, scripts).
- Intended users: learners, instructors, and contributors who want to run and extend course notebooks.

How to run notebooks (developer environment)
1. Recommended: Create a Python virtual environment and install dependencies listed in a requirements.txt (if present) or use the provided environment in the course.
   - python -m venv .venv
   - source .venv/bin/activate  # or .venv\Scripts\activate on Windows
   - pip install -r requirements.txt
2. Launch JupyterLab or Notebook:
   - jupyter lab
   - or: pip install jupyter
         jupyter notebook
3. For reproducible runs, prefer running notebooks with nbclient or papermill in CI.

Notebook testing and CI
- If CI is present, it should run notebooks headlessly (nbconvert/nbclient/papermill) and verify no errors.
- Keep cells that require interactive input minimal or guard them behind environment checks.

Repository conventions
- Notebooks should be named with a leading index when part of a course: `01-intro.ipynb`, `02-training.ipynb`.
- Keep large datasets out of the repo; reference external dataset sources or store them under `data/` with a small sample and a script to download full data.
- Add a short README in subdirectories explaining contents and how to run any included notebooks.

Recommended agents and responsibilities
- Course Curator
  - Purpose: Review notebooks for pedagogical flow, missing explanations, and broken cells.
  - Example prompt: "Review 01-intro.ipynb for clarity and suggest where to add short explanations or diagrams."

- Notebook Runner (CI helper)
  - Purpose: Run notebooks headlessly, capture runtime errors, and produce a report of failing notebooks and error traces.
  - Example prompt: "Run all notebooks in notebooks/ using nbclient and report any cells that raise exceptions, including stack traces."

- Dependency Assistant
  - Purpose: Inspect notebooks for imported packages, suggest a consolidated requirements.txt, and point out version-sensitive packages.
  - Example prompt: "Scan notebooks for import statements and produce a requirements.txt with common versions."

- Example Generator
  - Purpose: Generate small focused example notebooks or short exercises based on a topic (e.g., "fine-tuning a diffusion model - minimal example").
  - Example prompt: "Create a minimal notebook demonstrating how to fine-tune a small diffusion model on a toy dataset. Include short explanations and runnable code cells."

- Doc Writer
  - Purpose: Create or improve README, course outlines, and inline notebook explanations.
  - Example prompt: "Write a 200-word README for the generative-ai course outlining learning goals and required setup."

Guidelines for agents (do's and don'ts)
- Do: Make small, reversible changes to notebooks and push PRs with clear explanations.
- Do: Run notebooks locally (or in CI) to ensure changes don't break execution.
- Don't: Commit large datasets directly to the repo.
- Don't: Make assumptions about environment-specific secrets or private datasets — ask for instructions.

If you are an automated agent running in CI
- Use a non-interactive runner (nbclient/papermill) and set a timeout for long-running cells.
- Collect stdout/stderr and attach logs to the CI job for debugging.

Contact / maintainers
- If present, check the repository's CODEOWNERS or the README for maintainers and contributor guidelines.

Notes
- This AGENTS.md is intentionally concise; extend it with project-specific setup instructions (GPU requirements, Dockerfiles, dataset download scripts) as those become available.
