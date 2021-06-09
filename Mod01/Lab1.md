**Connection String:**

```
DefaultEndpointsProtocol=https;AccountName=imgstorfpm;AccountKey=M1iP1j9LY6WYZOZWrjSfk93kexOEIyrsedp7LAAGehXDqYIX25kQUy0M52oaoZS6OZim48OKPjzTrH5pGIej/Q==;EndpointSuffix=core.windows.net
```

**URL WEB API:**

```
https://imgapifpm.azurewebsites.net
```



 az webapp deployment source config-zip --resource-group ManagedPlatform --src api.zip --name imgapifpm

imgwebfpm

az webapp deployment source config-zip --resource-group ManagedPlatform --src web.zip --name imgwebfpm
