# 🌾 Bharat-AgriVision 2047

AI-powered crop health assistant for Indian farmers supporting Hindi and English.

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Configure AWS credentials:
```bash
aws configure
```
Enter your AWS Access Key ID, Secret Access Key, and region (us-east-1).

3. Run the application:
```bash
streamlit run app.py
```

## Features

- Bilingual support (Hindi & English)
- Crop health diagnostics
- Organic solutions
- Mobile-friendly interface
- Powered by AWS Bedrock (Claude 3 Haiku)

## AWS Bedrock Setup

Ensure you have:
- AWS account with Bedrock access
- Claude 3 Haiku model enabled in your region
- Proper IAM permissions for bedrock-runtime

## Usage

1. Select your preferred language
2. Enter crop name
3. Describe symptoms
4. Get AI-powered diagnosis and organic solutions
