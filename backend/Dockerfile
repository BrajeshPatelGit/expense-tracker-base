# Use an official Python runtime as a parent image
FROM python:3.12-slim

# Install system dependencies needed by psycopg2 and general build tooling
RUN apt-get update \
    && apt-get install --no-install-recommends -y \
       build-essential \
       libpq-dev \
       gcc \
    && rm -rf /var/lib/apt/lists/*

# Set a working directory
WORKDIR /app

# Copy requirements first to leverage Docker cache
COPY backend/requirements.txt ./

# Upgrade pip and install dependencies
RUN python -m pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

# Copy backend application code
COPY backend/app ./app
COPY backend/.env ./.env

# Expose the port Uvicorn will use
EXPOSE 8000

# Default command to run the FastAPI app
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
