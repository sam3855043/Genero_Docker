docker cp 
podman cp 4075aa7d3f6a:/opt/fourjs/fglgws/etc/fgllicense /u1/genero/fgl/etc/fgllicense
docker cp 594d519783fb:/app/data.txt /home/user/data.txt


docker exec -u root -it 4075aa7d3f6a /bin/bash 
podman exec -u root -it 4075aa7d3f6a /bin/bash 

podman  build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-3.21.03-build202409101731-l64xl212.run \
     --build-arg UTL_TAR=utl.tar.gz \
     --build-arg FGLDIRETC=fgletc.tar.gz \
     --build-arg BASH_PROFILE=.bash_profile \
     -t redhat-fglgws-base .
 - clear resource
 - podman system prune


 - 
 - create container
 - podman run -it --name rhel-fglgws
 - podman run -d -it --replace --name rhel-fglgws redhat-fglgws-base
 - podman exec -it rhel-fglgws /bin/bash
