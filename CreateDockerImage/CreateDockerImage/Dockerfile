FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
MAINTAINER Emrah AKIN <emrahakin@emrakin.com>
WORKDIR /app

COPY . ./
RUN dotnet restore "CreateDockerImage.csproj"

COPY . ./
RUN dotnet publish "CreateDockerImage.csproj" -c Release -o published 

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app/published .
ENTRYPOINT ["dotnet", "CreateDockerImage.dll"]