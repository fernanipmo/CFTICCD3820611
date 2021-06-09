**Web App URL**

**eventviewer\[yourname]**

```bash
eventviewer[yourname].azurewebsites.net
```



**Event Grid Topic**

hrtopic\[yourname]\

```
https://hrtopic[yourname].<YOUR LOCATION>.eventgrid.azure.net/api/events
```

**Access Key 1**

```

```



**Exercise 3**

```
dotnet new console --name EventPublisher --output . --framework netcoreapp3.1
```

 ```
az eventgrid event-subscription create \
--source-resource-id "/subscriptions/$subId/resourceGroups/PubSubEvents/providers/Microsoft.EventGrid/topics/$myTopicName" \
--name basicsub \
--endpoint $endpoint
 ```

