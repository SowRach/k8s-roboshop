FROM maven AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src /opt/server/src
RUN mvn clean package

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
WORKDIR /opt/server
COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
USER roboshop
CMD ["java","-jar","shipping.jar"]
