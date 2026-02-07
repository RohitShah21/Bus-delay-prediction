🚌 Real-Time Bus Delay Prediction System with PySpark
Project Overview
This project involves building an end-to-end Machine Learning pipeline using Apache Spark (PySpark) to predict public transit bus delays. The model leverages historical trip data and simulated real-time traffic sensors to estimate arrival delays with high accuracy.

The solution includes data cleaning, synthetic feature engineering, exploratory data analysis (EDA), model training using Random Forest Regression, and an interactive command-line prediction tool.

🚀 Key Features
Big Data Processing: Utilizes PySpark for efficient handling of large datasets.

Synthetic Feature Engineering: Generates a Live_Traffic_Index to simulate real-time IoT traffic sensor data, significantly boosting model accuracy.

Machine Learning Pipeline: Implements a scalable pipeline using StringIndexer, VectorAssembler, and RandomForestRegressor.

Data Visualization: Converts processed data to Pandas for rich visualizations using Matplotlib and Seaborn.

Interactive Prediction System: A user-friendly CLI loop that allows users to input trip details (Route, Line, Time, Traffic) and receive instant delay predictions.

🛠️ Technologies Used
Language: Python 3.10+

Core Engine: Apache Spark (PySpark 3.5.7)

Machine Learning: Spark MLlib (Random Forest, Pipelines)

Data Manipulation: Pandas, Spark SQL

Visualization: Matplotlib, Seaborn

Environment: Jupyter Notebook

📂 Dataset
The model relies on a CSV file named final_bus_dataset_multiline.csv. Key columns include:

Actual_Delay_Minutes (Target Variable)

Hour_of_Day

Day_of_Week

Route_Type

LineName

Live_Traffic_Index (Synthetically generated during runtime)

📊 Workflow
1. Data Loading & Cleaning
Initializes a Spark Session.

Removes duplicates and null values.

Filters out extreme outliers (delays > 100 minutes) to stabilize the model.

2. Feature Engineering
Traffic Simulation: Creates a Live_Traffic_Index (0-10 scale) by adding random noise to the actual delay, simulating imperfect real-world traffic sensor data.

Categorical Indexing: Converts string inputs (Day_of_Week, Route_Type, LineName) into numerical indices using StringIndexer.

Vector Assembly: Compiles all features into a single vector column for Spark ML.

3. Visualization
Generates insights on:

Delay distribution histograms.

Average delay by Hour of Day.

Impact of Route Type and Bus Line on delays.

Heatmap showing delay intensity (Day vs. Hour).

4. Model Training & Evaluation
Algorithm: Random Forest Regressor (numTrees=50, maxDepth=8).

Split: 80% Training / 20% Testing.

Scaling: Features are standardized using StandardScaler.

5. Interactive Application
The final cell of the notebook launches a text-based interface allowing users to manually test specific scenarios (e.g., "What is the delay on Line 25 on a Wednesday at 8 AM with heavy traffic?").

📈 Model Performance
Based on the latest training run included in the notebook:

R² (R-Squared): ~0.74 (The model explains 74% of the variance in delays).

RMSE (Root Mean Squared Error): ~3.70 minutes.

Top Feature Importances:

Live_Traffic_Index (Dominant factor)

Hour_of_Day

Day_of_Week

⚙️ Setup & Installation
Prerequisites:

Python installed.

Java (JDK 8 or 11) installed (Required for Spark).

Hadoop binaries (if running on Windows).

Install Python Libraries:

Bash

pip install pyspark pandas matplotlib seaborn
Environment Variables:

Ensure JAVA_HOME and HADOOP_HOME are set correctly in your system environment or within the first cell of the notebook.

Run the Notebook:

Bash

jupyter notebook "bus prediction model.ipynb"
🖥️ Usage Example (Interactive Mode)
Once the notebook is executed, the final cell will prompt:

Plaintext

=== 📝 ENTER TRIP DETAILS ===
Select Day: 1. Wednesday
Select Route Type: 2. Commuter Express
Select Bus Line: 3. Line 25
Enter Hour (0-23): 12
Simulate Live Traffic (0-10): 10

🔮 PREDICTION RESULT
------------------------------------
⏱️ ESTIMATED DELAY: 31.5 minutes
🚨 Status: SEVERE DELAY
🔮 Future Improvements
Replace synthetic traffic data with a real API (e.g., Google Maps Traffic API).

Integrate weather API data for real-time weather features.

Deploy the PySpark model using Flask or Streamlit for a web-based UI.
