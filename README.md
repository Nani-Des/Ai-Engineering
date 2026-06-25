# Ai-Engineering

Practice and teaching notebooks for core AI engineering topics: perceptron training, TensorFlow/Keras fundamentals, and an agentic AI primer — designed to run interactively (Jupyter/Colab) or headless for reproducible runs.

Overview
- A collection of Jupyter notebooks that demonstrate step-by-step model development: from elementary perceptron training to practical Keras workflows and a crash course in TensorFlow 2.x.
- Notebooks include runnable code, plotted outputs, and explanatory cells intended for hands-on learning and quick experiment reproduction.
- Each notebook is self-contained and can be executed in Google Colab (GPU available) or locally via Jupyter/JupyterLab. Headless execution using nbconvert or papermill is supported for automated testing.

Notebooks (what to expect)
- Dev't_Training_the_Perceptron.ipynb — hands-on perceptron training, loss landscapes, learning-rate experiments, and convergence diagnostics.
- IntroKerasTF.ipynb — building models with Keras Functional and Sequential APIs, data pipelines, callbacks, saving/loading models.
- TensorFlow_2_0_+_Keras_Crash_Course.ipynb — concise TF2 basics, eager execution examples, gradient tape, simple training loops.
- Agentic AI — a static HTML primer (Agentic AI — 2026 — KrishnaIK.html) with conceptual notes on agentic architectures.

Tech stack
- Primary: Jupyter Notebooks (ipynb)
- Typical libraries used in notebooks: TensorFlow/Keras, NumPy, pandas, matplotlib, seaborn, scikit-learn, and ipywidgets
- Execution environments: Jupyter / JupyterLab, Google Colab

Quick setup — run locally
1. Clone the repo
```
git clone https://github.com/Nani-Des/Ai-Engineering.git
cd Ai-Engineering
```
2. Create and activate a virtual environment
```
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```
3. Install recommended packages (minimal)
```
pip install --upgrade pip
pip install jupyterlab notebook numpy pandas matplotlib seaborn scikit-learn ipywidgets
# For TensorFlow (CPU)
pip install tensorflow
# or for GPU, install a matching TensorFlow wheel per your CUDA/cuDNN
```
4. Start JupyterLab
```
jupyter lab
```
Open the notebook you want to run (e.g., IntroKerasTF.ipynb) in the browser.

Run directly in Google Colab
- No local install required. In Colab choose Runtime → Change runtime type → GPU for acceleration.
- Open any notebook with this pattern in a browser:
```
https://colab.research.google.com/github/Nani-Des/Ai-Engineering/blob/main/IntroKerasTF.ipynb
```
Replace the filename in the URL to open other notebooks.

Headless / reproducible execution
- Execute a single notebook headless with nbconvert:
```
jupyter nbconvert --to notebook --execute "IntroKerasTF.ipynb" --ExecutePreprocessor.timeout=600 --output "IntroKerasTF.executed.ipynb"
```
- Run multiple notebooks in a directory (simple bash loop):
```
for nb in *.ipynb; do
  jupyter nbconvert --to notebook --execute "$nb" --ExecutePreprocessor.timeout=600 --output "exec_$nb"
done
```
- For parameterized runs or CI-friendly execution, use papermill:
```
pip install papermill
papermill Dev't_Training_the_Perceptron.ipynb out.ipynb -p learning_rate 0.1
```

Repro tips and GPU notes
- Notebook outputs may depend on package versions (TensorFlow, NumPy). Pin versions before long experiments (create a requirements.txt with exact versions).
- Use Colab or a local CUDA-enabled TensorFlow build for GPU acceleration. Select TensorFlow wheel matching your CUDA/cuDNN (see https://www.tensorflow.org/install).
- If you need exact reproducibility, set RNG seeds in notebook cells and record package versions (`pip freeze > requirements.txt`).

Project layout
```
README.md
Agentic AI — 2026 — KrishnaIK.html    # primer / article
Dev't_Training_the_Perceptron.ipynb   # perceptron experiments
IntroKerasTF.ipynb                    # Keras TF2 examples
TensorFlow_2_0_+_Keras_Crash_Course.ipynb
```

Execution checklist
- If running locally: ensure Python 3.8+ (3.10/3.11 recommended), JupyterLab, and TensorFlow installed.
- For GPU runs: install the matching TensorFlow wheel for your CUDA version or use Colab GPU.
- For automated CI/test runs: use nbconvert/papermill and increase ExecutePreprocessor.timeout if long training cells exist.

Status
Educational / ready for interactive experiments.

Author
- Nani-Des — https://github.com/Nani-Des

If you'd like, I can:
- produce a pinned requirements.txt (with tested package versions) for local reproducibility,
- add a small Makefile or script to run all notebooks headless and collect outputs,
- or extract the core code cells into runnable Python scripts for production usage.
