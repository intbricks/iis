## PostgreSQL Connector

### Examples
```
variable "username" {
  type    = string
  default = "postgrey"
}

connection "postgrey" "postgrey_conn" {
  host     = env("DB_HOST")
  port     = 5432
  username = var.username
  password = env("DB_PASSWORD")
  db_name = env("DB_NAME")
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

connector "postgrey" "version_check" {
  connection = postgrey.postgrey_conn
  operation  = "Select"
  query        = "SELECT version()" // check the connector
}

```

### Parameters
| Parameter Name                                                                              | Type                  | Required? | Default Value |
|---------------------------------------------------------------------------------------------|-----------------------|-----------|---------------|
| `connection`: PostgreSQL connection reference. See [connection docs](conn.md).              | PostgreSQL Connection | Yes       |               |
| `operation`: SQL query operation( `Select`, `Insert`, `Update`, `Delete`)                   | String                | Yes       |               |
| `query`: Sql query to execute. Can be inline or load from an external file (using `file()`) | String                | Yes       |               |
| `parameter`: Input parameter(s) for the query. See [SQL Parameter](cont.md) docs.           | Parameter             | No        |               |
| `result`: Track result(s) from the query execution. See [Result](cont.md) docs.             | Result                | No        |               |
