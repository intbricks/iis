## SQLite Connector

### Examples
```
connecton "sqlite" "sqlite_conn2" {
  source = "file://istest.db"
}

connector "sqlite" "version_check" {
  connection = sqlite.sqlite_conn
  operation = "Select"
  query = "select sqlite_version()"
}
```

### Parameters
| Parameter Name                                                                              | Type              | Required? | Default Value   |
|---------------------------------------------------------------------------------------------|-------------------|----|-----------------|
| `connection`: SQLite connection reference. See [connection docs](conn.md).                  | SQLite Connection | Yes       |               |
| `operation`: SQL query operation( `Select`, `Insert`, `Update`, `Delete`)                   | String            | Yes       |               |
| `query`: Sql query to execute. Can be inline or load from an external file (using `file()`) | String            | Yes       |               |
| `parameter`: Input parameter(s) for the query. See [SQL Parameter](cont.md) docs.           | Parameter         | No        |               |
| `result`: Track result(s) from the query execution. See [Result](cont.md) docs.             | Result            | No        |               |
