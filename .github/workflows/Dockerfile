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

COPY . /home/carlos/xalan

WORKDIR /home/carlos/xalan

RUN ls -la && ant

WORKDIR /home/carlos/dacapobench/benchmarks

RUN sed -i \
    's#/home/carlos/Documentos/xalan#/home/carlos/xalan#g' \
    bms/xalan/build.xml

RUN ant xalan

RUN chmod +x /home/carlos/run_energy_xalan.sh

CMD ["/home/carlos/run_energy_xalan.sh"]
