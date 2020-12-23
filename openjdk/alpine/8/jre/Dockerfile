FROM openjdk:8-jdk-alpine

ARG TZ
ENV TZ=${TZ}

RUN apk update \
        && apk add tzdata \
        && apk add openntpd \
        && apk add busybox-extras

RUN cp /usr/share/zoneinfo/${TZ} /etc/localtime
RUN echo ${TZ} > /etc/timezone

COPY ./tzupdater-2.3.2/tzupdater.jar /tmp/tzupdater.jar
COPY ./tzdata/tzdata-latest.tar.gz /tmp/tzdata.tar.gz

CMD "java -jar /tmp/tzupdater.jar -f -l file:///tmp/tzdata.tar.gz"

ENTRYPOINT date
