# Water Footprint Calculator for Sustainable Agriculture

A full-stack web application that estimates the water footprint of agricultural practices based on crop type, region, irrigation method, and weather data. The platform enables farmers, researchers, and policymakers to make data-driven decisions for efficient water use and climate-resilient farming.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [ML Model](#ml-model)
- [Tech Stack](#tech-stack)
- [API Endpoints](#api-endpoints)
- [Installation](#installation)
- [Usage](#usage)
- [Datasets and APIs Used](#datasets-and-apis-used)
- [License](#license)

---

## Overview

This platform estimates crop-wise water consumption (blue, green, and grey water footprints) using a machine learning model, climate APIs, soil data, and satellite inputs. The system provides:

- Accurate water footprint estimation for different crops
- Data visualization across crops and regions
- Crop and irrigation method recommendations
- Downloadable water footprint reports
- REST API backend integrated with PostgreSQL
- Modern frontend built using Next.js

---

## Key Features

| Feature Category      | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Crop Input Form       | Accepts crop type, location, irrigation method, and soil parameters         |
| Water Footprint Model | Predicts water usage in liters/kg and m³/ha                                 |
| Visualization         | Interactive charts showing water usage, trends, and crop comparisons        |
| Climate Integration   | Real-time climate data via OpenWeatherMap, NASA POWER, and SoilGrids APIs   |
| Recommendations       | Suggests water-efficient practices and crop alternatives                   |
| Reports               | Generates downloadable PDF and CSV reports for users                        |
| Admin Panel           | For moderating requests, managing users, and system-wide configurations     |

---

## Architecture

Frontend (Next.js) ↓ Backend (Django + Django REST Framework) ↓ PostgreSQL (Data Storage) ↓ Machine Learning Model (Water Footprint Estimator) ↓ External APIs (Climate, Soil, Satellite)
The system is modular, scalable, and suitable for cloud deployment with production-ready APIs.

---

## ML Model

- **Algorithm:** Random Forest Regressor
- **Target:** Water Footprint (liters/kg and m³/ha)
- **Features:** Crop type, location (lat/lon), irrigation method, rainfall, PET, soil texture, NDVI
- **Evaluation:**
  - R² Score: 0.87
  - MAE: ~420 L/kg (depending on crop and conditions)
- **Training Data Sources:** FAO WaterStat, India-WRIS, NASA POWER, CROPWAT

---

## Tech Stack

| Layer        | Technology                       |
|--------------|----------------------------------|
| Frontend     | Next.js (React), Tailwind CSS    |
| Backend      | Django, Django REST Framework    |
| ML           | Python (scikit-learn, pandas)    |
| Database     | PostgreSQL                       |
| Hosting      | Render / Railway / Vercel        |
| APIs         | NASA POWER, OpenWeatherMap, SoilGrids, SentinelHub (optional)

---

## API Endpoints

| Endpoint                      | Method | Description                                          |
|-------------------------------|--------|------------------------------------------------------|
| `/api/water-footprint/`       | POST   | Predicts water usage based on input crop and climate |
| `/api/crops/`                 | GET    | Returns supported crop list                         |
| `/api/regions/`               | GET    | Lists predefined regions or states                  |
| `/api/soil/`                  | GET    | Returns soil data for selected coordinates          |
| `/api/climate/`               | GET    | Returns climate metrics like rainfall, PET          |
| `/api/recommendations/`       | POST   | Suggests better irrigation or crop options          |
| `/api/report/pdf/`            | POST   | Generates downloadable PDF report                   |
| `/api/report/csv/`            | POST   | Generates downloadable CSV report                   |

All endpoints return JSON unless otherwise specified.

---



## Usage
Start the backend and frontend servers

Visit http://localhost:3000 to access the dashboard

Fill in the crop type, location, and irrigation method

Click “Generate” to view water usage stats and graphs

Generate and download reports as needed

## Datasets and APIs Used
Source	Purpose
NASA POWER	Evapotranspiration, solar radiation, climate
OpenWeatherMap	Real-time temperature, rainfall, humidity
SoilGrids	Soil pH, texture, organic content
FAO WaterStat	Crop-wise water use standards
India-WRIS	Regional irrigation and water availability
SentinelHub	Optional NDVI integration
