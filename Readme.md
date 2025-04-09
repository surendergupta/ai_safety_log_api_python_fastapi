# FastAPI Incident API

## Overview
This is a FastAPI-based Incident Management API that allows users to create, retrieve, and delete incidents stored in a MongoDB database.

## Features
- Create an incident
- Retrieve all incidents
- Retrieve a specific incident
- Delete an incident
- MongoDB integration

## Requirements
- Python 3.9+
- FastAPI
- Uvicorn
- Motor (MongoDB Async Driver)

## Installation
### 1. Clone the repository
```bash
git clone https://github.com/surendergupta/ai_safety_log_api_python_fastapi.git
cd ai_safety_log_api_python_fastapi
```

### 2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Set up environment variables
Create a `.env` file and specify your MongoDB URI:
```
MONGO_URI=mongodb://localhost:27017
```

## Running the API
Start the FastAPI server using Uvicorn:
```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

## API Endpoints
### 1. Get all incidents
```http
GET /incidents
```
#### Response
```json
{
  "status_code": 200,
  "message": "All Incidents retrieved",
  "data": [
    {
      "id": "6612f9c2f0d6a92b7e2b3a74",
      "title": "Database Outage",
      "description": "Primary database is down.",
      "severity": "High",
      "reported_at": "2024-04-06T12:00:00"
    }
  ]
}
```

### 2. Create a new incident
```http
POST /incidents
```
#### Request Body
```json
{
  "title": "Network Latency",
  "description": "High latency detected in the API.",
  "severity": "Medium"
}
```
#### Response
```json
{
  "status_code": 201,
  "message": "Incident successfully created",
  "data": {
    "id": "6612fa31f0d6a92b7e2b3a75",
    "title": "Network Latency",
    "description": "High latency detected in the API.",
    "severity": "Medium",
    "reported_at": "2024-04-06T12:30:00"
  }
}
```

### 3. Get a specific incident
```http
GET /incidents/{id}
```
#### Response
```json
{
  "status_code": 200,
  "message": "Incident successfully retrieved",
  "data": {
    "id": "6612fa31f0d6a92b7e2b3a75",
    "title": "Network Latency",
    "description": "High latency detected in the API.",
    "severity": "Medium",
    "reported_at": "2024-04-06T12:30:00"
  }
}
```

### 4. Delete an incident
```http
DELETE /incidents/{id}
```
#### Response
```json
{
  "status_code": 200,
  "message": "Incident successfully deleted",
  "data": null
}
```

## Testing the API
You can test the API using **Swagger UI**:
- Open [http://localhost:8000/docs](http://localhost:8000/docs) in your browser.
- Open [http://localhost:8000/redoc](http://localhost:8000/redoc) in your browser.

Or use **cURL/Postman** to make requests.
