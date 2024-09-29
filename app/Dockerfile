# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install system dependencies and Python packages
RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    && pip install --upgrade pip \
    && pip install -r requirements.txt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Collect static files
# RUN python manage.py collectstatic --noinput

# Expose port 8000
EXPOSE 8000

# Run Gunicorn server for production-ready deployment
CMD ["gunicorn", "gas_utility_service.wsgi:application", "--bind", "0.0.0.0:8000"]
