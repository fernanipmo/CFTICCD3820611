**Storage connection string**

**Access Keys\Connection string**

```
DefaultEndpointsProtocol=https;AccountName=securestorfpm;AccountKey=2e/S3UfORNPqze/WUHKRaHpKuIgOix/f4k5BWEayUAu5msSBihJGx6k4AGBf+YHtvDf2anHwaHBh/H5ZhUnT2w==;EndpointSuffix=core.windows.net
```

**securevault[yourname]\secrets\storagecredentials\Current version**

**Secret identifier**

```
https://securevaultfpm.vault.azure.net/secrets/storagecredentials/849e57f542be4c10b067633a64129920
```

```
@Microsoft.KeyVault(SecretUri=https://securevaultfpm.vault.azure.net/secrets/storagecredentials/849e57f542be4c10b067633a64129920)
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

**url records.json**

````URL records.json file
https://securestorfpm.blob.core.windows.net/drop/records.json
````

FileParser - [httpTrigger]
        Invoke url: https://securefuncfpm.azurewebsites.net/api/fileparser?code=HqhKueWtwopy3AToiNDKxWib4gUv02PjVPfY5uV9gHXtknhNzjGdag==



HTTP response code

200 OK

HTTP response content

[  {    "_id": "5c5318082390c97ac43be30d",    "index": 0,    "guid": "f7b104d1-cf92-4861-a187-dc25aa0cf79b",    "isActive": true,    "balance": "$3,940.15",    "picture": "http://placehold.it/32x32",    "age": 34,    "eyeColor": "brown",    "name": "Miles Fleming",    "gender": "male",    "company": "OPPORTECH",    "email": "milesfleming@opportech.com",    "phone": "+1 (846) 485-3207",    "address": "498 Lancaster Avenue, Fresno, District Of Columbia, 5580",    "about": "Aliqua irure cupidatat ea occaecat fugiat voluptate laboris ad nostrud. Consequat aliquip consequat amet do est deserunt ea. Voluptate adipisicing veniam pariatur eu commodo enim do sint eiusmod. Proident elit tempor cillum anim magna qui.\r\n",    "registered": "2014-07-02T05:21:22 +04:00",    "latitude": -75.703852,    "longitude": 101.595201,    "tags": [      "voluptate",      "officia",      "pariatur",      "enim",      "ex",      "ea",      "sit"    ],    "friends": [      {        "id": 0,        "name": "Walter Puckett"      },      {        "id": 1,        "name": "Karla Koch"      },      {        "id": 2,        "name": "Ingrid Mcknight"      }    ],    "greeting": "Hello, Miles Fleming! You have 9 unread messages.",    "favoriteFruit": "apple"  },  {    "_id": "5c5318082317918e5dac4e9f",    "index": 1,    "guid": "3067eb01-f176-4d0c-9033-2f761996a8b5",    "isActive": true,    "balance": "$2,623.90",    "picture": "http://placehold.it/32x32",    "age": 38,    "eyeColor": "green",    "name": "Howell Mcconnell",    "gender": "male",    "company": "INSURESYS",    "email": "howellmcconnell@insuresys.com",    "phone": "+1 (972) 515-2413",    "address": "794 Montague Street, Echo, Montana, 1080",    "about": "Nostrud eu Lorem nisi dolore tempor minim aliqua laboris labore cupidatat eu voluptate. Et fugiat incididunt laborum laborum est dolore sit. Quis eu Lorem duis duis in ad amet commodo commodo ex Lorem elit. Veniam et est eiusmod Lorem. Minim ullamco dolore labore dolore ipsum consectetur. Nisi do non quis deserunt veniam velit amet laboris elit aliquip ex. Occaecat ad sunt fugiat fugiat labore consectetur ut voluptate ipsum velit adipisicing officia tempor sunt.\r\n",    "registered": "2018-07-31T07:15:44 +04:00",    "latitude": 49.322514,    "longitude": -13.648224,    "tags": [      "ea",      "sint",      "velit",      "exercitation",      "proident",      "ad",      "anim"    ],    "friends": [      {        "id": 0,        "name": "Ida Rodgers"      },      {        "id": 1,        "name": "Rosemarie Cooley"      },      {        "id": 2,        "name": "Ward Brennan"      }    ],    "greeting": "Hello, Howell Mcconnell! You have 6 unread messages.",    "favoriteFruit": "strawberry"  },  {    "_id": "5c5318085c130b4ab508381c",    "index": 2,    "guid": "58a439a5-d05f-4878-bda2-7b9fd8138bf9",    "isActive": true,    "balance": "$2,239.32",    "picture": "http://placehold.it/32x32",    "age": 29,    "eyeColor": "blue",    "name": "Claudia Sharpe",    "gender": "female",    "company": "ZOLAREX",    "email": "claudiasharpe@zolarex.com",    "phone": "+1 (902) 558-3114",    "address": "471 Gain Court, Reinerton, Missouri, 9803",    "about": "Reprehenderit et excepteur cillum in deserunt id nulla Lorem consectetur anim in elit quis. Consectetur proident qui fugiat ea exercitation magna. Consectetur mollit incididunt commodo Lorem adipisicing amet aliqua adipisicing culpa labore esse cupidatat et cupidatat. Culpa elit quis eiusmod culpa nisi nulla incididunt et mollit proident officia sit cillum.\r\n",    "registered": "2015-09-12T03:47:10 +04:00",    "latitude": 24.369819,    "longitude": 71.950504,    "tags": [      "ea",      "duis",      "est",      "cillum",      "occaecat",      "veniam",      "voluptate"    ],    "friends": [      {        "id": 0,        "name": "Maxine Bird"      },      {        "id": 1,        "name": "Francis Burris"      },      {        "id": 2,        "name": "Brianna Battle"      }    ],    "greeting": "Hello, Claudia Sharpe! You have 8 unread messages.",    "favoriteFruit": "apple"  },  {    "_id": "5c531808aa73fd899160caa7",    "index": 3,    "guid": "6edc248d-7279-4a6c-a1a5-7c7244827418",    "isActive": false,    "balance": "$3,873.34",    "picture": "http://placehold.it/32x32",    "age": 27,    "eyeColor": "blue",    "name": "Barbra Mccray",    "gender": "female",    "company": "HINWAY",    "email": "barbramccray@hinway.com",    "phone": "+1 (982) 435-3641",    "address": "935 Kossuth Place, Dixonville, Georgia, 4237",    "about": "Commodo nulla culpa dolore non laboris qui anim sint. Et aliqua laboris mollit esse fugiat. Aliquip enim in incididunt aliqua consectetur in Lorem cupidatat.\r\n",    "registered": "2015-02-28T06:16:54 +05:00",    "latitude": 51.235573,    "longitude": 148.540869,    "tags": [      "quis",      "in",      "amet",      "tempor",      "non",      "veniam",      "voluptate"    ],    "friends": [      {        "id": 0,        "name": "Mendez Floyd"      },      {        "id": 1,        "name": "Pollard Dunn"      },      {        "id": 2,        "name": "Juliette Farmer"      }    ],    "greeting": "Hello, Barbra Mccray! You have 2 unread messages.",    "favoriteFruit": "strawberry"  },  {    "_id": "5c5318081a1f883604c2c22e",    "index": 4,    "guid": "38a5bd35-7f19-46f9-ad04-4e9679323f96",    "isActive": true,    "balance": "$1,773.82",    "picture": "http://placehold.it/32x32",    "age": 25,    "eyeColor": "blue",    "name": "Nora Espinoza",    "gender": "female",    "company": "WRAPTURE",    "email": "noraespinoza@wrapture.com",    "phone": "+1 (987) 406-3306",    "address": "454 Lloyd Street, Valmy, Palau, 2925",    "about": "Sint elit culpa mollit ipsum proident deserunt amet incididunt dolore. Lorem pariatur est fugiat ut qui elit exercitation dolor ipsum velit. Nulla nostrud excepteur nisi mollit sunt proident deserunt.\r\n",    "registered": "2017-12-17T02:40:21 +05:00",    "latitude": -66.559987,    "longitude": -149.268497,    "tags": [      "excepteur",      "quis",      "irure",      "magna",      "laborum",      "dolor",      "nostrud"    ],    "friends": [      {        "id": 0,        "name": "Rosie Horne"      },      {        "id": 1,        "name": "Dean Vega"      },      {        "id": 2,        "name": "Geraldine Mcdowell"      }    ],    "greeting": "Hello, Nora Espinoza! You have 5 unread messages.",    "favoriteFruit": "banana"  },  {    "_id": "5c5318080d9d1ab5f1820460",    "index": 5,    "guid": "2fa7f280-2bbf-4b3e-a9bc-30288f749b70",    "isActive": true,    "balance": "$3,967.32",    "picture": "http://placehold.it/32x32",    "age": 33,    "eyeColor": "green",    "name": "Allen Santos",    "gender": "male",    "company": "ZEPITOPE",    "email": "allensantos@zepitope.com",    "phone": "+1 (918) 507-3272",    "address": "252 Anna Court, Trona, Guam, 3638",    "about": "Amet nostrud aliquip laboris consequat. Commodo esse deserunt fugiat aliquip ipsum officia et. Labore culpa magna adipisicing non veniam dolor anim anim. Aliqua irure fugiat labore pariatur deserunt ea excepteur ipsum aliqua dolore officia. Tempor laborum sint magna culpa eu laborum dolore eu proident voluptate nostrud consequat sunt deserunt. Non aliqua duis laboris magna qui esse labore. Ullamco consequat aliqua dolore id.\r\n",    "registered": "2015-09-13T12:36:53 +04:00",    "latitude": 75.539327,    "longitude": -6.159221,    "tags": [      "duis",      "ea",      "ullamco",      "id",      "sunt",      "nostrud",      "magna"    ],    "friends": [      {        "id": 0,        "name": "Burt Barrett"      },      {        "id": 1,        "name": "Coleman Mcfarland"      },      {        "id": 2,        "name": "Mayo Rios"      }    ],    "greeting": "Hello, Allen Santos! You have 2 unread messages.",    "favoriteFruit": "banana"  },  {    "_id": "5c5318087fbd5b899cda4c02",    "index": 6,    "guid": "bf64b2d4-e1fb-4014-bdb4-f71a038665ae",    "isActive": false,    "balance": "$3,412.83",    "picture": "http://placehold.it/32x32",    "age": 35,    "eyeColor": "green",    "name": "Guy French",    "gender": "male",    "company": "MOTOVATE",    "email": "guyfrench@motovate.com",    "phone": "+1 (938) 570-3050",    "address": "724 Overbaugh Place, Beason, Marshall Islands, 6199",    "about": "Eiusmod velit incididunt laboris sit magna tempor voluptate voluptate aute eiusmod aliquip voluptate officia magna. Fugiat Lorem irure fugiat dolor et dolor. Exercitation nulla deserunt mollit enim officia consectetur.\r\n",    "registered": "2018-10-05T05:47:09 +04:00",    "latitude": 20.937031,    "longitude": 166.849989,    "tags": [      "dolor",      "mollit",      "proident",      "amet",      "magna",      "pariatur",      "aliqua"    ],    "friends": [      {        "id": 0,        "name": "Cooke Lee"      },      {        "id": 1,        "name": "Phillips Case"      },      {        "id": 2,        "name": "Juanita Sloan"      }    ],    "greeting": "Hello, Guy French! You have 6 unread messages.",    "favoriteFruit": "banana"  } ]

