
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

## Example Code

1.	**Prepare the Environment:**
Make sure you have created a virtual environment and installed all required packages.

2.	**Run the Simulation:**
Save the following sample code in a Python file (e.g., simulate.py):

         ```
  	      python
         from QCloud import *

         ibm_kawasaki = IBM_Kawasaki(env=None, name="ibm_kawasaki", printlog=True)
         qcloudsimenv = QCloudSimEnv(
            devices=[ibm_kawasaki],
            broker_class=ParallelBroker,
            job_feed_method="generator",
            job_generation_model=lambda: random.expovariate(lambd=0.1)
         )
         qcloudsimenv.run(until=100)
         ```
  	
This example demonstrates how to set up and run a simulation using the QCloud framework. The code initializes a device (using the IBM_Kawasaki class) and runs a simulation environment (QCloudSimEnv) with a custom job generation model. The simulation runs until a specified time limit.

Overview
- Device Initialization:
An instance of IBM_Kawasaki is created. This represents a device or service in the QCloud simulation environment.
-	Simulation Environment Setup:
A simulation environment (QCloudSimEnv) is set up with:
-	A list of devices (in this case, a single IBM_Kawasaki instance).
-	A broker class (ParallelBroker) that handles job scheduling.
-	A job feed method (generator) that dynamically creates jobs.
-	A job generation model based on an exponential distribution (using random.expovariate).
-	Simulation Execution:
The simulation environment is executed for a specified duration (until 100 time units).

3.	**Observe the Output:**
The simulation will execute, logging events to your console (as specified by printlog=True). You can review the simulation steps and results, which might include job scheduling, device processing, and more depending on how the QCloud framework is designed.

**Code Explanation**

-	IBM_Kawasaki Initialization:
   -	env=None: No specific environment passed during initialization.
   -	name="ibm_kawasaki": Assigns a name to the device instance.
   -	printlog=True: Enables logging to standard output.
-	QCloudSimEnv Setup:
   -	devices=[ibm_kawasaki]: Registers the device to be used in the simulation.
   -	broker_class=ParallelBroker: Uses the ParallelBroker class to manage job distribution.
   -	job_feed_method="generator": Configures the environment to generate jobs using a generator.
   -	job_generation_model=lambda: random.expovariate(lambd=0.1): Defines a job generation model where jobs arrive following an exponential distribution.
-	qcloudsimenv.run(until=100): Runs the simulation for 100 time units. You can modify this value to run the simulation for a different period.


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
