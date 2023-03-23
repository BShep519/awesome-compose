
FROM mcr.microsoft.com/dotnet/aspnet:5.0 as base
WORKDIR /app
RUN echo 'base finished'

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
COPY . /src
WORKDIR /src
RUN ls
RUN dotnet build "aspnetapp.csproj" -c Release -o /app/build
RUN echo 'build finished'

FROM build AS publish
RUN dotnet publish "aspnetapp.csproj" -c Release -o /app/publish
RUN echo 'publish finished'

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
