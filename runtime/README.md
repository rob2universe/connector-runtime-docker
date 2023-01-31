# Camunda 8 Connector Runtime

This module provides a base Docker image including the [Spring Zeebe Connector runtime](https://github.com/camunda-community-hub/spring-zeebe/tree/master/connector-runtime). 
The image starts the Connector Runtime with all `jar` files provided in the `/opt/app` directory as classpath.

To use the image, add at least one Connector to the classpath. We recommend providing JARs with all dependencies bundled.

> :warning: As all Connectors share a single classpath, it can happen that
> different versions of the same dependency are available which can lead to
> conflicts. To prevent this, common dependencies like `jackson` can be shaded and
> relocated inside the connector jar. 
> 
> An example of such relocation with`maven-shade-plugin` can be found in the 
> [Camunda 8 out-of-the-box Connectors repository](https://github.com/camunda/connectors-bundle/blob/cb925c1c5bdab9f55b77d2378be32116dec6f010/connectors/pom.xml#L83).

Example adding a Connector JAR by extending the image

```dockerfile
FROM camunda/connectors:0.5.0

ADD https://repo1.maven.org/maven2/io/camunda/connector/connector-http-json/0.15.0/connector-http-json-0.15.0-with-dependencies.jar /opt/app/
```

Example adding a Connector JAR by using volumes

```bash
docker run --rm --name=connectors -d \
            -v $PWD/connector.jar:/opt/app/connector.jar \                      # Add a connector jar to the classpath
            --network=your-zeebe-network \                                      # Optional: attach to network if Zeebe is isolated with Docker network
            -e ZEEBE_CLIENT_BROKER_GATEWAY-ADDRESS=ip.address.of.zeebe:26500 \  # Specify Zeebe address
            -e ZEEBE_CLIENT_SECURITY_PLAINTEXT=true \                           # Optional: provide security configs to connect to Zeebe
            camunda/connectors:0.5.0
```

# Secrets

To inject secrets into the Connector Runtime, they have to be available in the environment of the Docker container.

For example, you can inject secrets when running a container:

```bash
docker run --rm --name=connectors -d \
           -v $PWD/connector.jar:/opt/app/connector.jar \                      # Add a connector jar to the classpath
           --network=your-zeebe-network \                                      # Optional: attach to network if Zeebe is isolated with Docker network
           -e ZEEBE_CLIENT_BROKER_GATEWAY-ADDRESS=ip.address.of.zeebe:26500 \  # Specify Zeebe address
           -e ZEEBE_CLIENT_SECURITY_PLAINTEXT=true \                           # Optional: provide security configs to connect to Zeebe
           -e MY_SECRET=secret \                                               # Set a secret with value
           -e SECRET_FROM_SHELL \                                              # Set a secret from the environment
           --env-file secrets.txt \                                            # Set secrets from a file
           camunda/connectors:0.5.0
```

The secret `MY_SECRET` value is specified directly in the `docker run` call,
whereas the `SECRET_FROM_SHELL` is injected based on the value in the
current shell environment when `docker run` is executed. The `--env-file`
option allows using a single file with the format `NAME=VALUE` per line
to inject multiple secrets at once.

# Connectors Bundle

The [Connectors Bundle project](https://github.com/camunda/connectors-bundle) contains all available out-of-the-box Connectors provided by Camunda 8.
