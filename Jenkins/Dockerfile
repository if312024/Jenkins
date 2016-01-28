FROM jenkins
USER root
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install s3cmd -y
COPY eWallet.env /home/
COPY eWallet_PR.env /home/
COPY plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt
