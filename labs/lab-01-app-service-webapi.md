# Lab-01: App Service con .NET 8 Minimal API

Objetivo: Desplegar una Web API en Azure App Service con variables de entorno y slot de staging.

Prerequisitos:
- .NET 8 SDK, Azure CLI (az), cuenta Azure
- Git instalado

Pasos:
1. Crear API mínima
   ```bash
   dotnet new webapi -n Contoso.Api
   cd Contoso.Api
   ```
   Edita Program.cs para exponer un endpoint `/healthz` que devuelva 200.

2. Ejecutar local y probar
   ```bash
   dotnet run
   curl http://localhost:5205/healthz
   ```

3. Crear recursos en Azure
   ```bash
   az group create -n rg-az204-labs -l eastus
   az appservice plan create -n asp-az204 --resource-group rg-az204-labs --sku B1 --is-linux
   az webapp create -g rg-az204-labs -p asp-az204 -n contoso-api-$RANDOM --runtime "DOTNET|8.0"
   export WEBAPP_NAME=$(az webapp list -g rg-az204-labs --query "[0].name" -o tsv)
   ```

4. Configurar settings y connection strings (ejemplo)
   ```bash
   az webapp config appsettings set -g rg-az204-labs -n $WEBAPP_NAME --settings ASPNETCORE_ENVIRONMENT=Production FEATURE_FLAG_X=true
   ```

5. Habilitar logging
   ```bash
   az webapp log config -g rg-az204-labs -n $WEBAPP_NAME --application-logging filesystem --level Information
   ```

6. Desplegar con Zip Deploy
   ```bash
   dotnet publish -c Release -o publish
   cd publish
   zip -r app.zip .
   az webapp deployment source config-zip -g rg-az204-labs -n $WEBAPP_NAME --src app.zip
   ```

7. Crear slot de staging y hacer swap
   ```bash
   az webapp deployment slot create -g rg-az204-labs -n $WEBAPP_NAME --slot staging
   az webapp deployment source config-zip -g rg-az204-labs -n $WEBAPP_NAME --slot staging --src app.zip
   az webapp deployment slot swap -g rg-az204-labs -n $WEBAPP_NAME --slot staging
   ```

8. Probar
   ```bash
   echo "https://$WEBAPP_NAME.azurewebsites.net/healthz"
   ```

Criterios de aceptación:
- Endpoint /healthz operativo
- Variables de entorno aplicadas
- Slot staging creado y swap realizado

Limpieza:
```bash
az group delete -n rg-az204-labs -y
```