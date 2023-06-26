FROM python:3.6.15-slim

WORKDIR /source

COPY ./requirements-cpu.txt ./
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir -r requirements-cpu.txt

# Keep container running
CMD ["tail", "-f", "/dev/null"]