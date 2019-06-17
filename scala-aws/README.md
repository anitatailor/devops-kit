docker build -t rivigods/scala-sbt:scala-2.11_sbt-1.3 .
docker images
docker docker login --username $DOCKER_USERNAME --password $DOCKER_PASSWORD
#docker login --username $DOCKER_USERNAME --password $DOCKER_PASSWORD
docker login --username atailor22
docker push rivigods/scala-sbt
