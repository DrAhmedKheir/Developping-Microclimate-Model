# Developping-Microclimate-Model
🌿 Microclimate Forecasting Model for Agroforestry Systems
🔍 Purpose
This LSTM-based model was developed to predict microclimate conditions using only macroclimate data , specifically tailored for agroforestry environments . It enables microclimate simulation where direct sensor measurements are unavailable and serves as a critical component in the hybrid Hi-sAFe + ML framework presented in our Environmental Research Letters (ERL) publication.

🗂️ Data Sources
Macroclimate inputs : NASA POWER hourly data (solar radiation, air temperature, humidity, wind speed, etc.)

Microclimate responses : High-resolution IoT sensor data from the Wendhausen agroforestry trial (Germany), at four distances from tree strips (1 m, 4 m, 7 m, 24 m)

🧠 Model Overview
Architecture : Long Short-Term Memory (LSTM) Neural Network

Input (Predictors) :

Hourly macroclimate variables

One-hot encoded distance from trees

Output (Predicted Variables) :

Solar radiation (W/m²)

Soil moisture at 15 cm depth (m³/m³)

Soil temperature at 15 cm (°C)

Air temperature (°C)

Wind speed (m/s)

🏋️‍♂️ Training setup
Sequence length : 24-hour input → 3-hour ahead prediction

Data split : Train (70%) – Validation (15%) – Test (15%)

Loss function : Mean Squared Error (MSE)

Optimizer : Adam

Normalization : MinMaxScaler (fitted and saved)

📊 Performance on Test Data
variable	MAE	RMSE	R²
Solar Radiation (W/m²)	50.36	104.99	0.70
Soil Moisture (m³/m³)	0.03	0.04	0.83
Soil Temperature (°C)	0.92	1.23	0.96
Air Temperature (°C)	1.27	1.62	0.96
Wind Speed ​​(m/s)	0.33	0.46	0.72

🌍 Application in ERL Study
The trained model was applied to simulate microclimate conditions at 30°, 40°, 50°, and 60° latitudes using only macroclimate data. The resulting predictions were used to fill environmental input gaps in Hi-sAFe simulations , enabling a hybrid Hi-sAFe + ML approach to estimate crop yield and nutrient quality across climates.

📦 Files Included
microclimate_lstm_model.h5– Trained LSTM model

MacroClimateHourly.csv– Example macroclimate input

Microclimate.csv– Raw sensor training dataset

evaluate_model_metrics.csv– Summary of prediction accuracy

prediction_scatter.png– Visualization comparing predicted vs. observed

🚀 Future Directions
To improve robustness and generalizability, future work will:

Add biophysical predictors (tree type, height, canopy width, orientation, soil type)

Integrate multi-site datasets , eg, France (microclimate data) and Mediterranean systems

Transition to Transformer models or physics-informed ML for long-term generalization

