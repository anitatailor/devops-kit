# Pull base image
FROM  openjdk:8u151

ENV SCALA_VERSION 2.11.12
ENV SBT_VERSION  1.2.8
# Scala expects this file
RUN touch /usr/lib/jvm/java-8-openjdk-amd64/release

# Install Scala
RUN \
  curl -fsL http://downloads.typesafe.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz | tar xfz - -C /root/ && \
  echo >> /root/.bashrc && \
  echo 'export PATH=~/scala-$SCALA_VERSION/bin:$PATH' >> /root/.bashrc

# Install sbt
RUN \
  curl -L -o sbt-$SBT_VERSION.deb http://dl.bintray.com/sbt/debian/sbt-$SBT_VERSION.deb && \
  dpkg -i sbt-$SBT_VERSION.deb && \
  rm sbt-$SBT_VERSION.deb && \
  apt-get update && \
  apt-get install sbt && \
  sbt sbtVersion 

# Install aws cli
RUN apt-get update && \  
    apt-get install -yq --no-install-recommends \
      awscli \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Define working directory
WORKDIR /root
