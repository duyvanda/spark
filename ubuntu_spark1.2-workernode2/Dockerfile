FROM duyvanda/pyspark:1.1a
LABEL maintainer="duyvanda"

# Never prompt the user for choices on installation/configuration of packages
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux
# ENV CORES=4
# ENV MEMORY=16G
ENV SPARK_WORKER_WEBUI_PORT 8082
ENV SPARK_WORKER_LOG /usr/local/spark/logs
ENV TZ="Asia/Bangkok"
ENV PYARROW_IGNORE_TIMEZONE 1

COPY ./requirements.txt /requirements.txt

RUN pip install -r requirements.txt

EXPOSE 8082
ENTRYPOINT $SPARK_HOME/bin/spark-class org.apache.spark.deploy.worker.Worker spark://10.0.150.35:7077
CMD [ echo "executable" ]
# docker service create --name spark_worker2 --network merapbi --constraint node.hostname==binode2 -p 8082:8082 duyvanda/pyspark:3.2.0-workernode2
# docker build -t duyvanda/pyspark:3.1.2-workernode2 . --on binode2