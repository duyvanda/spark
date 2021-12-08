FROM duyvanda/pyspark:1.1a
LABEL maintainer="duyvanda"

# Never prompt the user for choices on installation/configuration of packages
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux
ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8080
ENV SPARK_MASTER_LOG /usr/local/spark/logs
ENV TZ="Asia/Bangkok"
ENV PYARROW_IGNORE_TIMEZONE 1

COPY ./requirements.txt /requirements.txt

RUN pip install -r requirements.txt

EXPOSE 8080 7077
ENTRYPOINT $SPARK_HOME/bin/spark-class org.apache.spark.deploy.master.Master -h 0.0.0.0
CMD [ echo "executable" ]
# docker service create --name spark-master --network merapbi -p 8080:8080 -p 7077:7077 duyvanda/pyspark:3.2.0-master
# docker build -t duyvanda/pyspark:3.2.0-master .
