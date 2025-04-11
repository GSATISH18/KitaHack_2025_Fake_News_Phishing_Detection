# AI-Powered Fake News & Phishing Detection API

## Overview
I choose this project as my final hackathon submission because I wanted to contribute to solving real-world problems like misinformation and cybersecurity . I always have a doubt regarding whether the link is safe or the news is Legit,that's why I decided to solve the issue that I face and many others,the model is not perfect but I beleive it's good for a prototype,since this is my first Hackathon.I will improve this project  and make it more suitable for real life scenario.About this 
 project ,it is an AI-powered system designed to address two key challenges:
- **Misinformation:** Detect whether news articles are fake or real.
- **Cybersecurity:** Detect if a URL is potentially a phishing attempt.

The solution aligns with the following Sustainable Development Goals:
- **SDG 4 – Quality Education:** Enhancing media literacy by identifying fake news.
- **SDG 9 – Industry, Innovation, and Infrastructure:** Innovating digital security through AI.
- **SDG 16 – Peace, Justice, and Strong Institutions:** Supporting societal trust by combating misinformation and cybercrime.

## Features

- **/predict/fake-news**: Accepts news text and returns a prediction of "Fake News" or "Real News."
- **/predict/phishing**: Accepts a URL (or its features) and returns a prediction of "Phishing URL" or "Legitimate URL."

## Technology Stack

- **Flask**: Used to develop the REST API.
- **scikit-learn**: Utilized to build and train the machine learning models.
- **TF-IDF (Term Frequency-Inverse Document Frequency)**: Used to vectorize textual data (news articles and URLs) for feature extraction.
- **Joblib**: For saving and loading trained machine learning models and vectorizers.
- **Pandas**: For data manipulation and preprocessing.

## Project Structure

HACKATHON KITAHACK/ ├── app/ │ ├── routes.py # Contains all API route definitions │ ├── fake_news_model.pkl # Trained model for fake news detection │ ├── tfidf_vectorizer_fake.pkl # TF-IDF vectorizer for the fake news model │ ├── model_phishing.pkl # Trained model for phishing detection │ └── tfidf_vectorizer_phish.pkl # TF-IDF vectorizer for the phishing model ├── main.py # Main file to start the Flask API ├── requirements.txt # Lists all required Python packages └── README.md # This file



## How It Works

### Data Preprocessing and Model Training

1. **Fake News Detection:**
   - **Data Source:** Combined datasets from `True.csv` (Real News) and `Fake.csv` (Fake News).
   - **Preprocessing:** Text data was cleaned (converted to lowercase, punctuation removed) and labeled (0 = Fake, 1 = Real).
   - **Feature Extraction:** TF-IDF from scikit-learn was used to convert text into numerical vectors.
   - **Model:** A Logistic Regression model (from scikit-learn) was trained on the vectorized data.
   
2. **Phishing Detection:**
   - **Data Source:** The phishing dataset contained URL information along with a status indicator.
   - **Preprocessing:** Data was cleaned, and features such as the URL string were used.
   - **Feature Extraction:** TF-IDF was also applied to convert URL strings into feature vectors.
   - **Model:** A Logistic Regression model was trained for phishing detection.

### API Functionality

The API provides two endpoints:
- **Fake News Endpoint:**  
  **URL:** `/predict/fake-news`  
  **Method:** POST  
  **Input:** JSON with a `"text"` field containing the news content.  
  **Output:** JSON with a `"prediction"` field stating either "Fake News" or "Real News".

- **Phishing Endpoint:**  
  **URL:** `/predict/phishing`  
  **Method:** POST  
  **Input:** JSON with a `"text"` field containing the URL.  
  **Output:** JSON with a `"prediction"` field stating either "Phishing URL" or "Legitimate URL".

## How to Run Locally

### Prerequisites

- Python 3.12 (or an appropriate version) is installed.
- All necessary packages are installed (see `requirements.txt`).  
  To install, run:

```bash
pip install -r requirements.txt


## Steps to Run
Open a command prompt in the project directory

1.Type
  cd "C:\HACKATHON\HACKATHON KITAHACK"
2. Run the application
   python main.py
3.The server should start on http://127.0.0.1:5000/.

4.Test the endpoints using Postman or a similar too,I perosnally used Postman.


# API Testing Examples

a. Fake News Prediction
Endpoint: http://127.0.0.1:5000/predict/fake-news
Method: POST
Content-Type: application/json
Request Body (Raw JSON):
{
  "text": "Scientists declare that eating chocolate can cure cancer!."
}
Response:
{ 
  "prediction": "Fake News"
}

b. Phishing URL Prediction
Endpoint: http://127.0.0.1:5000/predict/phishing
Method: POST
Content-Type: application/json
{
  "text": "https://www.apple.com/support/safety-security"
}
Response:
{ 
  "prediction": "Legitimate URL"
}


# Example API Test Results

Below are actual sample test cases used via Postman:

### Fake News Test
Request:
Body:Raw 
json
POST /predict/fake-news
{ 
"text": "Aliens discovered voting in U.S. elections, according to anonymous sources." 
} 

Response:
{ 
"prediction": "Fake News"
}

### Phising URL Test
Request:
Method: POST
Endpoint: /predict/phishing
Request Body (Raw JSON):
{ 
"text": "Click here to claim your prize: http://fake-prize-link.com" 
} 

Response: 
{
"prediction": "Phishing URL" 
}
 
# PROOF
Have added  folder called "screesnshot",has proof or test data.

# Live Demo Notice

This project runs locally using Flask and is not hosted on a public URL.
To test it, please follow the "How to Run Locally" section above.  
Alternatively, use a tool like [Ngrok](https://ngrok.com) to expose it publicly if needed.

# Final Note

a.Limitations

Model Accuracy: Logistic Regression may not be the most advanced choice for fake news and phishing detection. Performance can be improved and will be improved with more complex models like XGBoost,BERT or relevant model within my reach.
Dataset Quality: The model’s accuracy is dependent on the quality and balance of the training data. 
Misclassification can occur with sensational headlines or new phishing techniques.
Scope: Currently, only text-based fake news and URL-based phishing are detected, limiting the scope to simpler attacks.

b.Future Improvements Plans:

Model Enhancement: Experiment with advanced algorithms for better accuracy.
Real-Time Data: Implement automatic updates to keep the models relevant.
Broader Detection: Expand to detect multimedia-based misinformation and improve phishing detection with additional features.
Deployment: Try host the project publicly (e.g., on Heroku or AWS) for broader access.

c.Important Considerations:

Ethical Use: This tool is intended to assist in identifying misinformation and phishing, but human verification is still crucial.
Legal Compliance: Ensure compliance with data privacy regulations when using the tool.

# References
Datasets: Provided by Kaggle (Fake News and Phishing datasets)
Libraries: Flask, scikit-learn, pandas, joblib, etc.

# Developer Information
Developer: SATISHWARAN
Project: Solo final project for KitaHack 2025
