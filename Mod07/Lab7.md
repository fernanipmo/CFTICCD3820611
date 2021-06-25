**Storage connection string**

**Access Keys\Connection string**

```
DefaultEndpointsProtocol=https;AccountName=securestorfpm;AccountKey=2e/S3UfORNPqze/WUHKRaHpKuIgOix/f4k5BWEayUAu5msSBihJGx6k4AGBf+YHtvDf2anHwaHBh/H5ZhUnT2w==;EndpointSuffix=core.windows.net
```

**securevault[yourname]\secrets\storagecredentials\Current version**

**Secret identifier**

```
DefaultEndpointsProtocol=https;AccountName=securestorfpm;AccountKey=2e/S3UfORNPqze/WUHKRaHpKuIgOix/f4k5BWEayUAu5msSBihJGx6k4AGBf+YHtvDf2anHwaHBh/H5ZhUnT2w==;EndpointSuffix=core.windows.net
```

```
@Microsoft.KeyVault(SecretUri=DefaultEndpointsProtocol=https;AccountName=securestorfpm;AccountKey=2e/S3UfORNPqze/WUHKRaHpKuIgOix/f4k5BWEayUAu5msSBihJGx6k4AGBf+YHtvDf2anHwaHBh/H5ZhUnT2w==;EndpointSuffix=core.windows.net)
```

> 

**securefunc[yourname]\Settings\Configuration**

**New application setting**

**StorageConnectionString**

```
@Microsoft.KeyVault(SecretUri=Secret Identifier)
```

```

```



Editing the FileParser file:

```csharp
using Azure.Storage.Blobs;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.AspNetCore.Http;
using System;
using System.Threading.Tasks;

public static class FileParser
{
    [FunctionName("FileParser")]
    public static async Task<IActionResult> Run(
        [HttpTrigger("GET")] HttpRequest request)
    {
        string connectionString = Environment.GetEnvironmentVariable("StorageConnectionString");
        BlobClient blob = new BlobClient(connectionString, "drop", "records.json");
        var response = await blob.DownloadAsync();
        return new FileStreamResult(response?.Value?.Content, response?.Value?.ContentType);
    }
}
```