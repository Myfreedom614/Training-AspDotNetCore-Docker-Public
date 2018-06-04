FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY AspDotNetCore-WebApi/AspDotNetCore-WebApi.csproj AspDotNetCore-WebApi/
RUN dotnet restore AspDotNetCore-WebApi/AspDotNetCore-WebApi.csproj
COPY . .
WORKDIR /src/AspDotNetCore-WebApi
RUN dotnet build AspDotNetCore-WebApi.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish AspDotNetCore-WebApi.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "AspDotNetCore-WebApi.dll"]
