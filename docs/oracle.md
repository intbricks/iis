## Oracle Connector 

### References
* https://www.oracle.com/developer/working-in-go-applications-with-oracle-database-and-oracle-cloud-autonomous-database/
* https://pkg.go.dev/github.com/godror/godror
* https://github.com/sijms/go-ora
* https://www.syntio.net/en/labs-musings/efficient-fetching-of-data-from-oracle-database-in-golang/

### Examples 
```
variable "username" {
  type    = string
  default = "kumarasiri"
}

connection "oracle" "oracle_connection" {
  host     = env("DB_HOST")
  port     = 1521
  service  = env("DB_SERVICE")
  username = var.username
  password = env("DB_PASSWORD")
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

connector "oracle" "version_check" {
  connection = oracle.oracle_connection
  operation  = "Select"
  query        = "SELECT BANNER, BANNER_LEGACY FROM v$version" // check the connector
}
```

### Parameters 
| Parameter Name                                                                              | Type              | Required? | Default Value |
|---------------------------------------------------------------------------------------------|-------------------|-----------|---------------|
| `connection`: Oracle connection reference. See [connection docs](conn.md).                  | Oracle Connection | Yes       ||
| `operation`: SQL query operation( `Select`, `Insert`, `Update`, `Delete`)                   | String            | Yes       ||
| `query`: Sql query to execute. Can be inline or load from an external file (using `file()`) | String            | Yes       ||
| `parameter`: Input parameter(s) for the query. See [SQL Parameter](cont.md) docs.           | Parameter         | No        ||
| `result`: Track result(s) from the query execution. See [Result](cont.md) docs.             | Result            | No        ||

## Connector Issues and Fixes
* Oracle connector timeout:
```
    ORA-03135: connection lost contact
Process ID: 0
Session ID: 0 Serial number: 0
Help: https://docs.oracle.com/error-help/db/ora-03135/ 
```
Configuration notes: https://download.oracle.com/ocomdocs/global/Oracle-Net-Easy-Connect-Plus.pdf
  
* `ORA-00933: SQL command not properly ended`:
Had an additional `;` at the SQL statment: `SELECT DISTINCT emplid FROM SYSADM.ps_stdnt_car_term;` 

* Populating slice vs using `append` 
```
emplIdsPtrs := make([]*string, len(emplIds))
for index, emplId := range emplIds {
    emplIdsPtrs[index] = &emplId // if we use append, it will add null elements
}
```

* `query error ORA-01484: arrays can only be bound to PL/SQL statements`
This happens when passing arguments as an array directly (below will fail):
```
emplIds := []string{"0004709296", "0004399656", "0004382311", "0004416207", "0004417156", "0004417720", "0004465238", "0004465392", "0004450013", "0004461237"}
	emplIdPtrs := make([]*string, len(emplIds))

	for index, emplId := range emplIds {
		emplIdPtrs[index] = &emplId
	}

	args := sql.Named("emplids", emplIdPtrs)
	
	rows, err := conn.Query(query, args)  
```
* `query error ORA-01006: bind variable does not exist`
This is due to not passing the variable in the SQL query. 
    

