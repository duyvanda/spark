FROM duyvanda/pyspark:1.1a
LABEL maintainer="duyvanda"

# Never prompt the user for choices on installation/configuration of packages
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux
ENV CORES=4
ENV MEMORY=16G
ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8081
ENV SPARK_MASTER_LOG /usr/local/spark/logs
ENV TZ="Asia/Bangkok"
ENV PYARROW_IGNORE_TIMEZONE 1

COPY ./requirements.txt /requirements.txt

RUN pip install -r requirements.txt

EXPOSE 8081
ENTRYPOINT $SPARK_HOME/bin/spark-class org.apache.spark.deploy.worker.Worker -c 4 -m 16G spark://spark-master:7077
CMD [ echo "executable" ]
# docker service create --name spark_worker --network merapbi -p 8081:8081 duyvanda/pyspark:3.2.0-worker
# docker build -t duyvanda/pyspark:3.2.0-worker .