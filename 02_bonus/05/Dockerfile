FROM ybarbier/42:dev-node

RUN apt-get update -y

ADD src /app
WORKDIR /app
VOLUME /app/log

RUN npm install express

EXPOSE 3000

CMD node app.js > log/app_log.txt 2> log/app_log_err.txt
