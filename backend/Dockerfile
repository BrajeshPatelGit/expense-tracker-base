# Use an official Python runtime as a parent image
FROM python:3.12-slim

# Set a working directory
WORKDIR /app

# Copy requirements first to leverage Docker cache
COPY requirements.txt .

# RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .
# Expose the port the app runs on
EXPOSE 5001
# Default command to run the Python app
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "5001"]