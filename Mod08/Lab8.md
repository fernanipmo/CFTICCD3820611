**Web App URL**

```
httpapi[yourname].azurewebsites.net
```

```
http://httpapifpm.azurewebsites.net/
```



Exercise 2:

Set Headers policy to All Operations (azure-api-mgmt) "Inbound processing"

**Only** in Echo Headers is Backend tile: Service URL Override **http://httpapi\[yourname]\.azurewebsites.net/headers**



```
HTTP/1.1 200 OK
cache-control: private
content-encoding: gzip
content-type: application/json
date: Sat, 26 Jun 2021 22:33:04 GMT
ocp-apim-apiid: httpbin-api
ocp-apim-operationid: echo-headers
ocp-apim-subscriptionid: master
ocp-apim-trace-location: https://apimstv3qbxr4vdkijuz7ryl.blob.core.windows.net/apimst4i5crna3vvpgdnkkbs-inspector/1MaLAFkuG6bFQvUKPbJ1Cw2-1?sv=2018-03-28&sr=c&sig=Xj3lHguN%2B6CXtMxLGnwIQdkT0JskNKTLLb0sqwTpZ%2Bc%3D&se=2022-06-26T21%3A44%3A24Z&sp=racwdl&traceId=2986943f18f947aab7d741cb4ee9ac76
transfer-encoding: chunked
vary: Accept-Encoding,Origin
    {
    "headers": {
        "Accept": "*/*",
        "Accept-Encoding": "gzip,deflate,br",
        "Accept-Language": "en-GB,en;q=0.9",
        "Cache-Control": "no-cache, no-store",
        "Client-Ip": "20.74.34.150:1344",
        "Connection": "Keep-Alive",
        "Content-Type": "text/plain;charset=UTF-8",
        "Disguised-Host": "httpapifpm.azurewebsites.net",
        "Host": "httpapifpm.azurewebsites.net",
        "Max-Forwards": "8",
        "Ocp-Apim-Subscription-Key": "bbebe003b3954f8f8b6afa82642ef6c3",
        "Referer": "https://apimanagement.hosting.portal.azure.net/",
        "Sec-Ch-Ua": "\" Not;A Brand\";v=\"99\",\"Microsoft Edge\";v=\"91\",\"Chromium\";v=\"91\"",
        "Sec-Ch-Ua-Mobile": "?0",
        "Sec-Fetch-Dest": "empty",
        "Sec-Fetch-Mode": "cors",
        "Sec-Fetch-Site": "cross-site",
        "Source": "azure-api-mgmt",
        "Was-Default-Hostname": "httpapifpm.azurewebsites.net",
        "X-Arr-Log-Id": "2986943f-18f9-47aa-b7d7-41cb4ee9ac76",
        "X-Client-Ip": "20.74.34.150",
        "X-Client-Port": "1344",
        "X-Forwarded-Tlsversion": "1.2",
        "X-Original-Url": "/headers",
        "X-Site-Deployment-Id": "httpapifpm",
        "X-Waws-Unencoded-Url": "/headers"
    }
}
```



Send

Bypass CORS proxy



```
HTTP/1.1 200 OK
cache-control: private
content-length: 522
content-type: application/xml
date: Sat, 26 Jun 2021 22:47:52 GMT
ocp-apim-apiid: httpbin-api
ocp-apim-operationid: get-legacy-data
ocp-apim-subscriptionid: master
ocp-apim-trace-location: https://apimstv3qbxr4vdkijuz7ryl.blob.core.windows.net/apimst4i5crna3vvpgdnkkbs-inspector/1MaLAFkuG6bFQvUKPbJ1Cw2-2?sv=2018-03-28&sr=c&sig=Xj3lHguN%2B6CXtMxLGnwIQdkT0JskNKTLLb0sqwTpZ%2Bc%3D&se=2022-06-26T21%3A44%3A24Z&sp=racwdl&traceId=e5f63d07cbf84d77af2f75a20a9b79f6
vary: Origin
    <?xml version='1.0' encoding='us-ascii'?>

<!--  A SAMPLE set of slides  -->

<slideshow 
    title="Sample Slide Show"
    date="Date of publication"
    author="Yours Truly"
    >

    <!-- TITLE SLIDE -->
    <slide type="all">
      <title>Wake up to WonderWidgets!</title>
    </slide>

    <!-- OVERVIEW -->
    <slide type="all">
        <title>Overview</title>
        <item>Why <em>WonderWidgets</em> are great</item>
        <item/>
        <item>Who <em>buys</em> WonderWidgets</item>
    </slide>

</slideshow>
```



```
HTTP/1.1 200 OK
cache-control: private
content-encoding: gzip
content-type: application/json
date: Sat, 26 Jun 2021 23:04:56 GMT
ocp-apim-apiid: httpbin-api
ocp-apim-operationid: get-legacy-data
ocp-apim-subscriptionid: master
ocp-apim-trace-location: https://apimstv3qbxr4vdkijuz7ryl.blob.core.windows.net/apimst4i5crna3vvpgdnkkbs-inspector/1MaLAFkuG6bFQvUKPbJ1Cw2-3?sv=2018-03-28&sr=c&sig=Xj3lHguN%2B6CXtMxLGnwIQdkT0JskNKTLLb0sqwTpZ%2Bc%3D&se=2022-06-26T21%3A44%3A24Z&sp=racwdl&traceId=5dbf29471cb5493aaa48f5b80d007403
transfer-encoding: chunked
vary: Accept-Encoding,Origin
    {
    "version": "1.0",
    "encoding": "us-ascii" /*  A SAMPLE set of slides  */ ,
    "slideshow": {
        "@title": "Sample Slide Show",
        "@date": "Date of publication",
        "@author": "Yours Truly",
        "$comment": [],
        "slide": [{
            "@type": "all",
            "title": "Wake up to WonderWidgets!"
        }, {
            "@type": "all",
            "title": "Overview",
            "item": [{
                "#text": ["Why ", " are great"],
                "em": "WonderWidgets"
            }, null, {
                "#text": ["Who ", " WonderWidgets"],
                "em": "buys"
            }]
        }]
    }
}
```

```
api-inspector (0.447 ms)
    {
    "request": {
        "method": "GET",
        "url": "https://prodapifpm.azure-api.net/xml",
        "headers": [
            {
                "name": "Cache-Control",
                "value": "no-cache, no-store"
            },
            {
                "name": "Connection",
                "value": "Keep-Alive"
            },
            {
                "name": "Content-Type",
                "value": "text/plain;charset=UTF-8"
            },
            {
                "name": "Accept",
                "value": "*/*"
            },
            {
                "name": "Accept-Encoding",
                "value": "gzip,deflate,br"
            },
            {
                "name": "Accept-Language",
                "value": "en-GB,en;q=0.9"
            },
            {
                "name": "Host",
                "value": "prodapifpm.azure-api.net"
            },
            {
                "name": "Max-Forwards",
                "value": "9"
            },
            {
                "name": "Referer",
                "value": "https://apimanagement.hosting.portal.azure.net/"
            },
            {
                "name": "sec-ch-ua",
                "value": "\" Not;A Brand\";v=\"99\",\"Microsoft Edge\";v=\"91\",\"Chromium\";v=\"91\""
            },
            {
                "name": "sec-ch-ua-mobile",
                "value": "?0"
            },
            {
                "name": "Ocp-Apim-Subscription-Key",
                "value": "bbebe003b3954f8f8b6afa82642ef6c3"
            },
            {
                "name": "Sec-Fetch-Site",
                "value": "cross-site"
            },
            {
                "name": "Sec-Fetch-Mode",
                "value": "cors"
            },
            {
                "name": "Sec-Fetch-Dest",
                "value": "empty"
            },
            {
                "name": "X-Forwarded-For",
                "value": "83.49.4.76,13.91.254.72:1408"
            },
            {
                "name": "X-WAWS-Unencoded-URL",
                "value": "/xml"
            },
            {
                "name": "CLIENT-IP",
                "value": "10.0.32.22:32140"
            },
            {
                "name": "X-ARR-LOG-ID",
                "value": "5dbf2947-1cb5-493a-aa48-f5b80d007403"
            },
            {
                "name": "X-SITE-DEPLOYMENT-ID",
                "value": "apimwebappurYmRIRj7O2fdIiSEjo6dz8fBEuxYQAAfLI0dp3o"
            },
            {
                "name": "WAS-DEFAULT-HOSTNAME",
                "value": "apimwebappurymrirj7o2fdiisejo6dz8fbeuxyqaafli0dp3o.azurewebsites.net"
            },
            {
                "name": "X-Original-URL",
                "value": "/xml"
            },
            {
                "name": "X-ARR-SSL",
                "value": "2048|256|C=US,O=Microsoft Corporation,CN=Microsoft Azure TLS Issuing CA 02|C=US,S=WA,L=Redmond,O=Microsoft Corporation,CN=*.azure-api.net"
            },
            {
                "name": "X-Forwarded-Proto",
                "value": "https"
            },
            {
                "name": "X-AppService-Proto",
                "value": "https"
            },
            {
                "name": "X-Forwarded-TlsVersion",
                "value": "1.2"
            },
            {
                "name": "DISGUISED-HOST",
                "value": "prodapifpm.azure-api.net"
            }
        ]
    }
}api-inspector (0.010 ms)
    {
    "configuration": {
        "api": {
            "from": "/",
            "to": {
                "scheme": "http",
                "host": "httpapifpm.azurewebsites.net",
                "port": 80,
                "path": "/",
                "queryString": "",
                "query": {},
                "isDefaultPort": true
            },
            "version": null,
            "revision": "1"
        },
        "operation": {
            "method": "GET",
            "uriTemplate": "/xml"
        },
        "user": "-",
        "product": "-"
    }
}cors (49.817 ms)
    "Origin header was missing or empty and the request was classified as not cross-domain. CORS policy was not applied."
```

##### Backend

(53.544 ms)[↑ Back to top](https://apimanagement.hosting.portal.azure.net/apimanagement/Content/1.286.0.4/apimap//apimap-apis/index.html?clientOptimizations=undefined&l=en.en-us&trustedAuthority=https%3A%2F%2Fportal.azure.com&shellVersion=undefined#httpResponse)

```
forward-request (0.453 ms)
    {
    "message": "Request is being forwarded to the backend service. Timeout set to 300 seconds",
    "request": {
        "method": "GET",
        "url": "http://httpapifpm.azurewebsites.net/xml",
        "headers": [
            {
                "name": "Host",
                "value": "httpapifpm.azurewebsites.net"
            },
            {
                "name": "Cache-Control",
                "value": "no-cache, no-store"
            },
            {
                "name": "Content-Type",
                "value": "text/plain;charset=UTF-8"
            },
            {
                "name": "Accept",
                "value": "*/*"
            },
            {
                "name": "Accept-Encoding",
                "value": "gzip,deflate,br"
            },
            {
                "name": "Accept-Language",
                "value": "en-GB,en;q=0.9"
            },
            {
                "name": "Max-Forwards",
                "value": "9"
            },
            {
                "name": "Referer",
                "value": "https://apimanagement.hosting.portal.azure.net/"
            },
            {
                "name": "sec-ch-ua",
                "value": "\" Not;A Brand\";v=\"99\",\"Microsoft Edge\";v=\"91\",\"Chromium\";v=\"91\""
            },
            {
                "name": "sec-ch-ua-mobile",
                "value": "?0"
            },
            {
                "name": "Ocp-Apim-Subscription-Key",
                "value": "bbebe003b3954f8f8b6afa82642ef6c3"
            },
            {
                "name": "Sec-Fetch-Site",
                "value": "cross-site"
            },
            {
                "name": "Sec-Fetch-Mode",
                "value": "cors"
            },
            {
                "name": "Sec-Fetch-Dest",
                "value": "empty"
            },
            {
                "name": "X-Forwarded-For",
                "value": "83.49.4.76,13.91.254.72:1408,13.91.254.72"
            },
            {
                "name": "X-WAWS-Unencoded-URL",
                "value": "/xml"
            },
            {
                "name": "CLIENT-IP",
                "value": "10.0.32.22:32140"
            },
            {
                "name": "X-ARR-LOG-ID",
                "value": "5dbf2947-1cb5-493a-aa48-f5b80d007403"
            },
            {
                "name": "X-SITE-DEPLOYMENT-ID",
                "value": "apimwebappurYmRIRj7O2fdIiSEjo6dz8fBEuxYQAAfLI0dp3o"
            },
            {
                "name": "WAS-DEFAULT-HOSTNAME",
                "value": "apimwebappurymrirj7o2fdiisejo6dz8fbeuxyqaafli0dp3o.azurewebsites.net"
            },
            {
                "name": "X-Original-URL",
                "value": "/xml"
            },
            {
                "name": "X-ARR-SSL",
                "value": "2048|256|C=US,O=Microsoft Corporation,CN=Microsoft Azure TLS Issuing CA 02|C=US,S=WA,L=Redmond,O=Microsoft Corporation,CN=*.azure-api.net"
            },
            {
                "name": "X-Forwarded-Proto",
                "value": "https"
            },
            {
                "name": "X-AppService-Proto",
                "value": "https"
            },
            {
                "name": "X-Forwarded-TlsVersion",
                "value": "1.2"
            },
            {
                "name": "DISGUISED-HOST",
                "value": "prodapifpm.azure-api.net"
            }
        ]
    }
}forward-request (53.091 ms)
    {
    "response": {
        "status": {
            "code": 200,
            "reason": "OK"
        },
        "headers": [
            {
                "name": "Access-Control-Allow-Origin",
                "value": "*"
            },
            {
                "name": "Access-Control-Allow-Credentials",
                "value": "true"
            },
            {
                "name": "Content-Length",
                "value": "522"
            },
            {
                "name": "Content-Type",
                "value": "application/xml"
            },
            {
                "name": "Date",
                "value": "Sat, 26 Jun 2021 23:04:56 GMT"
            },
            {
                "name": "Server",
                "value": "gunicorn/19.9.0"
            }
        ]
    }
}
```

##### Outbound

(47.334 ms)[↑ Back to top](https://apimanagement.hosting.portal.azure.net/apimanagement/Content/1.286.0.4/apimap//apimap-apis/index.html?clientOptimizations=undefined&l=en.en-us&trustedAuthority=https%3A%2F%2Fportal.azure.com&shellVersion=undefined#httpResponse)

```
xml-to-json (45.348 ms)
    "XML-to-JSON policy was applied. Original Content-Length header was removed as its value was invalidated. Content-Type header was set to 'application/json'."transfer-response (1.986 ms)
    {
    "message": "Response has been sent to the caller in full"
}
```

