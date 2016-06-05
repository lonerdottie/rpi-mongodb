#FROM resin/rpi-raspbian:jessie
FROM resin/raspberrypi3-buildpack-deps

RUN sudo apt-get update && sudo apt-get upgrade

RUN sudo apt-get install wget

RUN wget http://andyfelong.com/downloads/core_mongodb.tar.gz &&  tar -zxvf core_mongodb.tar.gz
RUN wget http://andyfelong.com/downloads/tools_mongodb.tar.gz && tar -zxvf tools_mongodb.tar.gz

RUN sudo adduser --ingroup nogroup --shell /etc/false --disabled-password --gecos "" \
--no-create-home mongodb

RUN sudo chown root:root mongo* && sudo chmod 755 mongo* && sudo cp -p mongo* /usr/bin

RUN sudo mkdir /var/log/mongodb && sudo chown mongodb:nogroup /var/log/mongodb

RUN sudo mkdir /var/lib/mongodb && sudo chown mongodb:root /var/lib/mongodb && sudo chmod 775 /var/lib/mongodb

#RUN sudo apt-get install apt-utils

#RUN sudo apt-get install libasan0 libatomic1 libboost-atomic1.55.0 libboost-dev libboost-filesystem1.55.0 libboost-program-options1.55.0 libboost-system1.55.0 libboost-thread1.55.0 libboost1.55-dev libc-dev-bin libc6-dev libgcc-4.8-dev libgomp1 libpcap0.8 libpcrecpp0 libsnappy1 libssl1.0.0 libstdc++-4.8-dev libv8-3.14.5 linux-libc-dev

#RUN sudo rm *_mongodb.tar.gz

RUN echo 'bind_ip = 127.0.0.1\nquiet = true\ndbpath = /var/lib/mongodb\nlogpath = /var/log/mongodb/mongod.log\nlogappend = true\nstorageEngine = mmapv1' >> /etc/mongodb.conf

EXPOSE 27017

#VOLUME /var/lib/mongodb

#USER mongodb

WORKDIR /var/lib/mongodb

#ENTRYPOINT ["/usr/bin/mongod", "--journal", "--config", "/etc/mongodb.conf"]

CMD sudo /usr/bin/mongod --journal --quiet --config /etc/mongodb.conf
