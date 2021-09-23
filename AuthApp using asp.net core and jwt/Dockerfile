#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["AuthApp using asp.net core and jwt/AuthApp using asp.net core and jwt.csproj", "AuthApp using asp.net core and jwt/"]
RUN dotnet restore "AuthApp using asp.net core and jwt/AuthApp using asp.net core and jwt.csproj"
COPY . .
WORKDIR "/src/AuthApp using asp.net core and jwt"
RUN dotnet build "AuthApp using asp.net core and jwt.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "AuthApp using asp.net core and jwt.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "AuthApp using asp.net core and jwt.dll"]