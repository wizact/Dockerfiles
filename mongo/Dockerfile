FROM ubuntu:latest

MAINTAINER Amir Mohtasebi <amir.mohtasebi@gmail.com>

# Importing MongoDB GPG key and create list file
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.0.list

# Installing latest version of MongoDB
RUN apt-get update && apt-get install -y mongodb-org

# Create data directory
RUN mkdir -p /data/db
VOLUME ["/data/db"]

# Expose ports
EXPOSE 27017
# Only if we need admin interface to be exposed
EXPOSE 28017

# Run Mongod
ENTRYPOINT ["/usr/bin/mongod"]

# Only if we need rest and httpinterface enabled
CMD ["--rest", "--httpinterface", "--smallfiles"]
