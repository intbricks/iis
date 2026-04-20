## MySQL Connector

### Examples

```
variable "username" {
  type    = string
  default = "mysql"
}

connection "mysql" "mysql_conn" {
  host     = env("DB_HOST")
  port     = 1521
  username = var.username
  password = env("DB_PASSWORD")
  db_name  = env("DB_NAME")
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

connector "mysql" "version_check" {
  connection   = mysql.mysql_conn
  operation    = "Select"
  query        = "SELECT version()" // check the connector
}
```

### Parameters

| Parameter Name                                                                             | Type             | Required? | Default Value |
|--------------------------------------------------------------------------------------------|------------------|-----------|---------------|
| `connection`: MySQL connection reference. See [connection docs](conn.md).                  | MySQL Connection | Yes       |               |
| `operation`: SQL query operation( `Select`, `Insert`, `Update`, `Delete`)                  | String           | Yes       |               |
| `query`: Sql query to execute. Can be inline or load from an external file (using `file()`) | String           | Yes       |               |
| `parameter`: Input parameter(s) for the query. See [SQL Parameter](cont.md) docs.          | Parameter        | No        |               |
| `result`: Track result(s) from the query execution. See [Result](cont.md) docs.            | Result           | No        |               |
