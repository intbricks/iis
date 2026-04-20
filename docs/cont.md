## Template Connector

### References

### Examples

### Parameters
|Parameter Name| Type   | Required? | Default Value   |
|---|---|----|-----------------|
|||||
|||||
|||||
|||||


## Common Connector Documentation
* This contains the documentation for configuring various types common for connectors.
* Common types are defined below. 

### Result
| Parameter Name                                                           | Type   | Required? | Default Value   |
|--------------------------------------------------------------------------|--------|-----------|-----------------|
| `name`: Name for result                                                  | String | Yes       ||
| `filter`: Filter for result (store the result after applying the filter) | Filter | No        ||   
                
### Filter
* One of `xpath` or `jsonpath` or `csv` is required.

| Parameter Name                                                                                                                                             | Type     | Required? | Default Value   |
|------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|-----------|-----------------|
| `xpath`: Apply a XPath expression to the result (XML data)                                                                                                 | `string` | No        ||
| `jsonpath`: Apply a JSONPath expression to result (JSON data)                                                                                              | `string` | No        ||
| `csv`: Apply a [Panda DataFrame filter expression](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.filter.html) to result (CSV/tabular data) | `string` | No        ||

### SQL Parameter

| Parameter Name                                                               | Type   | Required? | Default Value |
|------------------------------------------------------------------------------|--------|-----------|---------------|
| `name`: Parameter name                                                       | String | Yes       |               |
| `value`: Parameter value                                                     | String | Yes       |               |
| `type`: Parameter type (`String`, `Number`, `Date`, `DateTime`, `TimeStamp`) | String | No        |               |

### OnStatus

| Parameter Name                                                    | Type    | Required? | Default Value  |
|-------------------------------------------------------------------|---------|-----------|----------------|
| `status`: Http status code                                        | Number  | Yes       |                |
| `options`: Response handler options (see [Options type](conn.md)) | Options | No        | `Log` and drop |
