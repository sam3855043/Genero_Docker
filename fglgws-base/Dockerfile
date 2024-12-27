FROM fglgws-os
USER root

ARG user=genero
ARG group=fourjs
ARG FGLGWS_PACKAGE
ARG TOPENV

WORKDIR ${HOME}
ENV ZONE topprd


COPY ${FGLGWS_PACKAGE} /tmp/fglgws-install.run
COPY ${UTL} /

RUN mkdir -p /opt/fourjs \
  && chown ${user}:${group} /opt/fourjs /tmp/fglgws-install.run
USER ${user}

# Install fglgws package
ENV FGLDIR /opt/fourjs/fglgws
ENV PATH ${FGLDIR}/bin:${PATH}
RUN /tmp/fglgws-install.run --accept --install --quiet --target ${FGLDIR} 
RUN fglrun -V
#RUN tar zxvf /utl.tar.gz

