
# Quantum Cloud Simulation Environment

This repository contains the SigSim2025 artifact: a digital‑twin simulation of a quantum cloud environment, including event‑driven job brokering, dynamic/predefined job feeds, and device maintenance cycles. It supports both serial and parallel scheduling policies across multiple quantum devices.

## Prerequisites

- Git  
- Docker (recommended) or Python 3.8+

## Cloning the repository
To clone the repository, run the following command. 
```bash
git clone https://github.com/quantumcloudsim/SigSim2025.git
```

## Python Environment (if not using Docker)

1. **Create & activate a virtual environment**  
   For macOS/Linux, run the following commands: 
   ```bash
   cd SigSim2025
   python3 -m venv .venv
   source .venv/bin/activate       # macOS/Linux
   ```
   For Windows PowerShell, run the following: 
   ```bash
   cd SigSim2025
   python3 -m venv .venv
   .venv\Scripts\Activate.ps1      # Windows PowerShell
   ```
3.	**Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
3.	**Run Use‑Case scripts**
   ```bash
   python3 Section-6-Use-case-1.py
   python3 Section-6-Use-case-2.py
   ```
## Containerized Artifact (recommended)
### We provide a Docker container for reproducibility across systems.

1. **Build the Docker image**
   ```bash 
   cd SigSim2025
   docker build -t sigsim2025:latest .
   ```
2. **Verify the environment**

   ```bash
   docker run --rm -it sigsim2025:latest bash
    # Inside container:
    #   python --version
    #   pip list
    #   ls
    #   exit
   ```
3. **Run the program**

    ```bash
    docker run --rm sigsim2025:latest
    ```
## Repository Structure

   ```bash
      SigSim2025/
      ├── Dockerfile
      ├── README.md
      ├── requirements.txt
      ├── qcloud.py
      ├── Section-6-Use-case-1.py
      ├── Section-6-Use-case-2.py
      ├── QCloud/                  # Core simulation code
      ├── configs/                 # Configuration files
      ├── results/                 # Experiment outputs
      ├── synth_job_batches/       # Job definitions
      └── utility_functions/       # Helper scripts
   ```
## Citation 
If you use this artifact in your work, please cite:
  
   ```
     @misc{SigSim2025,
       author       = {A Digital Twin of Scalable Quantum Clouds},
       title        = {{Submission to SigSim2025}},
       year         = {2025},
       doi          = {10.5281/zenodo.15099199},
       howpublished = {\url{https://github.com/quantumcloudsim/SigSim2025.git}}
     }
   ```
