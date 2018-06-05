FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
RUN apt-get update && apt-get -y install openssh-server unzip
RUN mkdir /var/run/sshd && chmod 0755 /var/run/sshd 
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
RUN sed -i 's/#StrictModes yes/StrictModes no/g' /etc/ssh/sshd_config
RUN service ssh restart
RUN mkdir /root/.vs-debugger && chmod 0755 /root/.vs-debugger
RUN curl -sSL https://aka.ms/getvsdbgsh | bash /dev/stdin -v vs2017u1 -l /root/.vs-debugger/
EXPOSE 22 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY AspDotNetCore-WebApi/AspDotNetCore-WebApi.csproj AspDotNetCore-WebApi/
RUN dotnet restore AspDotNetCore-WebApi/AspDotNetCore-WebApi.csproj
COPY . .
WORKDIR /src/AspDotNetCore-WebApi
RUN dotnet build AspDotNetCore-WebApi.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish AspDotNetCore-WebApi.csproj -c Release -o /app
RUN echo 'service ssh restart' >> /app/start.sh
RUN echo 'echo -e "1qa@WS3ed\n1qa@WS3ed" | passwd root' >> /app/start.sh
RUN echo 'dotnet /app/AspDotNetCore-WebApi.dll' >> /app/start.sh
RUN chmod a+x /app/start.sh

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
RUN cp -r /app/* /root/
ENTRYPOINT ["bash", "start.sh"]