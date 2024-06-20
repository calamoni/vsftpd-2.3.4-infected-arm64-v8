FROM arm64v8/ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y
RUN apt-get install -y git

WORKDIR /root/

RUN git clone https://github.com/calamoni/vsftpd-2.3.4-infected-arm64-v8.git && \
	cd vsftpd-2.3.4-infected-arm64-v8.git && \
	cd vsftpd-2.3.4 && \
	mv * /root/ && \
	cd /root && \
	rm -rfv vsftpd-2.3.4-infected-arm64-v8.git
 
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

RUN chmod +x /usr/local/sbin/vsftpd

RUN echo 'echo Started FTP Server@ `hostname -i 2>/dev/null`:21' > /root/run.sh && \
	echo "/usr/local/sbin/vsftpd" >> /root/run.sh

CMD ["/bin/bash", "-c", "/bin/bash run.sh"]
