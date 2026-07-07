FROM ubuntu:26.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
    ant \
    git \
    openjdk-8-jdk \
    openjdk-11-jdk \
    unzip \
    zip \
    wget \
    curl \
    python3 \
    python3-pip \
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


WORKDIR /home/carlos/xalan

COPY . .


RUN echo "Building Xalan with Java 8"

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH

RUN java -version
RUN ant


WORKDIR /home/carlos/xalan/dacapobench/benchmarks


RUN echo "Configuring DaCapo"
RUN echo "jdk.11.home=/usr/lib/jvm/java-11-openjdk-amd64" > local.properties


ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH


RUN java -version
RUN git --version
RUN ls -la


RUN ant xalan


RUN chmod +x /home/carlos/run_energy_xalan.sh


CMD ["/home/carlos/run_energy_xalan.sh"]
