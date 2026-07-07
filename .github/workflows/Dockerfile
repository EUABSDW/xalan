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


WORKDIR /home/carlos/xalan

COPY . .

RUN ant

WORKDIR /home/carlos/xalan/dacapobench/benchmarks

RUN ant xalan

RUN chmod +x /home/carlos/run_energy_xalan.sh

CMD ["/home/carlos/run.sh"]
