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


RUN echo "Contenido del workspace:" && \
    ls -la /home/carlos && \
    echo "Build files encontrados:" && \
    find /home/carlos -name build.xml


RUN XALAN_DIR=$(dirname "$(find /home/carlos -path '*xalan*/build.xml' | head -1)") && \
    echo "Xalan encontrado en: $XALAN_DIR" && \
    echo "$XALAN_DIR" > /tmp/xalan_path


RUN cd "$(cat /tmp/xalan_path)" && ant


WORKDIR /home/carlos/dacapobench/benchmarks


RUN XALAN_DIR=$(cat /tmp/xalan_path) && \
    sed -i "s#/home/carlos/Documentos/xalan#$XALAN_DIR#g" bms/xalan/build.xml


RUN ant xalan


RUN chmod +x /home/carlos/run_energy_xalan.sh


CMD ["/home/carlos/run_energy_xalan.sh"]
