FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# trigger a deployment
# trigger another deployment
# pay attention this time
# using the login action
# using the correct syntax (we hope)
# what's my secret?
# pleeaaase work!
# gettin tired now...
# no, really, pay attention
# Fix the YAML
# one brace for built-in variables
# tagging
# literal tag
# no curlies
# First prayer, Az web app deploy
# Modify slot-name
# try and try again
# check staging slot health


# copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
COPY ./appsettings.*.json /app/out/
COPY ./appsettings.json /app/out/

# build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app

ENV SQL_USER="YourUserName" \
SQL_PASSWORD="changeme" \
SQL_SERVER="changeme.database.windows.net" \
SQL_DBNAME="mydrivingDB" \
WEB_PORT="8080" \
WEB_SERVER_BASE_URI="http://0.0.0.0" \
ASPNETCORE_ENVIRONMENT="Production"

COPY --from=build-env /app/out .

EXPOSE 8080

ENTRYPOINT ["dotnet", "poi.dll"]

