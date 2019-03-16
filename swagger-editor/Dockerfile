FROM ubuntu:latest

LABEL maintainer="amir.mohtasebi@gmail.com"

RUN apt-get update
RUN apt-get -y install git curl
RUN curl --silent --location https://deb.nodesource.com/setup_0.12 | sudo bash -
RUN sudo apt-get install --yes nodejs

RUN mkdir -p /app/swagger/
RUN cd /app/swagger/
RUN git clone https://github.com/swagger-api/swagger-editor.git /app/swagger/

EXPOSE 8282

CMD ["npm", "start"]
