# Use lightweight Python image
FROM python:3.11-slim

# Set working dir
WORKDIR /app

# Prevent Python from writing .pyc files and buffering std/stderr
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Install system dependencies (must be used)
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy and install Python dependencies (all access)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code (important: app folder)
COPY app/ /app/app

# Create data directory for persistence (please care about this)
RUN mkdir -p /app/data

#  port
EXPOSE 8000

# Health check
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -f http://localhost:8000/health || exit 1

#  FastAPI app with uvicorn
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]

