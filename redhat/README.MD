56c43cbf8701

 - podman build --force-rm -t fglgws-redhat8-os .


podman  build --force-rm \
     --build-arg FGLGWS_PACKAGE=fjs-fglgws-3.21.03-build202409101731-l64xl212.run \
     --build-arg UTL_TAR=utl.tar.gz \
     -t fglgws-base .

podman exec -d -u 0 -it 47f0ef8f47a9 /bin/bash 

podman run -it --name oracle-listener-container -p 1521:1521 rhel-oracle-listener
podman exec -it oracle-client /bin/bash
podman exec -it oracle-client-container /bin/bash
lsnrctl status

podman logs oracle-client-container