## SOAP Connector

### References
* https://github.com/russellhaering/goxmldsig
* https://mojoauth.com/parse-and-generate-formats/parse-and-generate-xml-with-go#handling-complex-xml-structures
* https://chameerar.medium.com/consuming-soap-web-services-in-go-part-1-fe8817adea74

### Example
```
connector "soap" "quotes" {
  connection = http.ws_api
  method = "POST"
  soap_action = "GetClassesRequest"
  version = "1.1"

  ws_sec {
    username_token {
      username = 
      password =   
    }
    timestamp = true
    binary_security_token = file("assets/X.509.certs") 
    sign  = true
    encrypt = true    
  }
  
  body {
    template = file(assets/ws-body.tml) 
    var {
      name = "name-in-template"
      value = "v1"
    }
  } 
  
  header {
    template = file(assets/ws-header.tml)
    var {
      name = "name-in-template"
      value = "v1"
    }
  } 

  envelope {
     template = file("assets/ws-request.tml")
     var {
      name = "name-in-template"
      value = "v1"
    }
  }
  
  headers = {
    Content-Type : "application/xml",
    Accept : "application/xml",
  }

  on_status {
    status       = 400
    policy       = "ExponentialBackoff"
    count        = 3
    initial_wait = 10
    factor       = 2
  }

  on_status {
    status = 500
    policy = "Log"
  }

  result {
    name = "token"
    filter {
      xpathpath = "/access_token"
    }
  }
}
```

### Parameters
* One of (`header`, `body`) or `envelope` is required.

| Parameter Name                                                                         | Type            | Required? | Default Value |
|----------------------------------------------------------------------------------------|-----------------|-----------|---------------|
| `connection`: Http connection. See [HTTP Connection](conn.md).                         | HTTP Connection | Yes       |               |
| `method`: HTTP Method.                                                                 | String          | No        | POST          |
| `soap_action`: SOAP action to be used. This will be sent in the `SOAPAction` http header | String          | Yes       |               |
| `version`: SOAP spec version (`1.1` or `1.2`)                                          | String          | No        | 1.2           |
| `ws_sec`: WS-Security header configuration                                             | WSSecurity Type | No        ||
| `header`: SOAP header. Either provide in-line or using a template                      | Header Type     | No        ||
| `body`: SOAP body. Either provide in-line or using a template                          | Body Type       | Yes       ||
| `envelope`: SOAP envelope. Either provide in-line or using a template                  | Envelope Type   | Yes       ||
| `headers`: Http headers. Note `SOAPAction` header will be overriden by `soap_action`   | Map             | No        |
| `on_status`: Response status handlers (1 or more). See [OnStatus](cont.md)             | OnStatus        | No        |
| `result`: SOAP result from the execution                                               | Result          | No        |

#### WSSecurity 
| Parameter Name                                    | Type          | Required? | Default Value |
|---------------------------------------------------|---------------|-----------|---------------|
| `username_token`: Username token for WS-Security  | UserNameToken | No        |               |
| `timestamp`: Generate timestamp (`true`, `false`) | Bool          | No        | true          |
| `binary_security_token`: X509 certificate.        |               |           |               |
| `private_key`: Private Key.                       |               |           |               |
| `sign`: Sign the request (`true`, `false`)        | Bool          | No        | true          |
| `encrypt`: Encrypt the request (`true`, `false`)  | Bool          | No        | true          |

##### UserNameToken    
| Parameter Name                          | Type   | Required? | Default Value   |
|-----------------------------------------|--------|-----------|-----------------|
| `username`: Username for username token | String | Yes       ||
| `password`: Password for username token | String | Yes       ||
        

