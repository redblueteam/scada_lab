# Use a Tomcat image with Java 11
FROM tomcat:9-jre11-openjdk-slim

# Set environment variable for ScadaBR's webapp name
ENV SCADABR_WEBAPP_NAME="ScadaBR"

# Install necessary packages (if any additional for ScadaBR)
RUN apt-get update && apt-get install -y \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Download ScadaBR WAR file
RUN wget https://sourceforge.net/projects/scadabr/files/ScadaBR/0.9.1/ScadaBR.war/download -O /usr/local/tomcat/webapps/${SCADABR_WEBAPP_NAME}.war

# Expose Tomcat's default port (8080) for HTTP access.
# ScadaBR's internal logic often uses this port.
EXPOSE 8080

# Start Tomcat by default when the container runs
CMD ["catalina.sh", "run"]
