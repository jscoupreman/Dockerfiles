FROM debian:stable
RUN apt-get update 

# installs ping, netstat for debugging purposes
# installing tzdata will fix NESSUS_TZ_DIR related warning
RUN apt-get install -y net-tools iputils-ping tzdata wget

RUN rm -rf /var/lib/apt/lists/*

RUN wget https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads/10703/download?i_agree_to_tenable_license_agreement=true -O /tmp/Nessus.deb

RUN dpkg -i /tmp/Nessus.deb

RUN rm /tmp/Nessus.deb

# defaut Nessus Scanner port (https)
EXPOSE 8834

ENTRYPOINT [ "/opt/nessus/sbin/nessusd" ]
# ENTRYPOINT [ "/etc/init.d/nessusd start" ]