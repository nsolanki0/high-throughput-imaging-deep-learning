# High-Throughput Imaging and Deep Learning Workflow

### Overview
This repository documents computational work undertaken during a nearly three-year position as Student Research Assistant at Freie Universität Berlin, supporting the quantitative analysis of high-throughput microscopy data, including fluorescence microscopy data, generated from _Escherichia coli_ growth and ageing experiments.

The project combined experimental microscopy with image processing, manual annotation, deep-learning-assisted segmentation and tracking, computational infrastructure setup, iterative workflow development, validation, post-processing, and downstream quantitative analysis in R.

The central computational challenge was to reliably identify and follow individual bacterial cells across longitudinal microscopy experiments while preserving sufficient accuracy for subsequent quantitative biological analysis.

The workflow evolved iteratively from data preparation and manual annotation through segmentation and tracking, validation, post-processing, and downstream analysis.

> **Note:** The original research code, experimental datasets, and laboratory-specific computational environment are not included in this repository. This repository focuses on documenting the computational workflow, methodology, infrastructure, and my contribution to the project rather than reproducing the original research code.

### Scientific Context
The underlying biological project investigated population dynamics through cellular growth, ageing, and long-term molecular changes in _E. coli_ under different experimental conditions.

A mother-machine microfluidic platform was used together with high-throughput microscopy to generate longitudinal imaging datasets of bacterial cells.

The experimental design enabled individual cells to be observed over time, but also generated large volumes of time-resolved image data requiring computational processing.

The imaging data therefore needed to be transformed from microscopy images into reliable cell-level measurements through a sequence of computational steps:
- identification and segmentation of individual cells;
- tracking of cells across successive frames;
- quality control of image-analysis outputs;
- extraction and organisation of cell-level measurements;
- downstream quantitative and statistical analysis.
The scale and longitudinal nature of the data made manual analysis impractical and motivated the development and integration of automated or semi-automated image-analysis approaches.

### Computational Problem
The primary computational problem was the reliable segmentation and tracking of individual bacterial cells in high-throughput time-lapse microscopy data.

The workflow had to operate on real experimental datasets rather than relying solely on idealised or manually curated image examples. Practical challenges included:
- large imaging datasets;
- variation in image quality;
- closely positioned or crowded cells;
- changes in cell morphology over time;
- segmentation errors;
- tracking errors;
- propagation of segmentation errors into cell trajectories;
- conversion of image-derived outputs into biologically meaningful measurements.
Rather than treating segmentation as an isolated machine-learning problem, the project was approached as an end-to-end computational workflow.

### Overall workflow

```text
Experimental microscopy
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
Deep-learning-assisted
      segmentation
          │
          ▼
        Tracking
          │
          ▼
 Quality control /
      validation
          │
          ▼
    Post-processing
          │
          ▼
   Quantitative analysis
          │
          ▼
  Biological interpretation
```
The deep-learning component was therefore integrated into a broader experimental and computational workflow rather than considered independently from the microscopy data and downstream analysis.

A more detailed technical representation of the workflow is provided in `docs/workflow-overview.md`.

### Experimental Platform
The imaging workflow was based on:
- mother-machine microfluidics;
- high-throughput microscopy;
- fluorescence microscopy where applicable;
- time-lapse imaging;
- longitudinal observation of bacterial cells;
- experiments performed under multiple conditions.
The mother-machine system provided a framework for following bacterial cells over time, creating a need for reliable cell segmentation and tracking across successive image frames.

The computational workflow was therefore designed around the characteristics and requirements of the experimental datasets rather than around a generic image-analysis example.

## My Computational Contribution
My contribution spanned the computational workflow from establishing the computational environment through image processing, deep-learning-assisted analysis, validation, post-processing, and downstream quantitative analysis.

### 1. Computational Infrastructure
The project required additional computational resources to support the updated image-analysis and deep-learning workflow.

I contributed to upgrading and configuring the computational infrastructure and software environment, including:
- system memory resources;
- GPU resources;
- software configuration;
- required dependencies;
- the computational environment required to run the updated image-analysis workflow.
Further details are documented in `computational-infrastructure/README.md`.

### 2. DeLTA v2 Setup and Integration
The laboratory was initially working with an earlier version of the DeLTA framework. I contributed to establishing the computational setup required to transition to DeLTA v2 and run it with the project's microscopy datasets.

This involved practical deployment and integration tasks including:
- installing and configuring the updated software;
- addressing software and dependency issues encountered during deployment;
- adapting input and output requirements;
- integrating experimental imaging datasets with the workflow;
- testing the computational pipeline;
- troubleshooting deployment problems;
- verifying that the workflow could operate on the project data.
The work therefore extended beyond simply executing an existing software package and involved establishing a usable computational environment around the software.

### 3. Data Preparation
The microscopy datasets required preparation before they could be processed using automated image-analysis methods.

The workflow included steps for:
- organising imaging data;
- preparing image sequences;
- selecting appropriate datasets;
- formatting inputs;
- checking image quality;
- preparing data for annotation and model-based processing.
Data preparation was an important component of the workflow because downstream segmentation and tracking depended on the consistency and suitability of the image inputs.

### 4. Manual Annotation
Representative microscopy images were manually annotated to provide labelled examples for segmentation development, evaluation, and the broader model-development workflow.

Annotation was treated as an important component of the computational workflow rather than simply as a preliminary step.

The annotated data were used to:
- assess segmentation behaviour;
- identify segmentation errors;
- evaluate image-analysis outputs;
- identify areas requiring further refinement.
Manual annotation therefore provided an essential reference for evaluating automated image-analysis outputs.

### 5. Cell Segmentation
Cell segmentation was used to identify individual bacterial cells within microscopy images.

Segmentation outputs were evaluated against manually annotated examples, with attention to practical failure modes including:
- missed cells;
- incorrectly segmented regions;
- merged cells;
- fragmented cells;
- boundaries that did not adequately represent individual cells.
Segmentation quality was considered in the context of the subsequent tracking and quantitative-analysis requirements.

Accurate segmentation was particularly important because errors at this stage could propagate into downstream cell tracking and ultimately affect the reliability of quantitative measurements.

### 6. Cell Tracking
Following segmentation, individual cells needed to be associated across successive frames.

Tracking therefore formed a second critical component of the image-analysis workflow.

Tracking outputs were inspected for errors and inconsistencies, particularly where segmentation errors could propagate into incorrect cell trajectories.

The longitudinal nature of the experiments meant that reliable tracking was necessary for converting individual image frames into meaningful time-resolved cellular measurements.

### 7. Iterative Workflow Development
The computational workflow was refined iteratively using representative experimental datasets.

The general development cycle was:

```text
Initial workflow
      │
      ▼
Run on representative data
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
      └──────────────► Repeat
```
This iterative approach was important because performance on real experimental microscopy data could differ substantially from behaviour observed on simpler or idealised examples.

The workflow was therefore developed around observed performance on the project's experimental datasets, with particular attention to segmentation and tracking errors that could affect downstream biological analysis.

## Deep Learning
The project incorporated the DeLTA framework for deep-learning-assisted bacterial cell segmentation and tracking, forming the computational link between microscopy images and cell-level measurements.

My contribution included the practical computational setup, integration, testing, evaluation, and workflow development surrounding the DeLTA-based analysis. I was also involved in the broader model-development workflow through preparation and annotation of training and evaluation data, assessment of model outputs, identification of failure modes, and iterative evaluation of model and workflow performance.

I did not independently perform the transfer-learning/model-training step itself. This reflects the specific division of responsibilities within the project rather than indicating that I was uninvolved in model development or evaluation.

Further documentation is available in `deep-learning/DeLTA/`.

## Validation
Validation was performed using representative microscopy data and manually annotated examples.

The purpose of validation was to determine whether the computational workflow generated sufficiently reliable segmentation and tracking outputs for downstream quantitative biological analysis.

Validation considered both individual image-analysis outputs and the behaviour of cell trajectories over time.

Particular attention was given to practical failure modes rather than relying exclusively on a single numerical performance metric.

This allowed the image-analysis workflow to be assessed in the context in which it was ultimately intended to be used: extracting biologically meaningful measurements from longitudinal experimental microscopy data.

## Post-Processing
Raw segmentation and tracking outputs required additional processing before they could be used for downstream analysis.

Post-processing included activities such as:
- checking detected cells;
- identifying problematic trajectories;
- filtering or flagging unreliable outputs;
- organising cell-level measurements;
- correcting or flagging problematic outputs where feasible;
- preparing processed data for statistical analysis.
This stage connected the image-analysis workflow to the subsequent biological analysis.

## Quantitative Analysis
Processed imaging data were subsequently analysed using R.

The downstream analysis transformed image-derived measurements into quantitative summaries for biological interpretation and publication-oriented analysis.

## Repository Structure
```text
high-throughput-imaging-deep-learning/
│
├── README.md
│
├── computational-infrastructure/
│   └── README.md
│
├── deep-learning/
│   └── DeLTA/
│       └── README.md
│
├── analysis/
│   └── README.md
│
└── docs/
    └── workflow-overview.md
```
Because the original laboratory code and datasets are not available for public release, the repository is structured primarily around project documentation, workflow description, technical methodology, and selected figures/diagrams rather than source-code reproduction.

## Technical Skills Demonstrated
### Computational Infrastructure
- Hardware resource assessment
- System memory and GPU upgrades
- Computational environment configuration
- Scientific software installation
- Dependency management
- Troubleshooting research software
- GPU-enabled computational workflows

### Image Analysis
- High-throughput microscopy data processing
- Fluorescence microscopy
- Time-lapse image analysis
- Image annotation
- Single-cell image analysis
- Cell segmentation
- Cell tracking
- Quality control
- Post-processing

### Machine Learning
- Practical deployment and integration of deep-learning-based image-analysis workflows
- DeLTA framework integration
- Segmentation/tracking evaluation
- Segmentation and tracking output validation
- Iterative workflow refinement
- Identification of image-analysis failure modes
- Integration of deep-learning workflows with experimental datasets
- Contribution to model development through training/evaluation data preparation, model-output evaluation, and iterative performance assessment

### Data Analysis
- Cell-level quantitative data processing
- R-based statistical analysis
- Data visualisation
- Publication-oriented quantitative analysis
- Conversion of image-derived outputs into quantitative biological measurements

## Key Takeaway
This project demonstrates an end-to-end computational biology workflow for transforming experimental microscopy data into quantitative biological measurements.

A particularly important aspect of the work was the integration of computational infrastructure, scientific software, image analysis, deep-learning-assisted segmentation and tracking, validation, post-processing, and R-based quantitative analysis.

The project demonstrates experience working across the boundary between experimental biology and computational analysis, including the practical challenges of deploying research software, processing real experimental imaging data, evaluating machine-learning-assisted outputs, and preparing quantitative measurements for biological analysis.

## Code and Data Availability
The original source code, experimental datasets, laboratory-specific configurations, and other research materials are not included.

This repository is intended as a technical project record and portfolio resource documenting the computational workflow, methodology, infrastructure, and my contribution.

Additional diagrams, workflow documentation, methodological notes, and non-sensitive illustrative material may be added where appropriate to further document the computational approaches used in the project.
