FROM fglgws-redhat8-os

# 使用 root 權限進行初始設定
USER root

# Install necessary packages
RUN yum -y update && \
    yum -y install \
    file \ 
    git \
    bzip2 && \
    yum clean all


# 定義參數
ARG user=genero
ARG group=fourjs
ARG FGLGWS_PACKAGE
ARG FGLDIRETC
ARG UTL_TAR
ARG U1ETC
ARG BASH_PROFILE

# 建立使用者和群組
RUN groupadd -r ${group} || true && \
    useradd -r -g ${group} ${user}




# 設定工作目錄和環境變數
WORKDIR ${HOME}
ENV ZONE topprd
COPY ${FGLGWS_PACKAGE} /tmp/fglgws-install.run
# 建立目錄並設定權限
RUN mkdir -p /opt/fourjs && \
    chown ${user}:${group} /opt/fourjs /tmp/fglgws-install.run

# 切換為指定的使用者
USER ${user}

# 安裝 fglgws 套件
# Install fglgws package
ENV FGLDIR /opt/fourjs/fglgws
ENV PATH ${FGLDIR}/bin:${PATH}

RUN ls -l /tmp/fglgws-install.run
RUN chmod +x /tmp/fglgws-install.run
RUN sh /tmp/fglgws-install.run --accept --install --quiet --target ${FGLDIR} 
RUN fglrun -V


# utl 上包
WORKDIR /
#COPY ${UTL} /
USER root
#RUN ls -la /
#RUN tar zxvf /utl.tar.gz

#fgllicense 設定

#COPY ${FGLDIRETC} /opt/fourjs/fglgws/fgletc.tar.gz
WORKDIR /opt/fourjs/fglgws
COPY ${FGLDIRETC} /opt/fourjs/fglgws
RUN ls /opt/fourjs/fglgws
RUN tar zxvf fgletc.tar.gz
RUN ls /opt/fourjs/fglgws/etc

#T100 profile enviorment
WORKDIR /
COPY ${U1ETC} /
RUN tar zxvf u1etc.tar.gz
RUN ls /u1/etc

WORKDIR /opt/fourjs
RUN git clone https://github.com/sam3855043/MogDB_oci_testing.git
RUN ls /opt/fourjs

COPY ${BASH_PROFILE} /opt/fourjs
RUN . /opt/fourjs/.bash_profile
RUN ls -la /opt/fourjs
CMD ["/bin/bash"]

