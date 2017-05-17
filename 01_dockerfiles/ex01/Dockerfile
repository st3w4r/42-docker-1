FROM debian


RUN apt-get update && apt-get upgrade

RUN apt-get install curl -y

RUN apt-get install bzip2

# CONFIG TEAMSPEAK
WORKDIR /home/t3
RUN adduser ts3
RUN curl http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 > teamspeak-server.tar.bz2 
RUN tar -xjvf teamspeak-server.tar.bz2
#RUN cd teamspeak3-server_linux_amd64
RUN sh teamspeak3-server_linux_amd64/ts3server_startscript.sh start

COPY teamspeak /etc/init.d/teamspeak
RUN chmod 777 /etc/init.d/teamspeak

#CMD /bin/bash
