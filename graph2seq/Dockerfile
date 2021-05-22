FROM tensorflow/tensorflow:1.14.0-py3

RUN apt-get update &&  apt-get install -y git

WORKDIR /root/
RUN git clone https://github.com/IBM/Graph2Seq

ENV TINI_VERSION v0.6.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini
ENTRYPOINT ["/usr/bin/tini", "--"]

