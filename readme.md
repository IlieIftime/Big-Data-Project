# README - Final Big Data Project: Urban Mobility in Lisbon

## Authors
- Ilie Iftime, Student ID: 112779
- Inês Cruz, Student ID: 123557
- Sofia Quintino, Student ID: 123554

## Overview
This project implements an end-to-end urban mobility data analysis system using Big Data technologies, specifically MongoDB and PySpark. The primary focus is the analysis of shared bicycle usage in the GIRA system and traffic disruptions in Lisbon.

The project covers ingestion of semi-structured data, cleaning and transformation, exploratory analysis, clustering, predictive modeling, and an inference pipeline for recommending zones with higher bicycle availability.

## Objectives
- Collect, integrate, and prepare urban mobility datasets.
- Identify temporal and spatial patterns in bicycle availability.
- Analyze the relationship between traffic disruptions and GIRA bicycle availability.
- Develop predictive models using PySpark ML.
- Create clear visualizations with Plotly.
- Simulate near-real-time queries and recommend zones with higher bicycle supply.

## Technology Stack
- Apache Spark / PySpark 3.4.1
- MongoDB / MongoDB Atlas
- MongoDB Spark Connector 10.2.1
- Plotly 5.15.0
- Jupyter Notebook
- Docker / Docker Compose

## Repository Structure
```text
projeto-big-data/
├── data/
├── scripts/
│   ├── .ipynb_checkpoints/
│   ├── outputs/
│   ├── init-mongo.js
│   └── ProjetoFinal_BD_112779.123557.123554.ipynb
├── docker-compose.yml
├── Dockerfile.jupyter
├── Dockerfile.mongodb
├── readme.md
└── Relatorio_BD_112779.123557.123554.pdf
```

## Prerequisites
- Docker and Docker Compose
- Access to a MongoDB instance (Atlas or local)
- Jupyter Notebook, if not using Docker
- Python 3.8+ with PySpark and Plotly

## How to Run
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd projeto-big-data
   ```

2. Start the Docker containers:
   ```bash
   docker-compose up --build
   ```

3. Access Jupyter Notebook in the browser through the port defined in `docker-compose.yml`.

4. Open the notebook:
   ```text
   scripts/ProjetoFinal_BD_112779.123557.123554.ipynb
   ```

5. Configure the MongoDB connection. The notebook uses a MongoDB Atlas URI. Replace it with your own URI or adjust it for a local MongoDB instance:
   ```python
   uri = "mongodb+srv://<user>:<password>@<cluster>.mongodb.net/test?retryWrites=true&w=majority"
   ```

6. Run the notebook cells in order.

## Project Modules
1. **Data Reading from MongoDB** - Loading the `condicionamentos` and `mobilidade_lisboa` collections.
2. **Data Cleaning and Transformation** - Normalization, timestamp conversion, and null removal.
3. **Daily Aggregations and Dataset Integration** - Daily averages of bicycle availability and traffic disruption counts.
4. **Exploratory Data Analysis (EDA)** - Line charts, bar charts, histograms, and correlation heatmap.
5. **Bonus: Congestion Map by Hour** - Geospatial visualization with Plotly ScatterMapbox.
7. **Predictive Models with PySpark ML** - Random Forest Regressor and Linear Regression.
   - 7.1 Congestion Probability Prediction (Classification)
   - Clustering with PCA (3D)
   - Incident Map Colored by Cluster
8. **Inference and Zone Recommendation Pipeline** - Near-real-time query simulation.
   - Advanced Feature Engineering with Window Functions.

## Key Results
- Weak correlation between GIRA bicycle availability and traffic disruptions.
- Identification of traffic congestion hotspots in Lisbon.
- Persistent imbalances in bicycle distribution across stations.
- Final Random Forest model with sliding-window features:
  - **R2 = 0.99**
  - **RMSE = 0.48**
- Zone recommendation pipeline to identify areas with higher bicycle availability.

## Limitations
- Dependence on the quality of source data.
- No integration with external data such as weather, holidays, or public events.
- Correlation analysis does not establish causality.

## Future Work
- Expose the model as an API.
- Integrate external data sources.
- Develop route optimization algorithms for bicycle redistribution teams.

## Report
The full project report is available at:
```text
Relatorio_BD_112779.123557.123554.pdf
```

## License
Project developed for academic purposes.
