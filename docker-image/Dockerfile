FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jdk AS builder
RUN git clone https://github.com/yakiyoshi/spring-petclinic.git
WORKDIR spring-petclinic
RUN ./mvnw package -s settings.xml

FROM quay.io/yakiyoshi/spring-petclinic:java-1.8-jre
ARG JAR_FILE=spring-petclinic/target/*.jar
COPY --from=builder ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","app.jar"]
EXPOSE 8080
