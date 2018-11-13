FROM openjdk:8-alpine

ENV CLASSPATH "/src/*.jar"
ENV TK_CONFIG "/config/conf.d"
ENV TK_BOOTSTRAP "/config/bootstrap.cfg"
ENV CLIENT_AUTH "need"

COPY logback.xml /config/
COPY request-logging.xml /config/
COPY conf.d /config/conf.d

EXPOSE 8140

ENTRYPOINT java -Djava.security.egd=/dev/urandom -XX:OnOutOfMemoryError="kill -9 %p" -cp "$(echo $CLASSPATH | tr ' ' ':')" clojure.main -m puppetlabs.trapperkeeper.main --config $TK_CONFIG --bootstrap-config $TK_BOOTSTRAP
