FROM debian:jessie

RUN echo deb http://download.gluster.org/pub/gluster/glusterfs/LATEST/Debian/jessie/apt jessie main > \
      /etc/apt/sources.list.d/gluster.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D5DC52DC && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y glusterfs-server glusterfs-client jq curl && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /var/cache/*

VOLUME ["/data/glusterfs/brick1"]

ADD ./*.sh /opt/rancher/

EXPOSE 24007
EXPOSE 24007/udp
EXPOSE 24008
EXPOSE 24008/udp
EXPOSE 49152

# Add Giddyup
ADD https://github.com/cloudnautique/giddyup/releases/download/v0.11.0/giddyup /usr/local/bin/giddyup
RUN chmod +x /usr/local/bin/giddyup
