# Imagem Ubuntu
FROM ubuntu:22.04

# Definir variáveis de ambiente
ENV SCALA_VERSION=2.12.15 \
    SPARK_VERSION=3.5.4 \
    HADOOP_VERSION=3 \
    PYTHON_VERSION=3.9

# Instalar dependências
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    openjdk-11-jdk \
    python${PYTHON_VERSION} \
    python3-pip \
    scala \
    && rm -rf /var/lib/apt/lists/*

# Instalar Spark
RUN wget -qO- https://dlcdn.apache.org/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz | tar -xz -C /opt/
RUN mv /opt/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} /opt/spark

# Definir variáveis do Spark
ENV SPARK_HOME=/opt/spark \
    PATH="/opt/spark/bin:/opt/spark/sbin:${PATH}"

# Instalar PySpark e outras dependências
RUN pip3 install --no-cache-dir pyspark

# Criar diretório para persistência de bibliotecas Python
VOLUME /root/.local

# Definir diretório de trabalho
WORKDIR /laboratorio-spark


# Cria os diretórios onde os volumes serão montados
RUN mkdir -p /laboratorio-spark/arquivos_laboratorio /laboratorio-spark/arquivos_laboratorio

#Uso interativo do container
#CMD ["/bin/bash"]

#mantendo o container em execucao
CMD ["tail", "-f", "/dev/null"]