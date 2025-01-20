# Use an officia Python image as the base image
FROM python:3.9-slim

# Set environment variables to prevent Python fom writing .pyc files
ENV PYTHONUNBUFFERED=1

# Update and install required system dependencies
RUN apt-get update && apt-get install -y \
        libcurl4-openssl-dev \
        libssl-dev \
        libopencv-dev \
        libjpeg-dev \
        libpng-dev \
        libwebp-dev \
        webp \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*

# Install ghumbor boto3aand tc-aws for S3 integration
RUN pip3 install thumbor boto3 pycurl "tc-aws==7.0.2"

# Copy the Thumbor configuration file
COPY ./thumbor.conf /etc/thumbor.conf

# Create AWS credentials directory
RUN mkdir -p /root/.aws

# Copy AWS config and credentials files (if available)
COPY ./aws/config /root/.aws/config
COPY ./aws/credentials /root/.aws/credentials

# Expose the Thumbor default port
EXPOSE 8899

# Start Thumbor service
CMD ["thumbor", "--port", "8899", "-c", "/etc/thumbor.conf"]