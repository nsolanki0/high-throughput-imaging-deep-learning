# DeLTA v2 Integration

## Overview
This section documents the integration of DeLTA v2 into an existing laboratory workflow for deep-learning-assisted segmentation and tracking of bacterial cells in time-lapse microscopy data.

DeLTA was used by the laboratory because it provided the best framework at the time for automated or semi-automated cell segmentation and tracking for the requirements of the microscopy experiments.

By the time I joined the project, the laboratory had an established workflow based on DeLTA v1, including models trained on laboratory-specific microscopy data.

Following the release of DeLTA v2, the laboratory aimed to transition to the newer version. I was involved in establishing the new computational environment, integrating DeLTA v2 with the laboratory's existing data and workflow, testing the system under different computational configurations, and evaluating its behaviour on the experimental datasets.

The work was carried out iteratively over an extended period on a part-time basis.

**Official DeLTA documentation:** [Installation and setup](https://delta.readthedocs.io/en/latest/usage/installation.html)

## Transition from DeLTA v1 to v2
Before the transition, the laboratory was already using DeLTA v1 for segmentation and tracking.

The existing workflow included models that had been trained on laboratory-specific microscopy data through a separate transfer-learning process. Model training was an iterative laboratory activity, with additional training datasets incorporated over time to improve performance on the experimental data.

When DeLTA v2 became available, the objective was to establish the newer architecture while retaining the benefit of the existing laboratory-specific work.

The transition can therefore be summarised as:

```text
Existing laboratory workflow
            │
            ▼
        DeLTA v1
            │
            ▼
Models trained on
laboratory-specific data
            │
            │
            ▼
       DeLTA v2
            │
            ▼
New computational environment
            │
            ▼
Integration with laboratory data
            │
            ▼
Testing and evaluation
            │
            ▼
Iterative refinement
```

An important part of the transition was subsequently testing whether the existing v1-trained models could be used with the v2 architecture. This approach worked and provided a practical route for taking advantage of the newer DeLTA framework while retaining models developed using the laboratory's accumulated training data.

## Computational Setup
The DeLTA v2 workflow was established on an upgraded local computational system.

The host operating system was Windows 10, while the DeLTA environment was operated within Windows Subsystem for Linux (WSL) using a Debian-based Linux environment.

The computational setup involved testing both CUDA-enabled and non-CUDA configurations in order to establish and verify the working environment.

The resulting setup can be represented as:

```text
Windows 10
    │
    ▼
WSL / Debian
    │
    ├───────────────┐
    ▼               ▼
Non-CUDA testing   CUDA-enabled testing
    │               │
    └───────┬───────┘
            ▼
       DeLTA v2
            │
            ▼
Laboratory microscopy data
```

Establishing the environment required substantial practical configuration and troubleshooting.

At the time, the available documentation and existing laboratory setup did not provide a straightforward deployment path. I was also working with this type of computational problem for the first time and had limited direct support during the process.

Consequently, a significant part of the work involved reconstructing how the existing workflow operated, understanding the interaction between the software environment and the laboratory's data, testing different configurations, and progressively establishing a functioning DeLTA v2 workflow.

Specific configuration and troubleshooting details are documented separately where they are known and can be reproduced.

## Integration with Laboratory Data
Once the computational environment was established, DeLTA v2 needed to be integrated with the laboratory's existing microscopy workflow.

This involved working across several components:

```text
Laboratory microscopy data
            │
            ▼
      Data preparation
            │
            ▼
       Input handling
            │
            ▼
         DeLTA v2
       ┌────┴────┐
       ▼         ▼
 Segmentation  Tracking
       │         │
       └────┬────┘
            ▼
       Output handling
            │
            ▼
      Post-processing
```

The integration therefore involved more than installing the software. The workflow had to be tested against the characteristics of the laboratory's real experimental datasets and connected to the subsequent processing and analysis stages.

## Iterative Evaluation and Refinement
The DeLTA v2 workflow was developed and evaluated iteratively.

The general process was:

```text
Configure workflow
        │
        ▼
Run on laboratory data
        │
        ▼
Inspect segmentation
and tracking outputs
        │
        ▼
Identify recurring errors
        │
        ▼
Modify configuration
or processing approach
        │
        ▼
Re-run on the data
        │
        ▼
Compare and evaluate
        │
        └──────────────► Repeat
```

Manual checking was used to identify segmentation and tracking errors, while testing on the same experimental datasets allowed the behaviour of different workflow configurations and models to be compared.

Particular attention was given to whether errors observed in the previous workflow continued to occur after changes were introduced.

This provided a practical before-and-after assessment of the workflow rather than relying solely on a single aggregate performance metric.

## Existing Models with the DeLTA v2 Architecture
A later stage of the work involved testing the existing models developed through the laboratory's DeLTA v1 workflow with the DeLTA v2 architecture.

The objective was to determine whether the existing laboratory-specific model knowledge could be retained while benefiting from the newer version of the DeLTA framework.

The approach was successful, allowing the v1-trained models to operate with the v2 architecture.

This formed an important part of the transition from the established laboratory workflow to the newer DeLTA implementation.

## Contribution Boundary
My involvement covered the practical transition to and operation of DeLTA v2, including:
- establishing the computational environment;
- configuring the DeLTA v2 workflow;
- working with the WSL/Debian environment;
- testing CUDA and non-CUDA configurations;
- integrating laboratory microscopy data;
- testing existing laboratory models with the v2 architecture;
- inspecting segmentation and tracking outputs;
- identifying recurring image-analysis errors;
- evaluating changes to the workflow;
- iteratively refining and testing the resulting pipeline.

The transfer-learning/model-training step itself was performed separately within the laboratory and was not independently carried out by me. However, I was involved in the broader model-development workflow, including preparation and annotation of training/evaluation data, evaluation of model outputs, identification of failure modes, and iterative assessment of model and workflow performance.

The distinction is therefore specifically that I did not perform the model-training step itself, rather than that I was uninvolved in model development or evaluation.

## Relationship to the DeLTA Project
DeLTA is externally developed research software. This repository does not reproduce or claim ownership of the DeLTA framework.

Instead, this section documents how DeLTA v2 was integrated into a specific laboratory workflow and how the transition from an established DeLTA v1-based workflow was approached.

## Reproducibility Notes
Known environment details are recorded here where available:

| Category | Details |
|---|---|
| Host operating system | Windows 10 |
| Linux environment | WSL / Debian |
| DeLTA version | v2 |
| GPU acceleration | CUDA-enabled and non-CUDA configurations tested |
| Hardware | See `computational-infrastructure/README.md` |
| Python | 3.11 |
| Environment management | Conda |
| Dependency details | To be documented |
| Dataset details | Laboratory data; not publicly available |

Sensitive laboratory data, credentials, and machine-specific configuration should not be included in the public repository.

## Related Documentation
- `../../computational-infrastructure/README.md` — computational infrastructure and environment setup
- `../../docs/workflow-overview.md` — broader computational workflow
- `../../analysis/README.md` — downstream quantitative analysis
