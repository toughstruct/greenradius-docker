FROM freeradius/freeradius-server:latest

USER root
RUN apt-get update
RUN apt install -y net-tools vim tcpdump iproute2 curl && apt-get clean  && rm -r /var/lib/apt/lists/*

ARG CACHEBUST=9
COPY freeradius/ /etc/raddb/
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh

RUN curl -k https://toughradius-1251458486.cos.ap-shanghai.myqcloud.com/enterprise/toughradius-latest -o /usr/local/bin/toughradius
RUN chmod +x /usr/local/bin/toughradius

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["toughradius"]