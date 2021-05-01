#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["WebApplication1/Server/WebApplication1.Server.csproj", "WebApplication1/Server/"]
COPY ["WebApplication1/Shared/WebApplication1.Shared.csproj", "WebApplication1/Shared/"]
COPY ["WebApplication1/Client/WebApplication1.Client.csproj", "WebApplication1/Client/"]
RUN dotnet restore "WebApplication1/Server/WebApplication1.Server.csproj"
COPY . .
WORKDIR "/src/WebApplication1/Server"
RUN dotnet build "WebApplication1.Server.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication1.Server.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication1.Server.dll"]