## SFTP(Secure File Transfer Protocol) Connector

### References
* https://www.sectigo.com/blog/what-is-an-ssh-key
* https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process
* https://servicenow.iu.edu/kb?id=kb_article_view&sysparm_article=KB0023919

### Examples
```
connection "sftp" "sftp_conn" {
  host     = "ec2-54-175-114-196.compute-1.amazonaws.com"
  port     = 22
  username = var.username
  password = env("SFTP_PASSWORD")
}

connector "sftp" "upload_sftp" {
  connection = sftp.sftp_conn
  operation  = "upload"
  path       = "/data/s32sftp/upload/s32sftp.pdf"
}

connector "sftp" "download_sftp" {
  operation  = "download"
  connection = sftp.sftp_conn
  path       = "/data/s32sftp/upload/s32sftp.pdf"
}
```

### Parameters
* If `file_name_pattern` given and `path` is an absolute path, `file_name_pattern` will be ignored.
* `file_name_pattern` should be a valid [Go-regex](https://pkg.go.dev/regexp#pkg-overview)

| Parameter Name                                                                                | Type            | Required? | Default Value |
|-----------------------------------------------------------------------------------------------|-----------------|-----------|---------------|
| `connection`: SFTP connection reference. See [connection docs](conn.md).                      | SFTP Connection | Yes       |               |
| `operation`: Upload or download (`Upload`,`Download`).                                        | String          | Yes       |               |
| `path`: Path to the file or folder                                                            | String          | Yes       |               |
| `file_name_pattern`: Matching [regex](https://pkg.go.dev/regexp#example-package) for the file | String          | Yes       |               |
| `override`: Override the content, valid for `Upload`.                                         | Bool            | No        | `false`         |
| `tags`: Specify meta data using (key,value)                                                   | Map             | No        |               |
