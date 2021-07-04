Application Setting / Configuration

APPINSIGHTS_INSTRUMENTATIONKEY

```

```

URL Web App  
**smpapi[yourname]**

```

```

Exercise 2 Task 1

```
dotnet new webapi --output . --name SimpleApi --framework netcoreapp3.1
```



Otros

```

```

Exercise 3 Task 1,9

publish and prepare to deployment

```
dotnet publish -o ./Api --framework netcoreapp3.1

dir -s | ForEach-Object { & "C:\Program Files\7-Zip\7z.exe" a -tzip ("Apizip.zip") $_.Name }
```

```
az webapp deployment source config-zip --resource-group MonitoredAssets --src api.zip --name smpapi[yourname]
```
```

```
```
az webapp deployment source show --name smpapi[yourname] --resource-group MonitoredAssets
```

Browse

```
https://smpapi[yourname].azurewebsites.net/weatherforecast
```

