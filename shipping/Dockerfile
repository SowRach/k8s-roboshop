
#Build

FROM maven AS build

WORKDIR /opt/shipping

COPY pom.xml /opt/shipping/
RUN mvn dependency:resolve
COPY src /opt/shipping/src/
RUN mvn package

#
# Run
#
FROM openjdk:8-jre-alpine3.9

EXPOSE 8080

WORKDIR /opt/shipping

COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]



# FROM maven AS builder
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src /opt/server/src
# RUN mvn clean package

# FROM eclipse-temurin:17-jre-alpine
# EXPOSE 8080
# WORKDIR /opt/server
# COPY --from=builder /opt/server/target/shipping-*.jar /opt/server/shipping.jar
# USER roboshop
# CMD ["java","-jar","shipping.jar"]
