FROM eclipse-temurin:17.0.7_7-jre

# Configure the connector runtime version
ARG SPRING_ZEEBE_VERSION=8.3.0

RUN mkdir /opt/app

COPY start.sh /start.sh
RUN chmod +x start.sh

# Download Connector Runtime Application from Maven Central
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-runtime-application/${SPRING_ZEEBE_VERSION}/connector-runtime-application-${SPRING_ZEEBE_VERSION}-with-dependencies.jar /opt/app/connector-runtime-application-${SPRING_ZEEBE_VERSION}-with-dependencies.jar

# Use entry point to allow downstream images to add JVM arguments using CMD
ENTRYPOINT ["/start.sh"]
