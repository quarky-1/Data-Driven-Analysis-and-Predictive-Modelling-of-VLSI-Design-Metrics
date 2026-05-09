# Data-Driven Analysis and Predictive Modelling of VLSI Design Metrics

**Course:** Data Science & Data Analytics — PBL Project
**Institution:** Jaypee Institute of Information Technology, Noida
**Technology:** OpenLane | Sky130 PDK | Python | Scikit-learn

---

## Overview

This project applies data analytics and machine learning techniques to real VLSI design metrics extracted from an OpenLane RTL-to-GDSII flow. The design under analysis is an 8-bit ALU implemented on the Sky130 open-source PDK.

Rather than using a synthetic or publicly available dataset, all metrics were sourced directly from the OpenLane-generated `metrics.csv` file of a completed physical design run — including synthesis statistics, routing utilization, timing closure data, power consumption, and signoff verification results.

The project demonstrates how data science tools can be integrated into EDA workflows to extract meaningful insights from design reports and build predictive models for VLSI design characteristics.

---

## Project Pipeline

```
VLSI Design (OpenLane RTL-to-GDSII)
        ↓
Extraction of Metrics (metrics.csv)
        ↓
Data Collection → Data Preprocessing & Wrangling
        ↓
Structured Analytical Dataset (vlsi_long_format.csv)
        ↓
        ├── Exploratory Data Analysis (EDA)
        │       ├── Metrics Overview
        │       ├── Power Breakdown Analysis
        │       ├── Cell Distribution Analysis
        │       ├── Routing Layer Utilization
        │       ├── Physical Cell Breakdown
        │       ├── Timing Analysis
        │       └── Design Quality Scorecard
        │
        └── Predictive Modelling (Linear Regression)
                ├── Cell Count vs Power
                └── Cell Count vs Core Area
        ↓
Final Insights & Results
```

---

## Repository Structure

```
Data-Driven-Analysis-and-Predictive-Modelling-of-VLSI-Design-Metrics/
├── data/
│   ├── vlsi_metrics.csv          # Original wide-format OpenLane output
│   └── vlsi_long_format.csv      # Transformed long-format analytical dataset
├── notebook/
│   └── Data_Analytics_PBL_VLSI.ipynb   # Complete analysis notebook
├── plots/
│   ├── 01_metrics_overview.png
│   ├── 02_power_breakdown.png
│   ├── 03_cell_distribution.png
│   ├── 04_routing_layers.png
│   ├── 05_physical_cells.png
│   ├── 06_timing_summary.png
│   ├── 07_signoff_scorecard.png
│   ├── 08_power_prediction_model.png
│   └── 09_area_prediction_model.png
└── README.md
```

---

## Design Under Analysis

| Parameter | Value |
|-----------|-------|
| Design | 8-bit ALU (alu_8bit) |
| Technology | Sky130 HD Standard Cell Library |
| Flow | OpenLane RTL-to-GDSII |
| Flow Status | Completed Successfully |
| Synthesis Cells | 115 standard cells |
| Total Cells (with Physical) | 345 cells |
| Core Area | 1941.86 µm² |

---

## Tools and Technologies

| Tool | Purpose |
|------|---------|
| OpenLane | RTL-to-GDSII physical design flow |
| Sky130 PDK | Open-source process design kit |
| Python | Data analysis and modelling |
| Pandas | Data handling and transformation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Scikit-learn | Linear regression models |
| Google Colab | Development environment |

---

## Key Results

### Design Signoff

| Check | Result |
|-------|--------|
| DRC Violations | 0 |
| LVS Errors | 0 |
| Antenna Violations | 0 |
| Timing Violations (WNS) | 0 |
| Timing Violations (TNS) | 0 |

### Timing

| Metric | Value |
|--------|-------|
| Critical Path | 2.34 ns |
| Clock Period | 10 ns |
| Setup Slack | +3.41 ns |
| Hold Slack | +4.34 ns |

### Power (Typical Corner)

| Component | Value | Percentage |
|-----------|-------|------------|
| Internal Power | 25.5 µW | 41.9% |
| Switching Power | 35.3 µW | 58.1% |
| Leakage Power | 0.000747 µW | ~0% |
| **Total Power** | **60.8 µW** | |

### Predictive Models

| Model | R² Score | Predicted | Actual |
|-------|----------|-----------|--------|
| Cell Count vs Power | ~0.999 | 56.1 µW | 60.8 µW |
| Cell Count vs Core Area | ~0.988 | 1262 µm² | 1941.86 µm² |

The area model underestimation demonstrates a key real-world insight: simple cell-count-based models cannot capture physical design overhead from decap cells, fill cells, welltap structures, and routing spacing rules.

---

## Key Findings

- Switching power dominated total consumption at 58.1%, consistent with combinational CMOS behavior
- Routing was concentrated on met1 (21.88%) and met2 (27.89%) with no congestion on any layer
- Physical support cells (decap, fill, welltap) accounted for 58.5% of total cells, significantly impacting layout area
- OR gates formed the largest logic group (30 cells), reflecting the arithmetic and logical nature of an ALU
- The design achieved full timing closure with +3.41 ns setup slack on a 10 ns clock period

---

## Dataset Note

Two dataset formats are maintained:

**Wide Format** (`vlsi_metrics.csv`) — one row per design run, preserving the original OpenLane output structure. Required for ML modeling and maintains real engineering meaning.

**Long Format** (`vlsi_long_format.csv`) — transformed structure with Metric, Value, and Category columns. Used for EDA, visualization, and simplified analysis.

---

## Author

**Sarthak Tripathi**
B.Tech Electronics Engineering (VLSI Design and Technology)
Jaypee Institute of Information Technology, Noida
Enrollment No.: 2401180039

[LinkedIn](https://www.linkedin.com/in/sarthak-tripathi-0b925b1b7/) | [GitHub](https://github.com/quarky-1)

---

## Acknowledgements

- OpenLane Team and OpenROAD Project
- SkyWater PDK Initiative
- Scikit-learn, Pandas, Matplotlib, Seaborn open-source communities
