## REST Connector

### References
* https://frontegg.com/blog/oauth-flows
* https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2
* https://curity.io/resources/learn/oauth-client-credentials-flow/
* https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation
* https://developers.zoom.us/docs/internal-apps/s2s-oauth/
* https://www.informatica.com/content/dam/informatica-cxp/techtuesdays-slides-pdf/Simplify%20REST%20API%20Integrations%20in%20IICS.pdf
* https://tutorialedge.net/golang/go-oauth2-tutorial/
           
### Examples 
* No auth example:
```
version = "1.0.0"

package = "rest"

connector "rest" "no_auth" {
  resource   = "/quotes"
  connection = http.photo_api

  method = "POST"
  headers = {
    Content-Type : "application/json",
    Accept : "application/json",
    X-API-client : "no_auth_client"
  }
}

service "no_auth_service" {
  log = true // enable debug logs
  in_flow = ["rest.no_auth"]
  schedule = sched.schedule_once
}

// on a schedule
service "no_auth_service2" {
  log = true // enable debug logs
  in_flow = ["rest.no_auth"]
  schedule = sched.schedule_exp
}
```

* Basic auth example: 
```
version = "1.0.0"
package = "rest"

connector "rest" "basic_auth" {
  resource   = "/secure/quotes"
  mode       = "stream"
  connection = http.photo_api

  basic_auth {
    username = env("PHOTO_USERNAME")
    password = env("PHOTO_PASSWORD")
  }

  method = "POST"

  // if basic auth header is present ignore that -- or print a warning
  headers = {
    Content-Type : "application/json",
    Accept : "application/json",
    X-Cutom-Header : "X-Custom-Value",
  }
}

service "basic_auth_service" {
  log = true // enable debug logs
  in_flow = ["rest.basic_auth"]
  schedule = sched.schedule_once
}
```

### Parameters

| Parameter Name                                                             | Type            | Required? | Default Value |
|----------------------------------------------------------------------------|-----------------|-----------|---------------|
| `connection`: Http connection referece. See [connection docs](conn.md)     | Http Connection | Yes       |               |
| `resource`: REST resource                                                  | String          | Yes       |               |
| `headers`: (Key,value) map of headers                                      | Map             | No        |               |
| `basic_auth`: Configure basic auth                                         | BasicAuth       | No        |               |
| `oauth2`: Configure OAuth2                                                 | OAuth2          | No        |               |
| `resource`: REST resource                                                  | String          | Yes       |               |
| `method`: Http method (`GET`, `POST`, `HEAD`, `PUT`, `DELETE`)             | String          | Yes       |               |
| `query_params`: Query parameters for the request                           | Map             | No        |               |
| `result`: REST result                                                      | Result          | No        |               |
| `payload`: Payload for the request                                         | Payload         | No        |               |
| `on_status`: Response status handlers (1 or more). See [OnStatus](cont.md) | OnStatus        | No        |               |

#### BasicAuth
| Parameter Name                     | Type   | Required? | Default Value |
|------------------------------------|--------|-----------|---------------|
| `username`:Username for basic auth | String | Yes       |               |
| `password`:Password for basic auth | String | Yes       |               |
      
#### OAuth2
* Either (`token_endpoint`, `grant_type`, `client_id`, `client_secret`) (with `username`, `password` if token endpoint is secured) or previously obtained `access_token` is required.

| Parameter Name                                        | Type   | Required? | Default Value |
|-------------------------------------------------------|--------|-----------|---------------|
| `token_endpoint`: OAuth2 token endpoint               | Stirng | No        |               |
| `username`: Configure username for the token endpoint | String | No        |               |
| `password`: Configure password for the token endpoint | String | No        |               |
| `grant_type`: OAuth2 grant type                       | String | No        |               |
| `client_id`: OAuth2 client id                         | String | No        |               |
| `client_secret`: OAuth2 client secret                 | String | No        |               |
| `access_token`: OAuth2 access client                  | String | No        |               |


#### Payload

| Parameter Name                                                                            | Type   | Required? | Default Value |
|-------------------------------------------------------------------------------------------|--------|-----------|---------------|
| `template`: Provide a [Go template](https://pkg.go.dev/text/template) for input data body | String | Yes       |               |
