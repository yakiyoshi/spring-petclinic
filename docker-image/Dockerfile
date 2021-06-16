FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jdk AS builder
RUN git clone https://github.com/yakiyoshi/spring-petclinic.git
WORKDIR spring-petclinic
RUN ./mvnw package -s settings.xml && \
    cp target/*.jar /tmp/app.jar

FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jre
COPY --from=builder /tmp/app.jar .
ENTRYPOINT ["java","-jar","app.jar"]
EXPOSE 8080
