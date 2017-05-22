FROM debian


RUN apt-get update -y && apt-get upgrade -y

RUN apt-get install curl -y

RUN apt-get install bzip2 -y

# CONFIG TEAMSPEAK

#PORT 
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

#WORKDIR /home/t3
#RUN useradd ts3
#RUN echo "ts3:42born2code" | chpasswd

RUN curl http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 > teamspeak-server.tar.bz2 
RUN tar -xjvf teamspeak-server.tar.bz2
RUN mv teamspeak3-server_linux_amd64 /opt/teamspeak
RUN rm teamspeak-server.tar.bz2

ADD ./start /start

RUN chmod +x /start
RUN useradd teamspeak
RUN mkdir /data
RUN chown teamspeak:teamspeak /data

USER teamspeak
CMD /start
#RUN cd teamspeak3-server_linux_amd64
#WORKDIR teamspeak3-server_linux_amd64
#RUN sh ts3server_startscript.sh start
##COPY ts3 /etc/init.d/ts3
#COPY t3server.ini /home/t3/teamspeak3-server_linux_amd64/t3server.ini
##RUN chmod 755 /etc/init.d/ts3
#RUN chmod 755 /home/t3/teamspeak3-server_linux_amd64/t3server.ini
##USER ts3

#CMD /etc/init.d/teamspeak start
#ENTRYPOINT ["service","teamspeak","start"]
#ENTRYPOINT ["sh","ts3server_minimal_runscript.sh","start"]

