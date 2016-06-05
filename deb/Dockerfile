# GET BASE RASPBIAN IMAGE
FROM resin/raspberrypi3-debian:jessie

# GET UPDATES
RUN apt-get update && sudo apt-get upgrade

# DOWNLOAD AND UNPACK MONGODB
RUN sudo apt-get install mongodb-server

# Define mountable directories.
VOLUME ["/data/db"]

# Define working directory.
WORKDIR /data

# Define default command.
CMD sudo mongod --journal 

# Expose ports.
#   - 27017: process
#   - 28017: http
EXPOSE 27017
EXPOSE 28017

