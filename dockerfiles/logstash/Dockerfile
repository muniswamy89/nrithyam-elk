FROM nrithyam/ubuntu:latest

RUN apt-get update && \
    apt-get install -y wget 

# Install JDK 8
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" > /etc/apt/sources.list.d/webupd8team-java.list
RUN echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" >> /etc/apt/sources.list.d/webupd8team-java.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
RUN apt-get update
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN apt-get install -y oracle-java8-installer
RUN java -version

RUN wget https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash_1.4.2-1-2c0f5a1_all.deb -O /tmp/logstash.deb && \
    wget https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash-contrib_1.4.2-1-efd53ef_all.deb -O /tmp/logstash-contrib.deb && \
    dpkg -i /tmp/logstash.deb ; \
    dpkg -i /tmp/logstash-contrib.deb ; \
    apt-get -f -y install && \
    rm -rf /tmp/logstash.deb /tmp/logstash-contrib.deb
COPY logstash.conf /etc/logstash.conf
ENTRYPOINT ["/opt/logstash/bin/logstash"]
CMD []
