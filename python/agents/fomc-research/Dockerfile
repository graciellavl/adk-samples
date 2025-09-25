# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set environment variables for Poetry
# This tells Poetry to install dependencies in the system's site-packages
ENV POETRY_VIRTUALENVS_CREATE=false \
    PATH="/root/.local/bin:$PATH"

# Install Poetry using pip
RUN pip install --no-cache-dir poetry

# Set the working directory
WORKDIR /app

# Copy dependency files and install them
# Using --no-root prevents installing your project package itself, which we'll copy next
COPY pyproject.toml poetry.lock ./
RUN poetry install --no-root

# Copy the rest of your application's source code
COPY . .

# Command to run your application
CMD ["adk", "web", "--host", "0.0.0.0", "--port", "8080"]
