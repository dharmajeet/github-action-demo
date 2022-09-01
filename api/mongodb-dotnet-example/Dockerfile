FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY mongodb-dotnet-example.csproj .
RUN dotnet restore mongodb-dotnet-example.csproj
COPY . .
RUN dotnet build mongodb-dotnet-example.csproj -c Release -o /out
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /app
COPY --from=build /out ./

ARG ENVIRONMENT
ARG LOG_LEVEL
ENV ASPNETCORE_ENVIRONMENT=$ENVIRONMENT
ENV Logging__Loglevel__Default=$LOG_LEVEL
ENV Logging__Loglevel__Microsoft.AspNetCore=$LOG_LEVEL

ENTRYPOINT ["dotnet", "mongodb-dotnet-example.dll"]

#  a. docker build -t mongodb-dotnet-example:0.1.0 .
# 	b. docker create -p 8080:80 -e ASPNETCORE_ENVIRONMENT=Development -e Logging__Loglevel__Default=Debug  -e Logging__Loglevel__Microsoft.AspNetCore=Debug --name mongodb-dotnet-example mongodb-dotnet-example
# 	c. docker start  mongodb-dotnet-example
# 	d. docker logs mongodb-dotnet-example
# 	e. Open http://localhost:8080/swagger/index.html in browser