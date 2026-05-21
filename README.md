# AI-Powered Carbon Credit Verification System

## Summary

An AI system that automatically verifies the validity and additionality of carbon offset projects using satellite imagery, IoT sensor data, and machine learning. The goal is to reduce fraud in the voluntary carbon market and increase trust in carbon credits.

## Background

The voluntary carbon market is growing rapidly but suffers from a lack of transparency and verification. Many carbon offset projects have been found to overstate their impact or fail to demonstrate true additionality (the principle that emissions reductions would not have occurred without the project).

This is a real and pressing problem because:
- Billions of euros in carbon credits are traded annually
- Manual verification is expensive, slow, and inconsistent
- Companies and investors need reliable credits to meet net-zero commitments
- Regulatory pressure (EU CBAM, CSRD) is increasing scrutiny of Scope 3 emissions

## How is it used?

The system is used by:
1. **Carbon registries** to automate initial project screening
2. **Corporate buyers** to verify the quality of credits before purchasing
3. **Auditors** to flag high-risk projects for deeper review

The workflow:
1. User submits a carbon project ID or coordinates
2. System fetches satellite time-series (Sentinel-2/Landsat) for the project area
3. ML model estimates biomass/carbon stock changes over time
4. Naive Bayes classifier flags anomalies compared to similar reference areas
5. System outputs a verification score with confidence interval

## Data sources

- **Sentinel-2 satellite imagery** (ESA Copernicus, free)
- **Global Forest Watch** deforestation alerts
- **UNFCCC project registry** baseline data
- **IoT sensors** from project operators (soil carbon, tree diameter)
- Historical **carbon credit prices** and **project performance** records from Verra/Gold Standard

## AI techniques

- **Convolutional Neural Networks (CNN)** for land-use classification from satellite images
- **Linear regression** to model carbon stock trends over time
- **Naive Bayes classifier** to detect anomalies in reported vs. observed carbon sequestration
- **k-Nearest Neighbors** to compare project performance against similar reference projects
- **Simulated annealing** for optimal placement of ground-truth sensor networks

## Challenges

- Satellite imagery has limited resolution (10m for Sentinel-2), missing small-scale changes
- Ground truth data from project operators may be biased
- Temporal coverage gaps in cloudy regions (e.g., tropical forests)
- Class imbalance: fraudulent projects are rare, making training data scarce
- Different project types (forestry, soil, blue carbon) require different models

## What next?

Short-term:
- Train initial CNN on publicly available labeled deforestation datasets (Hansen Global Forest Change)
- Build MVP for forestry projects (REDD+) as they are the largest market segment
- Partner with one carbon registry (e.g., Plan Vivo) for pilot testing

Long-term:
- Expand to other project types (soil carbon, blue carbon, cookstoves)
- Integrate with blockchain-based carbon registries for tamper-proof records
- API for real-time verification embedded in trading platforms

## Acknowledgments

Built as part of the [Building AI](https://buildingai.elementsofai.com/) course by University of Helsinki and Reaktor.

Inspired by work on Scope 3 emissions analysis under the Rainbow carbon credit methodology framework.
