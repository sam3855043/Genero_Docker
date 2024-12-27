docker pull debian:latest
docker build --force-rm -t fglgws-os .


e84d1e2ec659
docker pull debian:latest
docker build --force-rm -t fglgws-os .
podman build --force-rm -t fglgws-os .
docker build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-5.00.02-build202405231030-l64xl228.run \
     --build-arg UTL_TAR=utl.tar.gz
     -t fglgws-base .

podman  build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-3.21.03-build202409101731-l64xl212.run \
     --build-arg UTL_TAR=utl.tar.gz \
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


podman build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-3.21.03-build202409101731-l64xl212.run \ 
     -t fglgws-base .
podman run -d -it --name fglgws fglgws-base 


podman exec  -u root -it 47f0ef8f47a9 /bin/bash

podman cp 47f0ef8f47a9:/opt/fourjs/fglgws/etc/fgllicense /u1/genero/fgl/etc/fgllicense.run
podman cp /u1/etc/ 47f0ef8f47a9:/u1/etc/ 
