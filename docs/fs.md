## File System(FS) Connector

### Examples 
```
connector "fs" "write_to_fs" {
  operation = "Write"
  path = "assets/fromS3.pdf"
  override = true
}
```

```
connector "fs" "read" {
  operation = "Read"
  path = "C:\\Data\\inputs.csv"
}
```

### Parameters

| Parameter Name                                                                                                      | Type   | Required? | Default Value |
|---------------------------------------------------------------------------------------------------------------------|--------|-----------|---------------|
| `operation`: Specify the operation (`Write`, `Read`).                                                               | String | Yes       |               |
| `path`: Path to the file.                                                                                           | String | Yes       |               |
| `override`: Override the content, valid for `Write`.                                                                | Bool   | No        | `false`       |
| `type`: Indicate filetype (`Txt`, `Binary`). If `Txt` is indicated content can be accessed within other connectors. | String | No        | `Binary`      |
| `tags`: Specify meta data using (key,value)          | Map            | No        ||
