# �tape de build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copier uniquement le projet API
COPY . .

# Restaurer les d�pendances et publier
RUN dotnet restore "PizzaStoreAPI.csproj"
RUN dotnet publish "PizzaStoreAPI.csproj" -c Release -o /out

# �tape de runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /out .

# Entr�e de l'application
ENTRYPOINT ["dotnet", "PizzaStoreAPI.dll"]
