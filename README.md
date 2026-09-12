# High-Throughput Imaging and Deep Learning Workflow

### Overview
This repository documents a computational workflow developed to support the quantitative analysis of high-throughput fluorescence microscopy data generated from Escherichia coli ageing experiments.

The project combined experimental microscopy with image processing, manual annotation, deep-learning-assisted segmentation and tracking, computational infrastructure setup, iterative workflow development, and downstream quantitative analysis in R.

The central computational challenge was to reliably identify and follow individual bacterial cells across longitudinal microscopy experiments while preserving sufficient accuracy for subsequent quantitative biological analysis.

The workflow evolved iteratively from data preparation and manual annotation through segmentation and tracking, validation, post-processing, and downstream analysis.

> **Note:** The original research code, experimental datasets, and laboratory-specific computational environment are not included in this repository because the work was conducted within a university research laboratory. This repository therefore focuses on documenting the computational workflow, methodology, infrastructure, and my contribution to the project rather than reproducing the original research code.

### Scientific Context
The underlying biological project investigated cellular ageing and long-term cellular behaviour in E. coli under different experimental conditions.

A mother-machine microfluidic platform was used together with high-throughput fluorescence microscopy to generate longitudinal imaging datasets of bacterial cells.

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

The workflow had to operate on real experimental datasets rather than idealised or manually curated image examples. Practical challenges included:
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
      Segmentation
          │
          ▼
        Tracking
          │
          ▼
Quality control / validation
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
The deep-learning component was integrated into this broader workflow rather than considered independently from the experimental data and downstream analysis.

### Experimental Platform
The imaging workflow was based on:
- mother-machine microfluidics;
- high-throughput fluorescence microscopy;
- time-lapse imaging;
- longitudinal observation of bacterial cells;
- experiments performed under multiple conditions.
The mother-machine system provided a framework for following bacterial cells over time, creating a need for reliable cell segmentation and tracking across successive image frames.

The computational workflow was therefore designed around the characteristics and requirements of the experimental datasets rather than around a generic image-analysis example.

## My Computational Contribution
My contribution covered multiple stages of the computational workflow, from establishing the computational environment through image processing, model-based analysis, validation, post-processing, and downstream quantitative analysis.

## 1. Computational Infrastructure
The project required additional computational resources to support the updated image-analysis and deep-learning workflow.

I contributed to upgrading and configuring the computational environment, including:
- system memory resources;
- GPU resources;
- software configuration;
- required dependencies;
- the computational environment required to run the updated image-analysis workflow.
The infrastructure upgrade established the computational resources required for subsequent deployment and use of the newer DeLTA workflow.

## 2. DeLTA v2 Setup and Integration
The laboratory was initially working with an earlier version of the DeLTA framework.

To support the use of a newer version, I worked on establishing the computational setup required to run DeLTA v2 with the project's microscopy datasets.

This involved practical deployment and integration tasks including:
- installing and configuring the updated software;
- resolving software and dependency issues;
- adapting input and output requirements;
- integrating experimental imaging datasets with the workflow;
- testing the computational pipeline;
- troubleshooting problems encountered during deployment;
- verifying that the workflow could operate on the project data.
The work therefore extended beyond simply executing an existing software package and involved establishing a usable computational environment around the software.

Further details of the computational environment and DeLTA deployment are documented in computational-infrastructure/.

## 3. Data Preparation
The microscopy datasets required preparation before they could be processed using automated image-analysis methods.

The workflow included steps for:
- organising imaging data;
- preparing image sequences;
- selecting appropriate datasets;
- formatting inputs;
- checking image quality;
- preparing data for annotation and model-based processing.
Data preparation was an important component of the workflow because downstream segmentation and tracking depended on the consistency and suitability of the image inputs.

## 4. Manual Annotation
Representative microscopy images were manually annotated to provide labelled examples for segmentation development and evaluation.

Annotation was treated as an important component of the computational workflow rather than simply as a preliminary step.

The annotated data were used to:
- assess segmentation behaviour;
- identify segmentation errors;
- evaluate the performance of the image-analysis workflow;
- identify areas requiring further refinement.
Manual annotation therefore provided an essential reference for evaluating automated image-analysis outputs.

## 5. Cell Segmentation
Cell segmentation was used to identify individual bacterial cells within microscopy images.

Segmentation outputs were evaluated against manually annotated examples, with attention to practical failure modes including:
- missed cells;
- incorrectly segmented regions;
- merged cells;
- fragmented cells;
- boundaries that did not adequately represent individual cells.
Segmentation quality was considered in the context of the subsequent tracking and quantitative-analysis requirements.

Accurate segmentation was particularly important because errors at this stage could propagate into downstream cell tracking and ultimately affect the reliability of quantitative measurements.

## 6. Cell Tracking
Following segmentation, individual cells needed to be associated across successive frames.

Tracking therefore formed a second critical component of the image-analysis workflow.

Tracking outputs were inspected for errors and inconsistencies, particularly where segmentation errors could propagate into incorrect cell trajectories.

The longitudinal nature of the experiments meant that reliable tracking was necessary for converting individual image frames into meaningful time-resolved cellular measurements.

## 7. Iterative Workflow Development
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

# Deep Learning
The project incorporated the DeLTA framework for deep-learning-assisted bacterial cell segmentation and tracking.

DeLTA formed part of the computational pipeline connecting microscopy images with cell-level measurements.

My contribution included the practical computational setup, integration, testing, evaluation, and workflow development surrounding the DeLTA-based analysis.

Importantly, my role did not include independently performing the transfer-learning training of the final model.

This repository therefore distinguishes between:
- establishing and operating the deep-learning workflow;
- preparing and evaluating image data;
- integrating experimental datasets;
- assessing segmentation and tracking performance;
- iteratively refining the workflow;
and the separate activity of transfer-learning/model training.

This distinction is intentional and reflects the actual scope of my contribution.

Further documentation is available in deep-learning/DeLTA/.

# Validation
Validation was performed using representative microscopy data and manually annotated examples.

The purpose of validation was to determine whether the computational workflow generated sufficiently reliable segmentation and tracking outputs for downstream quantitative biological analysis.

Validation considered both individual image-analysis outputs and the behaviour of cell trajectories over time.

Particular attention was given to practical failure modes rather than relying exclusively on a single numerical performance metric.

This allowed the image-analysis workflow to be assessed in the context in which it was ultimately intended to be used: extracting biologically meaningful measurements from longitudinal experimental microscopy data.

# Post-Processing
Raw segmentation and tracking outputs required additional processing before they could be used for downstream analysis.

Post-processing included activities such as:
- checking detected cells;
- identifying problematic trajectories;
- filtering or flagging unreliable outputs;
- organising cell-level measurements;
- preparing processed data for statistical analysis.
This stage connected the image-analysis workflow to the subsequent biological analysis.

# Quantitative Analysis
Processed imaging data were subsequently analysed using R.

The downstream analysis transformed image-derived measurements into quantitative summaries suitable for biological interpretation and publication-oriented analysis.

The complete computational chain can therefore be represented as:

```text
Experimental microscopy
          │
          ▼
       Image data
          │
          ▼
     Preprocessing
          │
          ▼
      Annotation
          │
          ▼
Deep-learning-assisted
     segmentation
          │
          ▼
      Cell tracking
          │
          ▼
    Post-processing
          │
          ▼
   Quality control
          │
          ▼
    R-based analysis
          │
          ▼
Biological interpretation
```
The downstream R analysis was an important final stage of the workflow because the objective was not simply to generate segmentation or tracking outputs, but to convert those outputs into quantitative information that could contribute to biological interpretation.

## Computational Infrastructure
The infrastructure component of the project involved upgrading the computational resources required for the image-analysis workflow.

The overall setup can be viewed as:
```text
Hardware requirements
          │
          ├── System memory upgrade
          │
          └── GPU upgrade
                  │
                  ▼
       Computational environment
                  │
                  ▼
          DeLTA v2 installation
                  │
                  ▼
       Dependency configuration
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
         Operational pipeline
```
This component demonstrates practical experience in establishing computational infrastructure for research software and integrating that environment with a real experimental analysis workflow.

More detailed infrastructure and deployment documentation is available in computational-infrastructure/.

## Repository Structure
```text
high-throughput-imaging-deep-learning/
│
├── README.md
│
├── workflow/
│   ├── data-preparation/
│   ├── preprocessing/
│   ├── annotation/
│   ├── segmentation/
│   ├── tracking/
│   └── post-processing/
│
├── computational-infrastructure/
│   └── README.md
│
├── deep-learning/
│   ├── DeLTA/
│   │   └── README.md
│   ├── model-iterations/
│   └── validation/
│
├── analysis/
│   └── R/
│
├── figures/
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
- Practical deployment of deep-learning-based image-analysis workflows
- DeLTA framework integration
- Segmentation/tracking evaluation
- Model-output validation
- Iterative workflow refinement
- Identification of image-analysis failure modes
- Integration of deep-learning workflows with experimental datasets

### Data Analysis
- Cell-level quantitative data processing
- R-based statistical analysis
- Data visualisation
- Publication-oriented analysis
- Conversion of image-derived outputs into quantitative biological measurements

## Key Takeaway
This project demonstrates an end-to-end computational biology workflow in which experimental microscopy data were transformed into quantitative biological measurements.

A particularly important aspect of the work was the integration of several layers of computational research:

```text
Computational infrastructure
          ↓
Computational environment
          ↓
Scientific software
          ↓
Experimental imaging data
          ↓
Data preparation
          ↓
Annotation
          ↓
Deep-learning-assisted analysis
          ↓
Segmentation & tracking
          ↓
Validation
          ↓
Post-processing
          ↓
R-based quantitative analysis
          ↓
Biological interpretation
```
The project therefore demonstrates experience working across the boundary between experimental biology and computational analysis, including the practical challenges involved in deploying research software, processing real experimental imaging data, evaluating machine-learning-assisted outputs, and preparing quantitative measurements for biological analysis.

The workflow illustrates an ability to work across multiple layers of a computational research problem rather than treating machine learning, image analysis, infrastructure, and statistical analysis as isolated tasks.

## Code and Data Availability
The original source code, experimental datasets, laboratory-specific configurations, and other research materials are not included because the work was conducted within a university research environment.
This repository is intended as a technical project record and portfolio documentation describing the computational workflow, methodologies, infrastructure, and my contribution.

Where appropriate, additional diagrams, workflow documentation, methodological notes, and non-sensitive illustrative material may be added to demonstrate the computational approaches used in the project.