#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app

COPY *.csproj .
RUN dotnet restore

COPY . ./

RUN dotnet publish  --no-restore  -c Release -o out

FROM  mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "DockeWeb.dll"]



#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
#WORKDIR /app
#EXPOSE 80
#
#FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
#WORKDIR /src
#COPY ["DockeWeb/DockeWeb.csproj", "DockeWeb/"]
#RUN dotnet restore "DockeWeb/DockeWeb.csproj"
#COPY . .
#WORKDIR "/src/DockeWeb"
#RUN dotnet build "DockeWeb.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DockeWeb.csproj" -c Release -o /app/publish
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DockeWeb.dll"]