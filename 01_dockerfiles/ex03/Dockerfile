FROM debian

RUN apt-get update -y && apt-get upgrade -y

#DEPENDENCIES
RUN apt-get install git -y
RUN apt-get install wget -y
#RUN apt-get install postgresql-9.4 -y
#RUN apt-get install sqlite3 -y
RUN apt-get install gcc -y
# RUN POSTGRESQL
#RUN service postgres start

#USER postgres
#RUN createuser git -P < "42born2code"

#RUN chmod 777 /home/git
#USER git
# INSTALL GO
WORKDIR $HOME/local
RUN wget https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz
RUN tar -xzvf go1.8.linux-amd64.tar.gz

ENV GOROOT=$HOME/local/go
ENV GOPATH=$HOME/gogs
ENV PATH=$PATH:$GOROOT/bin:$GOPATH/bin

WORKDIR $GOPATH/src/github.com/gogits

#DOWNLOAD GOGS FROM DEVELOP BRANCH
RUN git clone --depth=1 -b develop https://github.com/gogits/gogs
RUN go get -u -tags "sqlite" github.com/gogits/gogs
WORKDIR $GOPATH/src/github.com/gogits/gogs
RUN go build -tags "sqlite"

# CREATE GIT USER
RUN adduser git
RUN echo "git:born2code" | chpasswd

# CREATE DIRECTORIES
RUN mkdir $GOPATH/src/github.com/gogits/logs
RUN mkdir /root/gogs-repositories
RUN mkdir /data
#RUN chmod 777 /root/gogs-repositories
#RUN chmod 777 $GOPATH/src/github.com/gogits/logs

# START
EXPOSE 5432
EXPOSE 3000

ENV USER=root
RUN echo "root:docker" | chpasswd
#ENTRYPOINT ./gogs web

#RUN service postgresql start
#USER postgres
#RUN createuser git
#RUN "test"

#ENTRYPOINT service postgresql start && su - postgres  && createuser git -P < "test" && createdb gogs  && /bin/bash
#RUN su postgres
#ENTRYPOINT service postgresql start && /bin/bash
# && createuser git -P && createdb gogs && ./gogs web
ENTRYPOINT ./gogs web
#CMD /bin/bash
