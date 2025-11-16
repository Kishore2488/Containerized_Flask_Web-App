FROM python:3.11-slim

# OS deps (if needed)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

ENV FLASK_APP=app.py
ENV PORT=8000

CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:8000", "app:app"]
EXPOSE 8000
