FROM maven:3.8.6-jdk-8 AS MAVEN_BUILD
MAINTAINER leansoftx
COPY pom.xml /build/
COPY src /build/src/
WORKDIR /build/
RUN mvn clean package spring-boot:repackage -Dmaven.test.skip=true

FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=MAVEN_BUILD /build/target/boathouse-product-service-0.0.1-SNAPSHOT /app/
ENTRYPOINT ["java", "-jar", "boathouse-product-service-0.0.1-SNAPSHOT"]
