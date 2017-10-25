FROM debian:stretch

EXPOSE 13666

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y lcdproc lcdproc-extra-drivers

CMD ["LCDd", "-f", "-s", "no", "-a", "0.0.0.0"]
