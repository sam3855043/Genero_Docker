docker cp 
podman cp 4075aa7d3f6a:/opt/fourjs/fglgws/etc/fgllicense /u1/genero/fgl/etc/fgllicense
docker cp 594d519783fb:/app/data.txt /home/user/data.txt


docker exec -u root -it 4075aa7d3f6a /bin/bash 
podman exec -u root -it 4075aa7d3f6a /bin/bash 

podman  build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-3.21.03-build202409101731-l64xl212.run \
     --build-arg UTL_TAR=utl.tar.gz \
     -t fglgws-redhat-base .