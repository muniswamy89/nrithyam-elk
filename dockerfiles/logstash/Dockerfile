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

RUN wget https://download.elastic.co/logstash/logstash/packages/debian/logstash_1.5.3-1_all.deb -O /tmp/logstash.deb && \
    dpkg -i /tmp/logstash.deb ; \
    dpkg -i /tmp/logstash-contrib.deb ; \
    apt-get -f -y install && \
    rm -rf /tmp/logstash.deb /tmp/logstash-contrib.deb
COPY logstash.sample.conf /etc/logstash.sample.conf
ENTRYPOINT ["/opt/logstash/bin/logstash"]
CMD []
