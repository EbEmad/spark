FROM library/openjdk:8

WORKDIR /usr/local

COPY hdpbootstrap.sh .
COPY ./src  ./src

ENV JAVA_HOME="/usr/local/openjdk-8"
ENV SPARK_MASTER_HOST=0.0.0.0
#ENV JAVA_HOME="/usr/local/java"
ENV PATH="/usr/local/java/bin:${PATH}"
ENV HADOOP_HOME=/usr/local/hadoop
ENV HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
ENV HADOOP_MAPRED_HOME=/usr/local/hadoop
ENV HADOOP_COMMON_HOME=/usr/local/hadoop
ENV HADOOP_HDFS_HOME=/usr/local/hadoop
ENV YARN_HOME=/usr/local/hadoop
ENV PATH="/usr/local/hadoop/bin:${PATH}"
ENV PATH="/usr/local/hadoop/sbin::${PATH}"
ENV HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
ENV HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"
ENV PIP_ROOT_ACTION=ignore

RUN chmod +x hdpbootstrap.sh
RUN chmod +x ./src/start-hadoop.sh
RUN bash hdpbootstrap.sh

# Install Jupyter Notebook
RUN pip install pip --upgrade 
RUN pip install numpy pandas scipy matplotlib sciKit-learn keras jupyterlab notebook findspark pyspark --break-system-packages 




ENTRYPOINT [ "/bin/bash","-c" ]
CMD [ "./src/start-hadoop.sh" ]