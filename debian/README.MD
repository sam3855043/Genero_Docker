docker pull debian:latest
docker build --force-rm -t fglgws-os .


e84d1e2ec659
docker pull debian:latest
docker build --force-rm -t fglgws-os .
docker build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-5.00.02-build202405231030-l64xl228.run \
     -t fglgws-base .
docker cp /u1/genero/fgl/etc/fgllicense e4e63509c169:/opt/fourjs/fglgws/etc/fgllicense
docker run -d --name myCon d fglgws-base
bc094f8d311100c7c7882fa649c85873ac0db87a8f13f721f3cb51470214809c

docker run -it --replace --name fglgws fglgws-base
docker run -it --replace --name fglgws fglgws-base
docker run -p 10.40.40.60:6800:6800 -itd --replace --name fglgws fglgws-base
netstat -ntlp

docker exec -u root -it my-container
docker exec -u root -it my-container /bin/bash


sudo apt install net-tools