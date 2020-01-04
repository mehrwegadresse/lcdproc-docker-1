FROM debian:stretch-slim

EXPOSE 13666

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y git lcdproc lcdproc-extra-drivers

RUN wget -O /usr/lib/lcdproc/mdm166a.so https://raw.githubusercontent.com/mehrwegadresse/lcdproc-docker/master/mdm166a.so

CMD ["LCDd", "-f", "-s", "no", "-a", "0.0.0.0"]
