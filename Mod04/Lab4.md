**COSMOSDB**

**Resource group**

PolyglotData

**SQL Server**

polysqlsrvrfpm

**Azure Cosmos DB Account**

polycosmosfpm

**Storage Account**

polystorfpm

**Container**

images

URL

https://polystorfpm.blob.core.windows.net/images

**New container**

databases

**Database name**

AdventureWorks

**Server admin login**

user: testuser

password: TestPa55w.rd

**App Service**

polywebfpm

**SQL database instance name (connection string)**

AdventureWorksSqlContex

**Cosmos database instance name (connection string)**

AdventureWorksCosmosContext

**Blob container name (application setting)**

Blobcontainerurl



**PRIMARY CONNECTION STRING** 

```
AccountEndpoint=https://polycosmosfpm.documents.azure.com:443/;AccountKey=yRUBeSv9SGV445kfK30bmNtsaLlXYLzBzpj8tKYxsAvqkm7mo1dxU5RkZgDNsjlZLBCScprC4G43QoNNwTGggg==;
```



Home\ **polysqlsrvr\[yourname]\AdventureWorks**

**ADO.NET (SQL authentication)**

```
Server=tcp:polysqlsrvrfpm.database.windows.net,1433;Initial Catalog=AdventureWorks;Persist Security Info=False;User ID=testuser;Password=TestPa55w.rd;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
```

**Blob container images URL**

```
https://polystorfpm.blob.core.windows.net/images
```
**Migrate projects**

```
dotnet new console --name AdventureWorks.Migrate --framework netcoreapp3.1
```

User and password:

```
In the Login text box, enter testuser.

In the Password text box, enter TestPa55w.rd.
```

dotnet new console --name AdventureWorks.Migrate --framework netcoreapp3.1

**Deploy to Azure App Services:**

dotnet publish -o web 

**Publish zip file**

 az webapp deployment source config-zip --resource-group Polyglotdata --src web.zip --name polywebfpm

**Create a new .NET console project:**

dotnet new console --name AdventureWorks.Migrate

dotnet new console --name AdventureWorks.Migrate --framework netcoreapp3.1

References:

dotnet add .\AdventureWorks.Migrate\AdventureWorks.Migrate.csproj reference .\AdventureWorks.Models\AdventureWorks.Models.csproj

dotnet add .\AdventureWorks.Migrate\AdventureWorks.Migrate.csproj reference .\AdventureWorks.Context\AdventureWorks.Context.csproj

Add Entity Framework:

dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 3.0.1



**Cosmos DB Queries**

SELECT * FROM models

SELECT VALUE COUNT(1) FROM models

**Import **Microsoft.Azure.Cosmos from NuGet:**

dotnet add package Microsoft.Azure.Cosmos --version 3.4.1



**New file in VS Code**

**AdventureWorksCosmosContext.cs**

polycosmosfpm

"id": "0481d7e1-4970-4efa-a560-020f6579918d"

**Architecture**

