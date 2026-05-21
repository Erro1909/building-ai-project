# AI-Powered Carbon Credit Verification System

Building AI course project

## Summary

An AI system that automatically verifies the validity and additionality of carbon offset projects using satellite imagery, IoT sensor data, and machine learning. Reduces fraud in the voluntary carbon market and increases trust in carbon credits. Building AI course project by Enrico Natali.

## Background

The voluntary carbon market is growing rapidly but suffers from a lack of transparency and verification. Many carbon offset projects overstate their impact or fail to demonstrate true additionality.

Problems this solves:
* Billions of euros in carbon credits are traded annually with insufficient oversight
* Manual verification is expensive, slow, and inconsistent
* Companies need reliable credits to meet net-zero commitments
* Regulatory pressure (EU CBAM, CSRD) is increasing scrutiny of Scope 3 emissions

## How is it used?

The system is used by:
1. **Carbon registries** to automate initial project screening
2. **Corporate buyers** to verify credit quality before purchasing
3. **Auditors** to flag high-risk projects for deeper review

Workflow:
1. User submits a carbon project ID or coordinates
2. System fetches satellite time-series (Sentinel-2/Landsat) for the project area
3. ML model estimates biomass/carbon stock changes over time
4. Naive Bayes classifier flags anomalies vs. similar reference areas
5. System outputs a verification score with confidence interval

## Data sources and AI methods

| Source | Description |
| ----------- | ----------- |
| Sentinel-2 (ESA Copernicus) | Free satellite imagery, 10m resolution |
| Global Forest Watch | Deforestation alerts |
| UNFCCC project registry | Baseline data |
| Verra / Gold Standard | Historical credit prices and performance |

AI techniques used:
* **CNN** for land-use classification from satellite images
* **Linear regression** to model carbon stock trends over time
* **Naive Bayes** to detect anomalies in reported vs. observed sequestration
* **k-Nearest Neighbors** to benchmark against similar reference projects
* **Simulated annealing** for optimal sensor network placement

## Challenges

* Satellite imagery limited to 10m resolution — misses small-scale changes
* Ground truth data from operators may be biased
* Temporal gaps in cloudy regions (e.g., tropical forests)
* Class imbalance: fraudulent projects are rare, making training data scarce

## What next?

* Train initial CNN on Hansen Global Forest Change labeled dataset
* Build MVP for REDD+ forestry projects as the largest market segment
* Partner with one registry (e.g., Plan Vivo) for pilot testing
* Long-term: expand to soil/blue carbon, blockchain integration, real-time API

## Acknowledgments

* Built as part of the [Building AI](https://buildingai.elementsofai.com/) course by University of Helsinki and Reaktor
* Inspired by personal work on Scope 3 emissions analysis under the Rainbow carbon credit methodology
* Satellite data: ESA Copernicus Open Access Hub (free and open)