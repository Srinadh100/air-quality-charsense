# air-quality-charsense
CharSense – Biochar-based Air Purification with AI-driven Predictions
CharSense is an AI-powered air purification and monitoring system that combines biochar filtration technology with a deep learning model to predict air quality trends. It aims to provide a low-cost, sustainable alternative to HEPA purifiers while being especially relevant for healthcare, schools, rural households, and urban spaces.
Features
Biochar-based Air Filtration – Sustainable, affordable, and efficient for PM2.5 reduction.
Real-time Air Quality Monitoring – Captures pollutant levels and environmental parameters.
Deep Learning Model (WaveNet AQ) – Predicts AQI trends using attributes like PM2.5, RH, AT, etc.
Web Dashboard – Interactive frontend to visualize air quality readings and ML-based predictions.
Scalable Use Cases – Healthcare, schools, homes, workplaces, and rural smoke-affected regions.
Tech Stack
Frontend: React.js / HTML-CSS-JS, Tailwind CSS, TypeScript (Website for monitoring & predictions)
Data: Public air quality datasets (PM2.5, RH, AT, etc.) + simulated readings
Hardware (Prototype Stage): Biochar filter + fan-based purification unit
Repository Structure
CharSense/
│── node_modules/         # Node.js dependencies
│── public/               # Static public assets
│── src/                  # Source code
│   ├── components/       # React components
│   ├── data/            # Data files and utilities
│   ├── hooks/           # Custom React hooks
│   ├── lib/             # Library and utility functions
│   ├── pages/           # Page components
│   ├── App.css          # Main application styles
│   ├── App.tsx          # Main React application component
│   ├── index.css        # Global styles
│   ├── main.tsx         # Application entry point
│   └── vite-env.d.ts    # Vite type definitions
│── .gitignore           # Git ignore rules
│── bun.lockb            # Bun lockfile
│── components.json      # Component configuration
│── eslint.config.js     # ESLint configuration
│── index.html           # HTML template
│── package-lock.json    # npm lockfile
│── package.json         # Project dependencies and scripts
│── postcss.config.js    # PostCSS configuration
│── tailwind.config.ts   # Tailwind CSS configuration
│── tsconfig.app.json    # TypeScript config for app
│── tsconfig.json        # TypeScript configuration
│── tsconfig.node.json   # TypeScript config for Node
│── vite.config.ts       # Vite build configuration
│── README.md            # Project documentation
How It Works
Sensors / dataset readings are fed into the system (PM2.5, temperature, RH, etc.).
The biochar filter prototype physically filters pollutants.
The Deep Learning model (WaveNet AQ) predicts future AQI trends.
The frontend dashboard displays real-time readings & predictions.
Getting Started
1. Install dependencies
pip install -r requirements.txt
2. Run backend (ML Model API)
cd backend
python app.py
3. Run frontend (Dashboard)
cd frontend
npm install
npm start
5. Access Dashboard
Go to: http://localhost:3000
Model Training
Algorithm: Deep Learning (WaveNet-inspired LSTM)
Features: PM2.5, Temperature (AT), Relative Humidity (RH), Wind Speed, AQI trends
Output: Predicted AQI levels & pollution risk category
Future Roadmap
Wearable integration for personalized risk alerts
Deployable IoT-based prototype with biochar filters
Mobile app support for real-time tracking
# CharSense – Biochar-based Air Purification with AI-driven Predictions
## Features
- **Biochar-based Air Filtration** – Sustainable, affordable, and efficient PM2.5 reduction
- **Real-time Air Quality Monitoring** – Captures multiple pollutant levels and environmental parameters
- **Dual Prediction Models** – LSTM Neural Network and SARIMA for comprehensive air quality forecasting
- **Interactive Web Dashboard** – React-based frontend to visualize readings and predictions
- **Multi-parameter Analysis** – Simultaneous prediction of AT, RH, PM2.5, PM10, and CO2 levels
- **30-day Forecasting** – Accurate predictions for air quality trends
## Tech Stack
### Frontend
- **React** with TypeScript
- **Vite** build tool and dev server
- **Tailwind CSS** for styling
- **PostCSS** for CSS processing
### Backend & Data Science
- **Python** for data processing and modeling
- **TensorFlow/Keras** for LSTM implementation
- **statsmodels** for SARIMA time series analysis
- **scikit-learn** for metrics and data preprocessing
- **pandas** & **numpy** for data manipulation
### Visualization
- **matplotlib** for model evaluation plots
- **React Charts** for web dashboard visualizations
## Repository Structure
CharSense/
│
├── frontend/ # React TypeScript frontend application
│ ├── node_modules/ # Node.js dependencies
│ ├── public/ # Static public assets
│ ├── src/ # Source code
│ │ ├── components/ # React components
│ │ ├── data/ # Data files and utilities
│ │ ├── hooks/ # Custom React hooks
│ │ ├── lib/ # Library and utility functions
│ │ ├── pages/ # Page components
│ │ ├── App.css # Main application styles
│ │ ├── App.tsx # Main React component
│ │ ├── index.css # Global styles
│ │ ├── main.tsx # Application entry point
│ │ └── vite-env.d.ts # Vite type definitions
│ ├── .gitignore # Git ignore rules
│ ├── bun.lockb # Bun lockfile
│ ├── components.json # Component configuration
│ ├── eslint.config.js # ESLint configuration
│ ├── index.html # HTML template
│ ├── package-lock.json # npm lockfile
│ ├── package.json # Project dependencies
│ ├── postcss.config.js # PostCSS configuration
│ ├── tailwind.config.ts # Tailwind CSS configuration
│ ├── tsconfig.app.json # TypeScript config for app
│ ├── tsconfig.json # TypeScript configuration
│ ├── tsconfig.node.json # TypeScript config for Node
│ └── vite.config.ts # Vite build configuration
│
├── model/ # Deep Learning model code
│ ├── lstm_model.py # LSTM multi-output predictor
│ ├── sarima_model.py # SARIMA time series analysis
│ ├── training_scripts/ # Model training routines
│ └── evaluation/ # Model performance metrics
│
├── data/ # Air quality datasets
│ ├── AirView_Cleaned.csv # Processed sensor data
│ └── preprocessing/ # Data cleaning scripts
│
├── backend/ # FastAPI/Flask server
│ ├── app.py # Model serving API
│ └── requirements.txt Python dependencies
│
└── docs/ # Documentation & research
└── references.md # Research papers and citations

## Machine Learning Models

### LSTM Neural Network Architecture
```python
Sequential([
    LSTM(128, activation='relu', return_sequences=True, input_shape=(24, 5)),
    Dropout(0.2),
    LSTM(64, activation='relu'),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dense(5)  # Multi-output: AT, RH, PM2.5, PM10, CO2
])
SARIMA Model
Order: (1,1,1)
Seasonal Order: (1,1,1,24) for daily seasonality
Features: Individual prediction for each air quality parameter
Model Performance
LSTM Results (Last 30 Days)

Parameter	RMSE	MAE
AT	1.49	1.26
RH	4.93	3.80
PM2.5	8.05	7.15
PM10	28.53	21.01
CO2	11.30	7.24

SARIMA Results (Last 30 Days)
Parameter	MAE	RMSE	MAPE
AT	0.5992	0.0484	1.86%
RH	2.9564	4.7647	5.37%

How It Works
Data Collection: Sensors capture real-time air quality parameters (PM2.5, temperature, RH, etc.)
Biochar Filtration: Physical filtration of pollutants using sustainable biochar technology
Model Prediction: Dual-model approach (LSTM + SARIMA) for robust forecasting
Dashboard Visualization: Interactive React frontend displays real-time data and predictions
Alert System: Notifications for poor air quality conditions
Getting Started
Prerequisites
Python 3.8+
Node.js 16+
Bun or npm
Installation
1.Install backend dependencies
cd backend
pip install -r requirements.txt
2.Install frontend dependencies
cd ../frontend
npm install  # or bun install
3.Run the backend server
cd ../backend
python app.py
4.Start the frontend development server
cd ../frontend
npm run dev  # or bun run dev
5.Access the dashboard
Open http://localhost:3000 in your browser
Model Training
To train the LSTM model with your data:
# Preprocess your data
python model/preprocessing/clean_data.py
# Train the LSTM model
python model/training_scripts/train_lstm.py
# Evaluate model performance
python model/evaluation/evaluate_model.py
Future Roadmap
Wearable integration for personalized risk alerts
Deployable IoT-based prototype with biochar filters
Mobile app support for real-time tracking
Advanced ensemble modeling techniques
Real-time API integration with environmental agencies
Predictive maintenance for biochar filter systems
License
This project is licensed under the MIT License - see the LICENSE file for details.
References
WaveNet-inspired architecture for time series forecasting
Biochar filtration research papers
Air quality monitoring standards and guidelines
