FROM ubuntu:26.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
    ant \
    git \
    cvs \
    subversion \
    openjdk-8-jdk \
    openjdk-11-jdk \
    unzip \
    zip \
    wget \
    curl \
    python3 \
    python3-pip \
    python-is-python3 \
    nodejs \
    npm \
    bc \
    make \
    gcc \
    g++ \
    perl \
    sed \
    findutils \
    coreutils \
    linux-tools-generic \
    && rm -rf /var/lib/apt/lists/*


RUN pip3 install --break-system-packages requests


WORKDIR /home/carlos/xalan

COPY . .

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH

RUN ant

WORKDIR /home/carlos/xalan/dacapobench/benchmarks

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH

RUN ant xalan

RUN chmod +x /home/carlos/run_energy_xalan.sh

CMD ["/home/carlos/run_energy_xalan.sh"]
