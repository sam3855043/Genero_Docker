FROM debian:latest
RUN apt-get update \
  && apt-get install -y --no-install-recommends --no-install-suggests \
       file \
       bzip2 \
       libncursesw5 \
       binutils \
       sqlite3 \
       sudo \
       libncurses5 \
   && apt-get clean \
   && rm -rf /var/lib/apt/lists/*

   ARG user=genero
   ARG group=fourjs
   ARG uid=2000 
   ARG gid=2000

   ENV HOME=/home/${user}

RUN set -eufx \
  && groupadd -g "${gid}" "${group}" \
  && useradd -d "${HOME}" -u "${uid}" -g "${gid}" -M -N -r -s /bin/bash "${user}" \
  && mkdir -p "${HOME}" 
  #&& chown "${user}:${group}" "${HOME}" \
RUN ls -la /home
RUN chown genero:fourjs /home/genero
RUN ls -la /home
 WORKDIR ${HOME}
 USER ${user}