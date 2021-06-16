FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jdk AS builder
RUN git clone https://github.com/yakiyoshi/spring-petclinic.git
WORKDIR /app/spring-petclinic
RUN ./mvnw package -s settings.xml

FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jre
COPY --from=builder /app/spring-petclinic/target/*.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
EXPOSE 8080
