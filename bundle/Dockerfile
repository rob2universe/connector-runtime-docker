# Configure the connector runtime version
ARG RUNTIME_VERSION=0.10.0
FROM camunda/connectors:${RUNTIME_VERSION}

# Configure versions of included connectors
ARG CAMUNDA_CONNECTORS_VERSION='0.20.2'

# Download connectors from maven central
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-aws-lambda/${CAMUNDA_CONNECTORS_VERSION}/connector-aws-lambda-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-google-drive/${CAMUNDA_CONNECTORS_VERSION}/connector-google-drive-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-http-json/${CAMUNDA_CONNECTORS_VERSION}/connector-http-json-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-graphql/${CAMUNDA_CONNECTORS_VERSION}/connector-graphql-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-rabbitmq/${CAMUNDA_CONNECTORS_VERSION}/connector-rabbitmq-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-sendgrid/${CAMUNDA_CONNECTORS_VERSION}/connector-sendgrid-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-slack/${CAMUNDA_CONNECTORS_VERSION}/connector-slack-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-sns/${CAMUNDA_CONNECTORS_VERSION}/connector-sns-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-sqs/${CAMUNDA_CONNECTORS_VERSION}/connector-sqs-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-kafka/${CAMUNDA_CONNECTORS_VERSION}/connector-kafka-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-microsoft-teams/${CAMUNDA_CONNECTORS_VERSION}/connector-microsoft-teams-${CAMUNDA_CONNECTORS_VERSION}-with-dependencies.jar /opt/app/
