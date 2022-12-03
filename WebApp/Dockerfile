FROM mcr.microsoft.com/dotnet/sdk:6.0 as build
WORKDIR /src
ADD /WebApp ./WebApp
WORKDIR /src/WebApp
RUN dotnet publish "WebApp.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM mcr.microsoft.com/dotnet/aspnet:6.0 as prod
WORKDIR /app
COPY --from=build /app/publish /app
ENTRYPOINT [ "dotnet", "WebApp.dll" ]
EXPOSE 80