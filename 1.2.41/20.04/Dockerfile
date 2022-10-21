FROM ubuntu:20.04
ENV TZ Europe/Paris
ENV DEBIAN_FRONTEND noninteractive
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    apt-get -y install apt-transport-https lsb-core lsb-release net-tools netcat-openbsd sudo wget --no-install-recommends &&\
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    touch /usr/bin/firewall-cmd && \
    chmod +x /usr/bin/firewall-cmd && \
    useradd -m expedition && \
    chmod 755 /root
COPY ./setup /setup
WORKDIR /setup
ENV TERM=xterm
RUN ./initSetup.sh
WORKDIR /
RUN rm -rf /setup /tmp/*
COPY start.sh /
CMD /start.sh
