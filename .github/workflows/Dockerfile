FROM ubuntu:26.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
    ant \
    openjdk-8-jdk \
    unzip \
    python3 \
    bc \
    linux-tools-generic \
    && rm -rf /var/lib/apt/lists/*


WORKDIR /home/carlos

COPY . .

RUN echo "Contenido /home/carlos:"
RUN ls -la /home/carlos

RUN echo "Contenido xalan:"
RUN ls -la /home/carlos/xalan

RUN echo "Contenido dacapo:"
RUN ls -la /home/carlos/dacapobench


WORKDIR /home/carlos/xalan

RUN ant


WORKDIR /home/carlos/dacapobench/benchmarks

RUN pwd
RUN ls -la
RUN find . -name build.xml

RUN ant xalan


RUN chmod +x /home/carlos/run_energy_xalan.sh


CMD ["/home/carlos/run_energy_xalan.sh"]
