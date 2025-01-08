# Using Red Hat base image
FROM registry.access.redhat.com/ubi8/ubi:latest

# Environment Variables
ENV ORACLE_BASE=/opt/oracle
ENV ORACLE_HOME=$ORACLE_BASE/instantclient_21_1
ENV LD_LIBRARY_PATH=$ORACLE_HOME
ENV PATH=$PATH:$ORACLE_HOME

# Install necessary packages
RUN yum -y update && \
    yum -y install \
    vi \
    ncurses \
    ncurses-libs \
    ncurses-compat-libs \
    libaio \
    bzip2 \
    file \
    binutils \
    sqlite \
    sudo \
    wget \
    unzip \
    tar \
    gzip && \
    yum clean all

# Create Oracle directories
RUN mkdir -p $ORACLE_HOME/network/admin

# Install Oracle Instant Client
WORKDIR $ORACLE_BASE
RUN wget https://download.oracle.com/otn_software/linux/instantclient/211000/instantclient-basic-linux.x64-21.1.0.0.0.zip && \
    wget https://download.oracle.com/otn_software/linux/instantclient/211000/instantclient-sqlplus-linux.x64-21.1.0.0.0.zip && \
    wget https://download.oracle.com/otn_software/linux/instantclient/211000/instantclient-tools-linux.x64-21.1.0.0.0.zip && \
    unzip instantclient-basic-linux.x64-21.1.0.0.0.zip -d $ORACLE_BASE && \
    unzip instantclient-sqlplus-linux.x64-21.1.0.0.0.zip -d $ORACLE_BASE && \
    unzip instantclient-tools-linux.x64-21.1.0.0.0.zip -d $ORACLE_BASE && \
    rm -f instantclient-basic-linux.x64-21.1.0.0.0.zip instantclient-sqlplus-linux.x64-21.1.0.0.0.zip instantclient-tools-linux.x64-21.1.0.0.0.zip

# Create symbolic links
RUN if [ -e $ORACLE_HOME/libclntsh.so ]; then rm $ORACLE_HOME/libclntsh.so; fi && \
    if [ -e $ORACLE_HOME/libocci.so ]; then rm $ORACLE_HOME/libocci.so; fi && \
    ln -s $ORACLE_HOME/libclntsh.so.21.1 $ORACLE_HOME/libclntsh.so && \
    ln -s $ORACLE_HOME/libocci.so.21.1 $ORACLE_HOME/libocci.so

# Add Oracle Instant Client to system library path
RUN echo "$ORACLE_HOME" >> /etc/ld.so.conf.d/oracle-instantclient.conf && \
    ldconfig

# Configure Listener with specific IP
# 設定 tnsnames.ora
RUN mkdir -p $ORACLE_HOME/network/admin && \
    echo "TOPPRD = \
    (DESCRIPTION = \
        (ADDRESS = (PROTOCOL = TCP)(HOST = 10.40.40.207)(PORT = 1521)) \
        (CONNECT_DATA = \
            (SERVER = DEDICATED) \
            (SERVICE_NAME = TOPPRD) \
        ) \
    )" > $ORACLE_HOME/network/admin/tnsnames.ora
# 驗證 SQL*Plus
#CMD ["sqlplus", "-v"]

CMD ["/bin/bash"]
