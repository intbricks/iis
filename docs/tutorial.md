## Tutorial 
Welcome to the IntBrick Integration Service (IIS). In this tutorial, you will learn how to implement your first integration
using IIS. [Contact us](mailto:info@intbricks.com) for a product download link and a key.
 
* [HCL](https://github.com/hashicorp/hcl/) based Domain-specific langauge ([DSL](https://en.wikipedia.org/wiki/Domain-specific_language)) is used to configure Integration Service logic.
* IIS configuration langauge supports pre-defined functions through the standard library to simply user's effort on writing the configurations.
* Let's build an integration to download a file from a S3 bucket to the local file system. The full configuration for the scenario is shown below.
```
version = "1.0.0"

package = "s3"

connection "aws" "s3_conn" {
  access_key = env("ACCESS_KEY")
  secret_key = env("SECRET_KEY")
  region = "us-east-1"
}

connector "s3" "download_s3" {
  operation  = "GetObject"
  key        = "invoice.pdf"
  bucket     = "invoice-storage"
  connection = aws.s3_conn
}

connector "fs" "write_to_fs" {
  operation = "Write"
  path = "assets/invoice-fromS3.pdf"
  override = true
}

schedule "onetime_s3" {
  expression = "onetime()"
  time_zone = "America/Chicago"
}

service "s32local" {
  in_flow = ["s3.download_s3", "fs.write_to_fs"]
  schedule = sched.onetime_s3
}
```
* Each config file starts with `version`. `version` defines the configuration langauge version, which is currently `1.0.0`.
* Each config file belongs to a `package`. `pacakge` allows to group a configuration files together.
* A `connection` defines the external connection. In this case it will be of type `aws` with the name `s3_conn`.
* `aws` connection defines connection to an AWS resource with `access_key`, `secret_key` and `region`. Based on the type of 
connection these parameters will differ. For example, a database connection will have the database specific parameters. 
See [reference](reference.md) section for details. 
* A `connector` defines a unit of functionality. 
* `s3` connector defines the unit of functionality to interact with AWS S3 resource with `operation`, `key`, `bucket`. 
 Here the `s3` connector:  `download_s3` will download the file called: `invoice.pdf` from the S3 bucket: `invoice-storage`.  
* `fs` connector defines the unit of functionality to interact with the local file system. It supports writing(`Write`) 
or reading(`Read`) a file with the given `path`. If the file already exist it can be overridden with `override` set to `true`.
Here the `fs` connector: `write_to_fs`  will write the file to: `assets/invoice-fromS3.pdf`.
* `schedule` defines a schedule task. Schedule can be a onetime, a cron expression or exact time. See [reference](reference.md) section for details.
The `schedule`: `onetime_s3` will be executed once. 
* Finally, a `service` block defines the integration. Service has a `in_flow` and an optional `out_flow`. Each flow is 
collection of ordered connector references. `service` has a schedule for `in_flow` and `out_flow`
* If you put the above configuration file into a file called: `s3-download.hcl`, and have necessary S3 bucket 
(see [AWS S3 documentation](https://aws.amazon.com/s3/getting-started/) if you are new to S3), you can run the service with:
```
$ @IIS_KEY=<product-key> @ACCESS_KEY=<aws_access_key> SECRET_KEY=<aws_secret_key> REGION=us-east-1 iis --host 127.0.0.1  --port 8080 --packages s3:<path/to/s3-download/dictory>
```
* Next: you can read more about the configuration in [reference](reference.md), [standard library](stdlib.md) or review end-to-end working  
