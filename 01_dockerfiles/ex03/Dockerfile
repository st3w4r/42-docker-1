FROM debian

RUN apt-get update -y && apt-get upgrade -y

#DEPENDENCIES
RUN apt-get install git -y
RUN apt-get install wget -y

# INSTALL GO
WORKDIR $HOME/local
RUN wget https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz
RUN tar -xzvf go1.8.linux-amd64.tar.gz

ENV GOROOT=$HOME/local/go
ENV GOPATH=$HOME/gogs
ENV PATH=$PATH:$GOROOT/bin:$GOPATH/bin

WORKDIR $GOPATH/src/github.com/gogits

#DOWNLOAD GOGS FROM DEVELOP BRANCH
RUN  git clone --depth=1 -b develop https://github.com/gogits/gogs
WORKDIR $GOPATH/src/github.com/gogits/gogs
RUN go build

# START
ENTRYPOINT ./gogs web
