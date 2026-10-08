# springboot-vuln-hello-world

Spring Boot 3.1.2 app that returns `Hello World` on `/`. Compiled with Java 21 and
deployable to Cloud Foundry. It deliberately uses old dependency versions with known CVEs
(Spring Boot 3.1.2 and its Tomcat/Spring, plus log4j-core 2.14.1, commons-text 1.9,
jackson-databind 2.12.0 and commons-collections 3.2.1) for scanning demos. The vulnerable
libraries are on the classpath but never called. Do not use in production.

## Build and run

    mvn clean package
    java -jar target/hello-world.jar
    curl localhost:8080/        # Hello World

## Deploy to Cloud Foundry

    mvn clean package
    cf push

`manifest.yml` selects Java 21 through `JBP_CONFIG_OPEN_JDK_JRE`.

## Scan

    trivy fs --scanners vuln .
