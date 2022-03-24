FROM openjdk:oracle

LABEL manteiner="Innovabit S.A.C."

RUN microdnf install wget -y

WORKDIR /opt

USER root

ENV ARTEMIS_VERSION 2.20.0
ENV ARTEMIS_NAME apache-artemis-${ARTEMIS_VERSION}

RUN wget https://archive.apache.org/dist/activemq/activemq-artemis/${ARTEMIS_VERSION}/${ARTEMIS_NAME}-bin.tar.gz

RUN tar zxvf ${ARTEMIS_NAME}-bin.tar.gz

RUN mv ${ARTEMIS_NAME} artemis

RUN rm ${ARTEMIS_NAME}-bin.tar.gz

ENV ARTEMIS_HOME /opt/artemis

RUN chmod o+x ${ARTEMIS_HOME}/bin/

EXPOSE  1883 \
        5445 \
        5672 \
        8161 \
        9404 \
        61613 \
        61614 \
        61616 

ENV ARTEMIS_DEFAULT_BROKER test
ENV ARTEMIS_BROKER_PASSWORD test
ENV ARTEMIS_BROKER_USERNAME test

RUN ${ARTEMIS_HOME}/bin/artemis create ${ARTEMIS_DEFAULT_BROKER} --allow-anonymous --encoding utf-8 --name ${ARTEMIS_DEFAULT_BROKER} --password ${ARTEMIS_BROKER_PASSWORD} --user ${ARTEMIS_BROKER_USERNAME} --verbose

ENV ARTEMIS_DEFAULT_BROKER_HOME /opt/${ARTEMIS_DEFAULT_BROKER}

RUN chmod o+x ${ARTEMIS_DEFAULT_BROKER_HOME}/bin/

ENV PATH "$PATH:$ARTEMIS_DEFAULT_BROKER_HOME/bin"

WORKDIR ${ARTEMIS_DEFAULT_BROKER_HOME}

COPY bootstrap.xml ${ARTEMIS_DEFAULT_BROKER_HOME}/etc/bootstrap.xml

ENTRYPOINT [ "artemis" , "run"]