FROM ubuntu:xenial 

LABEL ravendb-version="40013-alpha"
LABEL operating-system="ubuntu"

ENV RAVEN_Port 8080
ENV RAVEN_ServerUrl "http://0.0.0.0:8080"
ENV RAVEN_DataDir /var/lib/ravendb/
ENV RAVEN_EverybodyAsAdmin true

# Update container
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
	&& apt-get install bzip2 -y \
	&& apt-get install apt-transport-https -y

# Install .NET Core
RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
    && apt-get update \
    && apt-get install dotnet-dev-1.0.1 -y

# RavenDB	
EXPOSE ${RAVEN_Port}
VOLUME ${RAVEN_DataDir}

# Extract RavenDB files
ADD http://hibernatingrhinos.com/downloads/ravendb%20for%20ubuntu%2016.04%20x64/40013-alpha /home/Raven.tar.bz2
RUN cd /home \
    && mkdir Raven \
    && tar xf Raven.tar.bz2 -C Raven \
    && rm /home/Raven.tar.bz2

# Run
WORKDIR /home/Raven/Server
CMD ./Raven.Server Raven/DataDir=${RAVEN_DataDir} Raven/ServerUrl=${RAVEN_ServerUrl} Raven/AllowEverybodyToAccessTheServerAsAdmin=${RAVEN_EverybodyAsAdmin}