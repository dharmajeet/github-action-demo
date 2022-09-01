FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY Training.csproj .
RUN dotnet restore Training.csproj
COPY . .
RUN dotnet build Training.csproj -c Release -o /out
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /app
COPY --from=build /out ./
ENTRYPOINT ["dotnet", "Training.dll"]