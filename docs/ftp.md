## FTP(File Transfer Protocol) Connector

### Examples


### Parameters
| Parameter Name                                                                                | Type           | Required? | Default Value |
|-----------------------------------------------------------------------------------------------|----------------|-----------|---------------|
| `connection`: FTP connection reference. See [connection docs](conn.md).                       | FTP Connection | Yes       |               |
| `operation`: Upload or download (`Upload`,`Download`).                                        | String         | Yes       |               |
| `path`: Path to the file or folder.                                                           | String         | Yes       |               |
| `file_name_pattern`: Matching [regex](https://pkg.go.dev/regexp#example-package) for the file | String          | Yes       |               |
| `override`: Override the content, valid for `Upload`.                                         | Bool           | No        | `false`         |
| `tags`: Specify meta data using (key,value)                                                   | Map            | No        |               |
