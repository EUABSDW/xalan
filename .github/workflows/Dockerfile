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


WORKDIR /home/carlos/xalan

COPY . .


RUN echo "Checking Xalan directory"
RUN ls -la /home/carlos/xalan


RUN echo "Building Xalan with Java 8"

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH

RUN java -version

RUN ant


RUN echo "Checking generated Xalan jars"
RUN ls -la /home/carlos/xalan/build


WORKDIR /home/carlos/xalan/dacapobench/benchmarks


RUN echo "Checking DaCapo directory"
RUN pwd
RUN ls -la
RUN find . -maxdepth 3 -name build.xml


RUN echo "Configuring DaCapo JDK 11 path"
RUN echo "jdk.11.home=/usr/lib/jvm/java-11-openjdk-amd64" > local.properties


RUN echo "Checking dependencies"
RUN git --version
RUN cvs --version
RUN svn --version
RUN python --version
RUN node --version


ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$JAVA_HOME/bin:$PATH


RUN java -version


RUN echo "Building DaCapo Xalan benchmark"
RUN ant xalan


RUN chmod +x /home/carlos/run_energy_xalan.sh


CMD ["/home/carlos/run_energy_xalan.sh"]
