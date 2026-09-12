# Workflow Overview

## Purpose
This document describes the architecture of the computational workflow used to transform longitudinal microscopy data from _Escherichia coli_ experiments into cell-level measurements for downstream quantitative analysis.

The workflow connected experimental imaging, image preparation, manual annotation, deep-learning-assisted segmentation and tracking, validation, post-processing, and R-based quantitative analysis.

The emphasis of this document is on the relationship between these computational stages rather than on reproducing the original laboratory code or datasets.

## End-to-End Workflow
The overall computational workflow can be represented as:

```text
                    EXPERIMENTAL DATA
                           │
                           ▼
                High-throughput microscopy
                           │
                           ▼
                   Data preparation
                           │
                           ▼
                    Preprocessing
                           │
                           ▼
                  Manual annotation
                           │
                           ▼
             Deep-learning-assisted analysis
                           │
                    ┌──────┴──────┐
                    ▼             ▼
               Segmentation    Tracking
                    │             │
                    └──────┬──────┘
                           ▼
                 Validation / Quality Control
                           │
                           ▼
                    Post-processing
                           │
                           ▼
                    Cell-level data
                           │
                           ▼
                     R analysis
                           │
                           ▼
                Biological interpretation
```

The deep-learning component was therefore integrated into a broader image-analysis workflow rather than treated as an isolated machine-learning task.

### Computational Infrastructure Layer
The image-analysis workflow required computational resources capable of supporting high-throughput image processing and deep-learning-assisted analysis.

The infrastructure and deployment process can be represented as:

```text
                 COMPUTATIONAL INFRASTRUCTURE

                  Hardware requirements
                           │
                    ┌──────┴──────┐
                    ▼             ▼
              System memory      GPU
                    │             │
                    └──────┬──────┘
                           ▼
                Computational environment
                           │
                           ▼
                  Software configuration
                           │
                           ▼
                  Dependency configuration
                           │
                           ▼
                    DeLTA v2 setup
                           │
                           ▼
                    Dataset integration
                           │
                           ▼
                    Workflow testing
                           │
                           ▼
                 Troubleshooting / debugging
                           │
                           ▼
                  Operational workflow
```

The infrastructure layer supported deployment of the updated DeLTA workflow and its integration with the experimental imaging data.

Further details are documented in `computational-infrastructure/README.md`.

### 1. Experimental Imaging Data
The workflow operated on longitudinal microscopy datasets generated from _E. coli_ experiments using a mother-machine microfluidic platform.

The resulting image sequences provided the input for the computational workflow and required preparation before automated analysis.

The key computational requirement was to preserve sufficient information across successive frames to support reliable cell segmentation, tracking, and downstream cell-level measurements.

### 2. Data Preparation
Experimental microscopy data were prepared and organised before entering the image-analysis workflow.

This stage included activities such as:

- organising imaging datasets;
- preparing image sequences;
- selecting datasets for processing;
- formatting inputs;
- checking image quality and suitability for analysis.

The purpose was to provide consistent inputs for subsequent preprocessing, annotation, segmentation, and tracking.

The original laboratory data structure and datasets are not reproduced in this repository.

### 3. Preprocessing
Preprocessing prepared the microscopy data for subsequent image analysis.

At the workflow level, this stage provided the transition between the organised experimental image data and the inputs used for annotation and model-based processing.

```text
Experimental image data
          │
          ▼
    Data preparation
          │
          ▼
       Preprocessing
          │
          ▼
    Analysis-ready inputs
```

Specific preprocessing operations are not documented here where the original implementation details are unavailable.

### 4. Manual Annotation
Manual annotation provided labelled data for evaluating automated image analysis and supporting the broader model-development workflow.

Representative microscopy images were annotated to identify bacterial cells and establish reference information for segmentation assessment.

The annotations supported:

- evaluation of segmentation outputs;
- identification of segmentation failure modes;
- comparison between automated outputs and reference annotations;
- subsequent model development within the wider project.

The relationship between manual annotation and automated analysis can therefore be represented as:

```text
                    Microscopy images
                           │
                ┌──────────┴──────────┐
                ▼                     ▼
        Manual annotation     Automated analysis
                │                     │
                └──────────┬──────────┘
                           ▼
                    Evaluation /
                     validation
```

The transfer-learning/model-training step itself was performed separately within the laboratory; however, the resulting training and evaluation workflow involved annotation, model-output evaluation, failure-mode identification, and iterative assessment.

### 5. DeLTA-Based Segmentation
The project incorporated the DeLTA framework to support deep-learning-assisted bacterial cell segmentation and tracking.

Within the workflow, segmentation identified individual bacterial cells within microscopy images.

```text
Prepared microscopy data
          │
          ▼
     DeLTA workflow
          │
          ▼
   Cell segmentation
          │
          ▼
   Segmented cell regions
```

Segmentation outputs were inspected using representative experimental data and manually annotated examples. These evaluations also contributed to the iterative assessment of model and workflow performance.

Particular attention was given to practical failure modes including:

- missed cells;
- incorrectly segmented regions;
- merged cells;
- fragmented cells;
- boundaries that did not adequately represent individual cells.

Segmentation quality was considered in relation to the subsequent tracking stage and the reliability of downstream measurements.

Further information on the DeLTA workflow is provided in `deep-learning/DeLTA/README.md`.

### 6. Cell Tracking
Following segmentation, individual bacterial cells were associated across successive microscopy frames.

Tracking therefore provided the temporal component of the image-analysis workflow.

```text
Frame t                  Frame t+1
   │                         │
   ▼                         ▼
Segmented cells         Segmented cells
   │                         │
   └──────────┬──────────────┘
              ▼
        Cell association
              │
              ▼
       Cell trajectories
              │
              ▼
     Time-resolved data
```

Tracking outputs were inspected for errors and inconsistencies, particularly where segmentation errors could propagate into incorrect cell trajectories.

Reliable tracking was necessary because the experimental design depended on longitudinal information from individual cells rather than independent measurements from individual image frames.

### 7. Validation and Quality Control
Validation and quality control were used to assess whether segmentation and tracking outputs were sufficiently reliable for downstream quantitative analysis.

The process included assessment of:

- segmentation quality;
- tracking consistency;
- problematic cell trajectories;
- correspondence with manually annotated examples;
- potential effects of image-analysis errors on downstream measurements.

The validation process was iterative:

```text
Segmentation / tracking outputs
             │
             ▼
        Output inspection
             │
             ▼
       Compare with reference
             │
             ▼
     Identify failure modes
             │
             ▼
       Assess reliability
             │
             ▼
      Refine workflow where
             │
             ▼
        Re-evaluate
```

Validation was therefore integrated into workflow development rather than being treated solely as a final assessment step.

### 8. Post-Processing
Segmentation and tracking outputs required further processing before they could be used for quantitative analysis.

Post-processing included:

- checking detected cells;
- identifying problematic trajectories;
- filtering or flagging unreliable outputs;
- organising cell-level measurements;
- correcting or flagging problematic outputs where feasible;
- preparing processed data for downstream analysis.

This stage connected image-analysis outputs with analysis-ready cell-level data.

### 9. Quantitative Analysis in R
Processed cell-level data were subsequently analysed using R.

The purpose of this stage was to transform image-derived measurements into quantitative summaries suitable for statistical analysis and biological interpretation.

```text
Processed cell-level data
           │
           ▼
       R-based analysis
           │
           ▼
     Quantitative results
           │
           ▼
 Biological interpretation
```

The specific downstream analyses will be documented separately in the `analysis/` section as those details are confirmed and made available.

### 10. Iterative Development Cycle
The workflow was developed iteratively rather than as a single linear implementation.

Representative experimental datasets were processed and inspected to identify limitations in segmentation, tracking, and downstream outputs.

The general development cycle was:

```text
              Initial workflow
                    │
                    ▼
          Process representative data
                    │
                    ▼
        Inspect segmentation / tracking
                    │
                    ▼
           Identify failure modes
                    │
                    ▼
          Modify workflow / processing
                    │
                    ▼
              Re-run analysis
                    │
                    ▼
             Evaluate outputs
                    │
                    └───────────────┐
                                    │
                                    ▼
                              Repeat cycle
```

This iterative approach was important because performance on real experimental microscopy data could differ from behaviour observed on simpler or idealised examples.

Workflow refinement was therefore guided by observed performance on experimental data and by the requirements of downstream quantitative analysis.

## Workflow Summary
The computational architecture can be summarised as:

```text
             COMPUTATIONAL INFRASTRUCTURE
                         │
                         ▼
                Computational environment
                         │
                         ▼
                    DeLTA v2
                         │
                         ▼
                Experimental image data
                         │
                         ▼
              Data preparation / preprocessing
                         │
                         ▼
                  Manual annotation
                         │
                         ▼
             Deep-learning-assisted analysis
                         │
                    ┌────┴────┐
                    ▼         ▼
               Segmentation  Tracking
                    │         │
                    └────┬────┘
                         ▼
                Validation / QC
                         │
                         ▼
                 Post-processing
                         │
                         ▼
                  Cell-level data
                         │
                         ▼
                    R analysis
                         │
                         ▼
              Biological interpretation
```

The workflow illustrates the integration of infrastructure, scientific software, experimental imaging, machine-learning-assisted image analysis, validation, and quantitative analysis into a single computational pipeline.
