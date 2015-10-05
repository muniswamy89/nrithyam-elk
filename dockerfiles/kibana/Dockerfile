FROM nginx:1
RUN apt-get update && apt-get install -y wget ca-certificates
#RUN wget https://download.elastic.co/kibana/kibana/kibana-4.1.1-linux-x64.tar.gz -O /tmp/kibana.tar.gz && \
#  cd /tmp && tar zxf kibana.tar.gz && mv kibana-*/* /usr/share/nginx/html/
RUN wget https://download.elasticsearch.org/kibana/kibana/kibana-3.1.2.tar.gz -O /tmp/kibana.tar.gz && \
    cd /tmp && tar zxf kibana.tar.gz && mv kibana-*/* /usr/share/nginx/html/
EXPOSE 80
