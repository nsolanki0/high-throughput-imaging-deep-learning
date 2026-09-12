# Computational Infrastructure

## Purpose
This document records the computational infrastructure and software environment established to support the DeLTA v2 image-analysis workflow.

The existing laboratory setup required additional computational resources and a new software environment before the updated workflow could be deployed and tested on the experimental microscopy data.

## Hardware Upgrade
The local computational system was upgraded to support image-processing and deep-learning workloads.

The known hardware configuration includes:

| Component | Configuration |
|---|---|
| System memory | 128 GB RAM |
| GPU	| To be documented |
| Host operating system	| Windows 10 |

The hardware upgrade provided the additional computational capacity required for establishing and testing the updated image-analysis workflow.

## Operating Environment
Although the host system ran Windows 10, the DeLTA v2 environment was operated within Windows Subsystem for Linux (WSL), using a Debian-based Linux environment.

The resulting computational setup was:

```text
Windows 10
    │
    ▼
WSL / Debian
    │
    ▼
Python 3.11
    │
    ▼
Conda environment
    │
    ▼
DeLTA v2
```

Using WSL provided a Linux-based environment for configuring and testing the DeLTA workflow while retaining the existing Windows host system.

## Python and Environment Management
The DeLTA v2 environment was configured using:

- Python 3.11
- Conda environment management

The environment was configured with the software dependencies required by the DeLTA workflow and its deep-learning components.

Dependency versions can be documented further it the original environment information becomes available.

## GPU and CUDA Configuration
Both CUDA-enabled and non-CUDA configurations were tested during deployment.

The Python environment included NVIDIA CUDA 12.3-related packages, including components for the CUDA runtime, cuBLAS, NVRTC, NVCC, and CUDA profiling support.

Known environment components included:

```text
CUDA-related Python packages
        │
        ├── CUDA Runtime 12.3
        ├── cuBLAS
        ├── NVRTC
        ├── NVCC
        └── CUDA CUPTI
```

These packages formed part of the Python environment used for testing GPU-enabled deep-learning workflows.

The exact system-level CUDA driver version and GPU model are not currently documented and can be added if the original configuration details are recovered.

## DeLTA v2 Deployment
The upgraded computational environment was configured to support DeLTA v2.

The deployment process involved:

```text
Hardware upgrade
      │
      ▼
Windows 10 host
      │
      ▼
WSL / Debian
      │
      ▼
Python 3.11 + Conda
      │
      ▼
Dependency configuration
      │
      ▼
CUDA / non-CUDA testing
      │
      ▼
DeLTA v2
      │
      ▼
Workflow verification
```

Establishing the environment required practical configuration, compatibility testing, and troubleshooting across the operating system, Linux environment, Python dependencies, GPU configuration, and DeLTA workflow.

The deployment was carried out iteratively, with the environment progressively tested and refined until the workflow could be operated with the laboratory's experimental data.

## Testing and Verification
The computational environment was tested under both GPU-enabled and non-GPU configurations.
Testing focused on establishing that:

- the required software environment could be configured successfully;
- DeLTA v2 could be executed within the WSL/Debian environment;
- the relevant dependencies were available;
- GPU-enabled processing could be tested where supported;
- the workflow could be connected to the laboratory's microscopy data.

Specific troubleshooting details are not documented where the original records are unavailable.

## Reproducibility Notes
The following details are currently known:

| Category	| Details |
| Host OS	| Windows 10 |
| Linux environment	| WSL / Debian |
| RAM	| 128 GB |
| GPU	| To be documented |
| Python	| 3.11 |
| Environment management | Conda |
| DeLTA	| v2 |
| CUDA configuration	| CUDA-enabled and non-CUDA configurations tested |
| CUDA Python components	| CUDA 12.3-related NVIDIA packages |
| Dataset	| Laboratory microscopy data; not publicly available |

Additional hardware, driver, dependency, and configuration information can be added if the original records are recovered.

Sensitive laboratory data, credentials, and machine-specific configuration should not be included in the public repository.