## Template 
### <> Connection

#### Example

#### <> Connection Parameters
|Parameter Name| Type   | Required? | Default Value   |
|---|---|----|-----------------|
|||||
|||||
|||||
|||||

## Common Connection Documentation
* This contains the documentation for configuring various types of connections. 
* Common types are defined below. 

### Options 
| Parameter Name                            | Type    | Required? | Default Value  |
|-------------------------------------------|---------|-----------|----------------|
| `read_timeout_in_seconds`: Read timeout   | Number  | No        |                |
| `write_timeout_in_seconds`: Write timeout | Number  | No        |                |
| `onerror`: Error handling configuration   | OnError | No        | `Log` and exit |
                                   
### OnError
| Parameter Name                                                               | Type   | Required? | Default Value |
|------------------------------------------------------------------------------|--------|-----------|---------------|
| `policy`: Policy to handle the error(`ReInit`, `Drop`, `Log`)                | String | No        | `Log`         |
| `count`: Number of retry attempts (valid for `ReInit` and `Log`)             | Number | No        | `3`           |
| `initial_wait_in_seconds`: Initial time (in seconds) to wait after a failure | Number | No        | `3`           |
| `factor`: Multipaction factor for exponential backoff                        | Number | No        | `10`          |

### Pool
| Parameter Name                                                               | Type   | Required? | Default Value |
|------------------------------------------------------------------------------|--------|-----------|---------------|
| `max_open_connections`: The maximum number of open connections to the database               | Number | No        | `0`         |
| `max_idle_connections`: The maximum number of connections in the idle connection pool          | Number | No        | `2`           |
| `max_connection_life_time_in_seconds`:The maximum amount of time a connection may be reused | Number | No        | `0`           |
| `max_connection_idle_time_in_seconds`: The maximum amount of time a connection may be idle before being closed                      | Number | No        | `0`  |

### AWS Connection

#### Example

```
connection "aws" "s3" {
  access_key = env("ACCESS_KEY")
  secret_key = env("SECRET_KEY")
  region = "us-east-1"
}
```

#### AWS Connection Parameters

* Specify sensitive parameters using an external source (such as `env`) rather directly specifying.
* One of (`access_key`, `secret_key`) or `profile` or `iam_profile` is required.

| Parameter Name                  | Type   | Required?                                                           | Default Value |
|---------------------------------|--------|---------------------------------------------------------------------|---------------|
| `access_key`: AWS Access Key.   | String | Yes if `profile` or `iam_profile` is not provided                   |               |
| `secret_key`: AWS Secret Key.   | String | Yes if `profile` or `iam_profile` is not provided                   |               |
| `region`: AWS Region.           | String | Yes                                                                 |               |
| `profile`: AWS Profile.         | String | Yes if (`access_key`, `secret_key`) or `iam_profile` is not provided |               |
| `iam_profile`: AWS IAM Profile. | String | Yes if (`access_key`, `secret_key`) or `profile` is not provided    |               |

### FTP(S) Connection

#### Example
```
connection "ftp" "ftp_conn" {
  host     = "ec2-54-175-114-196.compute-1.amazonaws.com"
  port     = [22, 900]
  username = var.username
  password = env("SFTP_PASSWORD")
}
```

#### FTP(S) Connection Parameters
* One of (`username`, `password`) or (`username`, `ssh_key`) is required.

| Parameter Name                                                                                                           | Type   | Required? | Default Value |
|--------------------------------------------------------------------------------------------------------------------------|--------|-----------|--------------|
| `host`: FTP server hostname.                                                                                             | String | Yes       |              |
| `ports`: FTP server ports(control port, data ports).                                                                     | List   | No        | [22]         |
| `username`: FTP server username.                                                                                         | String | No        |              |
| `password`: FTP server password.                                                                                         | String | No        |              |
| `private_key`: Private key for server's X.509 certificate.                                                               | String | No        |              |
| `upload_key`: Have IS generate a X.509 certificate, private key pair. X509 cert then need to install into the FTP server | Bool   | No        |    |


### Http Connection 
#### Example 
```
connection "http" "photo_api" {
  options {
    read_timeout_in_seconds  = 100
    write_timeout_in_seconds = 100
    onerror {
      policy                  = "re-init"
      count                   = 3
      initial_wait_in_seconds = 100
      factor                  = 10
    }
  }
  protocol = "http"
  host     = "localhost"
  port     = 9000
}
```
#### Http Connection Parameters
| Parameter Name                                              | Type   | Required? | Default Value |
|-------------------------------------------------------------|--------|-----------|---------------|
| `protocol`: HTTP protocol (`http` or `https`)               | String | No        | `https`        |
| `host`: Target host                                         | String | Yes       |               |
| `port`: Target host port                                    | Number | Yes       |               |
| `options`: Connection options. See [Options](conn.md) docs. | Options   | No        |              

### SFTP Connection

#### Example 
```
connection "sftp" "sftp_conn" {
  host     = "ec2-54-175-114-196.compute-1.amazonaws.com"
  port     = 22
  username = var.username
  password = env("SFTP_PASSWORD")
}
```

#### SFTP Connection Parameters
* One of (`username`, `password`) or (`username`, `ssh_key`) or (`username`, `upload_key`) is required. 

| Parameter Name                                                                                                              | Type   | Required?                      | Default Value |
|-----------------------------------------------------------------------------------------------------------------------------|--------|--------------------------------|---------------|
| `host`: SFTP server hostname.                                                                                               | String | Yes                            |               |
| `port`: SFTP server port.                                                                                                   | Number | No                             | 22            |
| `username`: SFTP server username.                                                                                           | String | Yes                            |               |
| `password`: SFTP server password.                                                                                           | String | Yes if `ssh_key` is not given  |               |
| `private_key`: Private key for authentication instead of (username, password).                                              | String | Yes if `password` is not given |               |
| `upload_key`: Have IS generate a (X.509 certificate, private key) pair. X509 cert then need to install into the SFTP server | Bool   | Yes if                         |    |
       
### Oracle Connection 

#### Example
```
connection "oracle" "oracle_connection" {
  host     = env("DB_HOST")
  port     = 1521
  service  = env("DB_SERVICE")
  username = var.username
  password = env("DB_PASSWORD")
  options {
    read_timeout_in_seconds = 100
    write_timeout_in_seconds = 100
    onerror {
      policy                  = "ReInit"
      count                   = 3
      initial_wait_in_seconds = 100
      factor                  = 10
    }
  }
}
```

#### Oracle Connection Parameters
| Parameter Name                                              | Type      | Required? | Default Value |
|-------------------------------------------------------------|-----------|-----------|---------------|
| `host`: Oracle server hostname/ip.                          | String    | Yes       |               |
| `port`: Oracle server port.                                 | Number    | No        | 1521          |
| `service`: Oracle service name.                             | String    | Yes       |               |
| `username`: Oracle database username.                       | String    | Yes       |               |
| `password`: Oracle database password.                       | String    | Yes       |               |
| `options`: Connection options. See [Options](conn.md) docs. | Options   | No        |               |

### MySQL Connection

#### Example
```
connection "mysql" "mysql_conn2" {
  host     = env("DB_HOST")
  port     = 1521
  username = var.username
  password = env("DB_PASSWORD")
  db_name = env("DB_NAME")
  pool {
    max_open_connections = 25
    max_idle_connections = 25
    max_connection_life_time_in_seconds = 300
    max_connection_idle_time_in_seconds = 120
  }
  options {
    timeout_in_seconds = 100
    onerror {
      policy                  = "ReInit"
      count                   = 3
      initial_wait_in_seconds = 100
      factor                  = 10
    }
  }
}
```

#### MySQL Connection Parameters
| Parameter Name                                              | Type      | Required? | Default Value |
|-------------------------------------------------------------|-----------|-----------|---------------|
| `host`: MySQL server hostname/ip.                           | String    | Yes       |               |
| `port`: MySQL server port.                                  | Number    | No        | 3306            |
| `db_name`: MySQL database name.                             | String    | Yes       |               |
| `username`: MySQL database username.                        | String    | Yes       |               |
| `password`: MySQL database password.                        | String    | Yes       |               |
| `pool`: Pool configurations. See [Pool](#pool) docs.      | Pool      | No        |               |
| `options`: Connection options. See [Options](#options) docs. | Options   | No        |               |


### PostgreSQL Connection

#### Example
```
connection "postgresql" "mysql_conn2" {
  host     = env("DB_HOST")
  port     = 5432
  username = var.username
  password = env("DB_PASSWORD")
  db_name = env("DB_NAME")
  pool {
    max_open_connections = 25
    max_idle_connections = 25
    max_connection_life_time_in_seconds = 300
    max_connection_idle_time_in_seconds = 120
  }
  options {
    timeout_in_seconds = 100
    onerror {
      policy                  = "ReInit"
      count                   = 3
      initial_wait_in_seconds = 100
      factor                  = 10
    }
  }
}
```

#### PostgreSQL Connection Parameters
| Parameter Name                                              | Type      | Required? | Default Value |
|-------------------------------------------------------------|-----------|-----------|---------------|
| `host`: PostgreSQL server hostname/ip.                           | String    | Yes       |               |
| `port`: PostgreSQL server port.                                  | Number    | No        | 5432            |
| `db_name`: PostgreSQL database name.                             | String    | Yes       |               |
| `username`: PostgreSQL database username.                        | String    | Yes       |               |
| `password`: PostgreSQL database password.                        | String    | Yes       |               |
| `pool`: Pool configurations. See [Pool](#pool) docs.      | Pool      | No        |               |
| `options`: Connection options. See [Options](#options) docs. | Options   | No        |               |


### Sqlite Connection

* SQLite file can be read from the local file system or from an S3 bucket.

#### Example
```
connection "sqlite" "mysql_conn2" {
  source = "is-test.db"
}

connection "sqlite" "sqlite_conn" {
  source = "s3://integration-test/istest.db"
  aws_conn = aws.s3
  options {
    timeout_in_seconds = 100
    onerror {
      policy                  = "ReInit"
      count                   = 3
      initial_wait_in_seconds = 100
      factor                  = 10
    }
  }
}
```

#### Sqlite Connection Parameters

| Parameter Name                                                                                   | Type           | Required? | Default Value |
|--------------------------------------------------------------------------------------------------|----------------|-----------|---------------|
| `source`: Sqlite file system or S3 bucket location.                                              | String         | Yes       |               |
| `aws_conn`: If the source type is AWS, provide the connection details to read from the S3 bucket | AWS Connection | No        |               |
| `options`: Connection options (valid for AWS Connection). See [Options](conn.md) docs.           | Options        | No        |               |
        
