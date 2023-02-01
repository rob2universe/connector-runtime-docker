FROM eclipse-temurin:17.0.6_10-jre

# Configure the connector runtime version
ARG SPRING_ZEEBE_VERSION=8.1.14

RUN mkdir /opt/app

COPY start.sh /start.sh
RUN chmod +x start.sh

# Download Spring Zeebe Connector Runtime from Maven Central
ADD https://s01.oss.sonatype.org/content/repositories/releases/io/camunda/spring-zeebe-connector-runtime/${SPRING_ZEEBE_VERSION}/spring-zeebe-connector-runtime-${SPRING_ZEEBE_VERSION}-with-dependencies.jar /opt/app/runtime.jar

# Use entry point to allow downstream images to add JVM arguments using CMD
ENTRYPOINT ["/start.sh"]
