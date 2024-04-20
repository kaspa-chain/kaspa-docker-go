FROM ubuntu:latest

ENV KASPA_VERSION=v0.12.17-rc1

WORKDIR /kaspa

RUN apt-get update -y
RUN apt-get install -y wget curl unzip vim

RUN wget https://github.com/kaspanet/kaspad/releases/download/${KASPA_VERSION}/kaspad-${KASPA_VERSION}-linux.zip
RUN unzip kaspad-${KASPA_VERSION}-linux.zip
RUN ls -al ./bin
RUN cp ./bin/* /usr/bin/

COPY scripts/*.bash /scripts/

RUN useradd -r kaspa
RUN mkdir -p /home/kaspa/.rusty-kaspa
RUN chown kaspa:kaspa /home/kaspa/.rusty-kaspa

USER kaspa

CMD ["/scripts/start.bash"]
