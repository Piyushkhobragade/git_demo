API Documentation

This document explains the backend API for this project running on AWS EC2.

Base URL

Your backend runs on your EC2 instance at:
http://<EC2-PUBLIC-IP>:3000/

Replace the port or URL if your backend uses a different one.

Endpoints

2.1 Health Check
Method: GET
Route: /health
Purpose: Check if backend is running
Example Response:
{
"status": "ok",
"message": "Backend is running"
}

2.2 Example Data API
Method: GET
Route: /api/data
Returns a list of sample items
Example Response:
{
"items": [1, 2, 3, 4],
"message": "Sample API data"
}

2.3 POST Submission Example
Method: POST
Route: /api/submit
Request Body Example:
{
"name": "Piyush",
"message": "Test submission"
}
Response Example:
{
"success": true,
"received": {
"name": "Piyush",
"message": "Test submission"
}
}

Error Handling

If an error happens, API returns:
{
"error": true,
"message": "Something went wrong"
}

Deployment Notes

Your backend deploys automatically using GitHub Actions:

Workflow connects to EC2 using SSH

Pulls the latest backend code

Installs dependencies

Restarts the backend service

This removes manual SSH updates.

Future Improvements

You can add:

Database queries using MySQL RDS

Authentication

Logging with CloudWatch

API Gateway + Lambda (serverless upgrade)
