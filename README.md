# ITAI-2376-workforce-scheduling-agent
This repository is for storing the documentation for my ITAI2376 Deep Learning Project.

# Workforce Scheduling Optimization — Multi-Agent System

## Project Overview

This project is an AI-based workforce scheduling optimization system for a synthetic manufacturing environment. It simulates a 24/7 production facility where employees must be assigned to shifts based on forecasted demand, skills, availability, maximum weekly hours, and operational constraints.

The system uses a two-agent architecture coordinated with CrewAI:

1. **Demand Forecasting Agent**: Predicts staffing demand using an LSTM model.
2. **Scheduling & Explanation Agent**: Creates a schedule using OR-Tools, validates the schedule, and explains the results using Gemini.

## What the Project Does

The system performs the following workflow:

1. Generates synthetic employee and demand datasets.
2. Trains an LSTM model to forecast staffing needs.
3. Uses OR-Tools to assign employees to shifts.
4. Validates schedule coverage and constraint compliance.
5. Generates a manager-friendly explanation using Gemini.
6. Coordinates the workflow through CrewAI.

## Tools and Models Used

- **CrewAI**: Multi-agent orchestration
- **TensorFlow / Keras**: LSTM demand forecasting model
- **Google OR-Tools**: Constraint-based scheduling optimization
- **Google Gemini API**: Schedule explanation
- **pandas / NumPy**: Data processing
- **scikit-learn**: Scaling and evaluation
- **python-dotenv**: API key management

## Project Structure

```text
workforce_scheduling_agent/
├── data/
│   ├── employees.csv
│   └── demand_history.csv
├── outputs/
│   ├── forecast.json
│   ├── forecast.csv
│   ├── schedule.json
│   ├── schedule.csv
│   ├── schedule_summary.json
│   ├── schedule_validation_summary.json
│   ├── schedule_explanation.txt
│   └── schedule_explanation.json
├── src/
│   ├── generate_data.py
│   ├── validate_data.py
│   ├── forecast_model.py
│   ├── scheduler.py
│   ├── validate_schedule.py
│   ├── explain_schedule.py
│   └── agents.py
├── .env
├── .gitignore
├── requirements.txt
└── README.md
