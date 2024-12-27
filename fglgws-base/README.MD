docker cp 
podman cp 4075aa7d3f6a:/opt/fourjs/fglgws/etc/fgllicense /u1/genero/fgl/etc/fgllicense
docker cp 594d519783fb:/app/data.txt /home/user/data.txt


docker exec -u root -it 4075aa7d3f6a /bin/bash 
podman exec -u root -it 4075aa7d3f6a /bin/bash 

