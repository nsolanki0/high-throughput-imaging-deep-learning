# Quantitative Analysis
## Overview
This section documents the final stage of the computational workflow, in which processed segmentation and tracking outputs were transformed into a final cell-level dataset suitable for downstream quantitative analysis.

Following automated image analysis, the resulting data required further inspection, quality control, and, where necessary, manual or semi-automated correction. These steps were performed using R and were important for identifying problematic outputs and preparing the dataset for subsequent biological analysis.

## From Image Analysis to Final Dataset

The final processing stage can be summarised as:

```text
Segmentation / tracking outputs
            │
            ▼
       Post-processing
            │
            ▼
 Manual / semi-automated correction
            │
            ▼
      Data inspection
            │
            ▼
     Visual quality control
            │
            ▼
       Final cell-level
          dataset
            │
            ▼
    Downstream analysis
```

The final dataset contained processed cell-level measurements derived from the microscopy workflow and provided the basis for subsequent quantitative analysis.

## R-Based Data Processing and Inspection
R was used during the final stages of data processing and quality control.

My involvement included:

- inspecting processed cell-level data;
- identifying problematic or inconsistent outputs;
- performing manual and semi-automated corrections where required;
- using visualisation to assess data quality and identify potential issues;
- preparing the resulting data for downstream analysis.

Visual inspection was an important part of this process because the reliability of downstream measurements depended on the quality of the underlying segmentation, tracking, and cell-level data.

## Downstream Quantitative Analysis
The final cell-level dataset could subsequently be used for quantitative and statistical analysis of the biological experiments.

I performed some downstream analyses in R, but this was not the primary focus of my contribution to the project. The specific analyses and statistical procedures are therefore not documented here where the original analysis details are no longer available.

## Code and Data Availability
The original experimental datasets and laboratory-specific analysis code are not included in this repository.

This section documents the role of R in the final data-processing, quality-control, and analysis stage of the workflow rather than reproducing the original laboratory analysis.
