FROM python:3.11.4-slim

WORKDIR /source

COPY ./requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Keep container running
CMD ["tail", "-f", "/dev/null"]