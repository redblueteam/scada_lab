# Use a lightweight Debian base image
FROM debian:stable-slim

# Install necessary packages for OpenPLC
# - build-essential: For compiling software
# - git: For cloning OpenPLC repository
# - python3, python3-pip: Python and its package installer
# - autoconf, automake, libtool, libusb-1.0-0-dev, pkg-config, cmake, wget, zip: Other build dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    python3 \
    python3-pip \
    autoconf \
    automake \
    libtool \
    libusb-1.0-0-dev \
    pkg-config \
    cmake \
    wget \
    zip \
    && rm -rf /var/lib/apt/lists/*

# Clone OpenPLC repository
RUN git clone https://github.com/thiagoralves/OpenPLC_v3.git /opt/OpenPLC_v3

# Navigate into the OpenPLC directory
WORKDIR /opt/OpenPLC_v3

# Run the OpenPLC installation script for Linux (headless, without GUI)
RUN ./install.sh linux --no-gui

# Expose necessary ports:
# 502: Modbus TCP (standard for PLC communication)
# 8080: OpenPLC web interface
EXPOSE 502 8080

# Command to run OpenPLC when the container starts
CMD ["/opt/OpenPLC_v3/start_openplc.sh"]
