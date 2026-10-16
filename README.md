# Faceo Analytics — Emotion Recognition CNN Microservice

Microservice running on default Port 8005 as part of the FACEO Facial Intelligence Platform.

## Features
- **Endpoint**: Microservice API for Emotion Recognition CNN Microservice
- **Container**: Production-ready Dockerfile optimized for Google Cloud Run
- **Port**: Supports dynamic `$PORT` environment variable (defaults to 8005)
- **Cost**: Supports Scale-to-Zero (`min-instances = 0`) and request-based CPU allocation on GCP

## Local Run
```bash
pip install -r requirements.txt
python main.py
```

## Docker Build & Run
```bash
docker build -t emotion-recognition--cnn-api .
docker run -p 8005:8005 -e PORT=8005 emotion-recognition--cnn-api
```

## GCP Cloud Run Deployment
```bash
gcloud run deploy emotion-recognition--cnn-api \
  --source . \
  --region asia-southeast1 \
  --min-instances 0 \
  --max-instances 1 \
  --memory 1Gi --cpu 1 \
  --cpu-throttling \
  --allow-unauthenticated
```
