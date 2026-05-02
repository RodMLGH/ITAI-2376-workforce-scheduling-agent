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

- **CrewAI**: Multi-agent orchestration.
- **TensorFlow / Keras**: LSTM demand forecasting model.
- **Google OR-Tools**: Constraint-based scheduling optimization.
- **Google Gemini API**: Schedule explanation.
- **pandas / NumPy**: Data processing.
- **scikit-learn**: Scaling and evaluation.
- **python-dotenv**: API key management.

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
```

## Installation

From the project root, install the required packages: `python -m pip install -r requirements.txt`
If needed, install manually: `python -m pip install pandas numpy scikit-learn tensorflow ortools google-genai python-dotenv crewai`

## Gemini API Setup

Create a `.env` file in the project root: 

GEMINI_API_KEY=your_api_key_here
GEMINI_MODEL=gemini-2.5-flash-lite
Recommended `.gitignore` entry: .env

## How to Run the Project

Run the full multi-agent workflow:
`python src\agents.py`
This runs the full CrewAI workflow from Demand Forecasting Agent to Scheduling & Explanation Agent.

## Output Files

The project generates the following outputs:
- `outputs/forecast.json` and `outputs/forecast.csv` (staffing demand forecast)
- `outputs/schedule.json` and `outputs/schedule.csv` (optimized workforce schedule)
- `outputs/schedule_summary.json` (high-level schedule metrics)
- `outputs/schedule_validation_summary.json` (coverage and constraint validation)
- `outputs/schedule_explanation.txt` and `outputs/schedule_explanation.json` (manager-friendly explanation)

## Notes About Synthetic Data

All data is synthetic. No real employee records, phone numbers, addresses, salary data, or proprietary company information are used. Synthetic data allows the project to demonstrate the full workflow safely while avoiding privacy concerns.


## Current Limitations

This project is a proof of concept. The first version schedules only a 3-day window, uses synthetic data, and applies a simplified set of constraints. Some positions may remain unfilled if there are not enough available or qualified employees.


## Future Improvements

Future versions could expand the schedule to 7 days, activate more employee fields such as experience and certifications, include more advanced manufacturing variables, improve the LSTM model, add preference-based scheduling, and build a Streamlit interface.


## Main Demo Command

`python src\agents.py`
