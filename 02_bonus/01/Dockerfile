# SCALA

FROM debian:jessie

# IMPORT PACKAGE

#COPY scala-2.12.1.deb /app/scala.deb


WORKDIR /app

RUN echo "deb http://ftp.debian.org/debian jessie-backports main" >>  /etc/apt/sources.list
RUN apt-get update -y && apt-get upgrade -y


# DEPENDENCIES

RUN apt-get install curl -y

RUN apt install -t jessie-backports openjdk-8-jre-headless ca-certificates-java -y
RUN apt-get install openjdk-8-jre -y

# DOWNLOAD SCALA

RUN curl https://downloads.lightbend.com/scala/2.12.2/scala-2.12.2.deb > scala.deb

# INSTALL

RUN dpkg -i scala.deb

# COMMANDS

CMD scala
