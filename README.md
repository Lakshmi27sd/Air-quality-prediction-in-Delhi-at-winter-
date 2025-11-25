

Supplementary Materials — Reproducibility
Contents:
- train_centralized.py  : multi-output C-TL-LSTM-MHA script
- environment.txt       : hardware & software details
- requirements.txt      : Python dependencies
- timing_procedure.txt  : how timings were measured

To reproduce timings:
1. `pip install -r requirements.txt`
2. `python eval_and_time.py`
Outputs: timings/per_model_timings.csv, timings/per_model_summary.csv

Hardware & Software Environment
- GPU: NVIDIA RTX 2080 Ti
- CPU: Intel® Core™ i9-9900K @ 3.60 GHz
- RAM: 64 GB
- OS: Windows 10 (or Ubuntu 20.04, whichever you used)
- Python: 3.9
- TensorFlow: 2.11
- CUDA: 11.3
- cuDNN: 8.x
- Key libraries:
  - numpy, pandas, matplotlib, scikit-learn, seaborn, scipy
  - tensorflow-addons (if used)

requirements.txt
tensorflow==2.11
numpy==1.24
pandas==1.5
matplotlib==3.7
scikit-learn==1.2
scipy==1.10
seaborn==0.12

timing_procedure.txt
Wall-clock times were measured using Python’s time.perf_counter() around the complete model.fit() call.
For the baseline, five univariate models (PM₂.₅, PM₁₀, NO₂, CO, SO₂) were trained sequentially with identical hyperparameters and epochs.
The total baseline time equals the sum of those five runs.
The centralized C-TL-LSTM-MHA model was trained once as a multi-output network.
Each configuration was run three times (N = 3); mean ± SD values are reported in per_model_summary.csv.

model,run_id,elapsed_seconds
PM25,run1,2.13
PM25,run2,2.12
...
centralized,run1,8.25
centralized,run2,8.23
centralized,run3,8.24


