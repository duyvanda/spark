FROM duyvanda/pyspark:1.1
LABEL maintainer="Puckel_"

# Never prompt the user for choices on installation/configuration of packages
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux
ENV TZ="Asia/Bangkok"
ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8080
ENV SPARK_MASTER_LOG /usr/local/spark/logs

COPY ./requirements.txt /requirements.txt

RUN pip install -r requirements.txt

EXPOSE 8080 7077
ENTRYPOINT $SPARK_HOME/bin/spark-class org.apache.spark.deploy.master.Master -h 0.0.0.0
CMD [ echo "executable" ]
# docker service create --name spark-master --network merapbi -p 8080:8080 -p 7077:7077 duyvanda/pyspark:3.1.2-master
# docker service create --name spark_worker --network merapbi -p 8081:8081 duyvanda/pyspark:3.1.2-worker
# docker build -t duyvanda/pyspark:3.1.2-master .
