FROM eclipse-temurin:17-jre-alpine

LABEL maintainer="michael.theis@msg.group"
LABEL ${project.groupId}.${project.artifactId}.project="CloudTrain"
LABEL ${project.groupId}.${project.artifactId}.version="${project.version}"
LABEL ${project.groupId}.${project.artifactId}.description="${project.description}"

COPY *.crt /usr/local/share/ca-certificates/

RUN echo "Update packages, install required packages and update trust store" && \
    apk update && apk add ca-certificates && rm -rf /var/cache/apk/* && \
    update-ca-certificates && \
    echo "Update JRE trust store" && \
    $JAVA_HOME/bin/keytool -importcert -noprompt -trustcacerts -alias zscaler_root_ca -cacerts -storepass changeit -file /usr/local/share/ca-certificates/zscaler.crt



