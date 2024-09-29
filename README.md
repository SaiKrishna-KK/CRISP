# CROSS: Client Risk, Sentiment Analysis, and Satisfaction Optimization

## Project Overview
**CROSS** is a financial services analysis platform that leverages Natural Language Processing (NLP) and Machine Learning to evaluate daily interactions and portfolios of clients, providing a comprehensive **Client Satisfaction Score**. This platform is designed to empower financial advisors and portfolio managers with deep insights into client sentiment, portfolio performance, and overall satisfaction, enabling them to identify potential risks, improve engagement, and ultimately increase client retention.

### Problem Statement:
Managing client satisfaction is a complex task for financial service firms. To ensure continued engagement, firms must track not only the performance of client portfolios but also monitor and analyze daily communications, such as emails, phone calls, and chats. A disjointed view of these elements can lead to a poor understanding of a client’s true satisfaction and result in overlooked risks. **CROSS** bridges this gap by integrating sentiment and risk analysis to provide a holistic view of each client’s status.

### Key Features:
- **Sentiment Analysis**: Automatically analyzes and categorizes daily communications to gauge client sentiment.
- **Risk Analysis**: Evaluates daily changes in client portfolios to compute risk levels and identify performance trends.
- **Client Satisfaction Scoring**: Integrates sentiment and risk scores to generate an overall satisfaction score, identifying high-priority clients who may require immediate attention.
- **Dashboard Visualization**: Displays all analysis results on a user-friendly dashboard (not included in this repository) for quick and intuitive access.

## Components of CROSS:
The project is divided into three main scripts, each handling a specific aspect of the analysis pipeline:

1. **Sentiment Analysis (`sentiment_analysis.py`)**:
   - Analyzes daily client communications (emails, phone call notes, and chat logs) using OpenAI's GPT model.
   - Outputs: Daily sentiment summaries stored in the `dailysentiments` collection.

2. **Risk Analysis (`risk_analysis.py`)**:
   - Analyzes the daily changes in client portfolios to compute a risk score and risk level.
   - Outputs: Daily risk summaries stored in the `dailyrisks` collection.

3. **Client Satisfaction Analysis (`client_satisfaction.py`)**:
   - Integrates daily risk and sentiment data to compute a comprehensive **Client Satisfaction Score**.
   - Outputs: Satisfaction levels, scores, and key reasons stored in the `clientSatisfaction` collection.

4. **Main Execution Script (`main.py`)**:
   - Runs the entire pipeline by sequentially executing the three scripts.

### Data Flow and Architecture
The application is built using a modular approach, with separate MongoDB collections for storing intermediate and final results:

1. **`clientInteraction`**: Stores raw client interactions data (emails, chats, phone call notes).
2. **`dailysentiments`**: Stores daily sentiment scores and summaries for each client.
3. **`portfolios`**: Contains information about each client’s portfolio, including daily changes in value.
4. **`dailyrisks`**: Stores daily risk analysis and performance trends for each client portfolio.
5. **`clientSatisfaction`**: Final output collection storing the overall satisfaction levels, scores, and reasons.

### How CROSS Works:
1. **Sentiment Analysis**:
   - Reads data from the `clientInteraction` collection.
   - Uses OpenAI's GPT to classify the sentiment of each daily interaction and generates a daily sentiment summary.
   - Stores the results in the `dailysentiments` collection.

2. **Risk Analysis**:
   - Reads portfolio data from the `portfolios` collection.
   - Computes risk scores based on daily volatility and profit/loss trends.
   - Stores the results in the `dailyrisks` collection.

3. **Client Satisfaction Analysis**:
   - Integrates data from both `dailysentiments` and `dailyrisks` collections.
   - Uses OpenAI’s GPT to produce a final client satisfaction score.
   - Stores the satisfaction results in the `clientSatisfaction` collection.

## Prerequisites:
- **Python**: 3.8+
- **MongoDB Atlas** (or local MongoDB setup)
- **OpenAI API Key** for GPT models.

## Setup Guide:
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repository/CROSS.git
   cd CROSS
   ```

2. **Install the Required Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure MongoDB**:
   - Create a MongoDB Atlas cluster or use a local setup.
   - Update the connection URI in the `.env` file:
     ```
     MONGODB_URI="your_mongodb_connection_uri"
     ```

4. **Create a `.env` File**:
   Add a `.env` file in the root directory with the following variables:
   ```ini
   OPENAI_API_KEY=<your_openai_api_key>
   MONGODB_URI=<your_mongodb_uri>
   ```

5. **Run the Main Script**:
   Execute the `main.py` script to run the entire pipeline:
   ```bash
   python main.py
   ```

## Script Descriptions:

### `main.py`
Runs all the scripts in the required order and handles any errors during execution.

### `sentiment_analysis.py`
Generates daily sentiment analysis based on client interactions.

### `risk_analysis.py`
Analyzes portfolio risk based on daily changes and performance trends.

### `client_satisfaction.py`
Integrates daily sentiment and risk data to produce the final client satisfaction score.

## Dashboard Integration:
CROSS includes a separate front-end dashboard (not part of this repository) to visualize the sentiment, risk, and satisfaction data for each client.

## Future Enhancements:
1. **Expand Portfolio Data**: Add more assets and performance metrics.
2. **Incorporate Market Trends**: Include external market data to contextualize client performance.
3. **Real-Time Updates**: Implement real-time data pipelines for continuous monitoring.

## Troubleshooting:
1. **MongoDB Connection Issues**:
   - Verify the MongoDB URI in the `.env` file.
   
2. **OpenAI API Errors**:
   - Ensure that your OpenAI API key is correctly set in the `.env` file.

3. **Script Execution Errors**:
   - Run each script individually to identify specific issues.

---

**Project Name**: **CROSS**  
**Author**: Sai Krishna Vishnumolakala, Siddu

**Contact**: svishnu1@umbc.edu  
**Version**: 1.0.0  

---

