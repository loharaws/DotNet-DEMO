# Build Stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /build

COPY . .

RUN dotnet restore src/dotnet-demoapp.csproj

RUN dotnet publish dotnet-demoapp.csproj -c Release -o /app/publish


# Runtime Stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 5000

ENTRYPOINT ["dotnet", "dotnet-demoapp.dll"]
