FROM arm64v8/ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y
RUN apt-get install -y git

WORKDIR /root/

RUN apt-get update && apt-get install -y \
    libssl3 \
    libpam0g \
    wget \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get purge -y git && \
	apt-get -y autoclean && \
	apt-get -y autoremove && \
	apt-get -y clean

RUN mkdir /usr/share/empty/ && \
	mkdir /var/ftp/ && \
	useradd -d /var/ftp ftp

RUN chown root.root /var/ftp && \
	chmod og-w /var/ftp

COPY vsftpd /usr/local/sbin/vsftpd 

COPY vsftpd.conf /etc/

RUN echo 'echo Started FTP Server@ `hostname -i 2>/dev/null`:21' > /root/run.sh && \
	echo "/usr/local/sbin/vsftpd" >> /root/run.sh

CMD ["/bin/bash", "-c", "/bin/bash run.sh"]
