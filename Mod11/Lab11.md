**Access Key/Connection String**

**asyncstor[yourname]**

**asyncstorfpm**

**URL smpapifpm**

````
https://smpapifpm.azurewebsites.net/weatherforecast
````



```bash
http://smpapifpm.azurewebsites.net/
```

**Exercise 1**

```
dotnet new console --name MessageProcessor --output . --framework netcoreapp3.1
```

**Instrumentation Key**

````
7b496302-0c7b-4489-bb13-48f54936c098
````

az webapp list --resource-group MonitoredAssets

az webapp list --resource-group MonitoredAssets --output table

az webapp list --resource-group MonitoredAssets --query "[?starts_with(name, 'smpapi')]"

az webapp list --resource-group MonitoredAssets --query "[?starts_with(name, 'smpapi')].{Name:name}" --output tsv



**Publicar el proyecto**

````
dotnet publish -o api
````



**Deploying the api.zip file to the web app**

````
az webapp deployment source config-zip --resource-group MonitoredAssets --src api.zip --name smpapifpm
````

