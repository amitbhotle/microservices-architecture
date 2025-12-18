# ---------- BUILD STAGE ----------
FROM python:3.11-slim AS builder

WORKDIR /app

# dependencies list copy
COPY requirements.txt .

# install dependencies
RUN pip install --no-cache-dir -r requirements.txt


# ---------- RUNTIME STAGE ----------
FROM python:3.11-slim

WORKDIR /app

# builder stage se installed libs copy
COPY --from=builder /usr/local/lib /usr/local/lib
COPY --from=builder /usr/local/bin /usr/local/bin

# application code copy
COPY . .

# worker start
CMD ["python", "worker.py"]

