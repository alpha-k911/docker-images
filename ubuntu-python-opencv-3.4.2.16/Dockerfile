FROM ubuntu:16.04

RUN apt-get update && apt-get install -y software-properties-common && add-apt-repository ppa:deadsnakes/ppa && \
    apt-get update && apt-get install -y python3.6 python3.6-dev python3-pip

RUN ln -sfn /usr/bin/python3.6 /usr/bin/python3 && ln -sfn /usr/bin/python3 /usr/bin/python && ln -sfn /usr/bin/pip3 /usr/bin/pip

RUN python3 --version
RUN mkdir src
WORKDIR src/
COPY . .
RUN apt-get install -y libsm6 libxext6 libxrender-dev
RUN pip3 install jupyter
RUN pip3 install opencv-python==3.4.2.16
RUN pip3 install opencv-contrib-python==3.4.2.16


ENV TINI_VERSION v0.6.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini
ENTRYPOINT ["/usr/bin/tini", "--"]

RUN apt-get install -y x11-apps

CMD ["jupyter", "notebook", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]


#ls
