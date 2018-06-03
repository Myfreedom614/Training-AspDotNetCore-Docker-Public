FROM microsoft/aspnet:4.7-windowsservercore-ltsc2016
# FROM lab-repo.msdev.ms.com:5000/microsoft-aspnet
ARG source
WORKDIR /inetpub/wwwroot
COPY ${source:-obj/Docker/publish} .
