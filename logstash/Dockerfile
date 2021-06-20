ARG logstash_version
FROM docker.elastic.co/logstash/logstash-oss:7.8.0
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD logstash.conf /usr/share/logstash/pipeline/logstash.conf
RUN bin/logstash-plugin install logstash-output-csv
