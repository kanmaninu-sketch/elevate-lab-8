# elevate-lab-8
# Dockerized Flask App on AWS EC2

This project demonstrates how to deploy a simple Flask web application using Docker on an Amazon EC2 instance. The app is containerized and exposed to the internet via port 80.

---

## Project Structure

├── app.py # Flask application ├── requirements.txt # Python dependencies ├── Dockerfile # Docker build instructions

Code

---

## Technologies Used

- Python 3.9
- Flask
- Docker
- Amazon EC2 (Amazon Linux)
- Git & GitHub

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
2. Build Docker Image
bash
docker build -t flaskapp .
3. Run the Container
bash
docker run -d -p 80:8080 flaskapp

EC2 Configuration
SSH access using .pem key

Security Group inbound rule: HTTP (port 80) open to public

Flask app listens on port 8080 inside container
---
## Source Code

#app.py
python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from my Dockerized Python Cloud App!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)

#requirements.txt
flask

#Dockerfile
FROM python:3.9

WORKDIR /app

COPY . .

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 8080

CMD ["python", "app.py"]


---

