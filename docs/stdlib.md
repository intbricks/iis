## Standard Library
IntBrick's Integration Service (IIS) standard library documentation.

###  Numeric Functions
| Function   | Description                                                                                                 | Example                                                                |
|------------|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| `abs`      | Returns the absoute value of a value                                                                        | `abs(23) = 23`, `abs(0) = 0`                                           |
| `ceil`     | Rreturns the closest whole number that is greater than or equal to the given value, which may be a fraction | `ceil(5) = 5`, `ceil(5.1) = 6`                                         |
| `floor`    | Returns the closest whole number that is less than or equal to the given value, which may be a fraction     | `floor(5) = 5`, `floor(4.9) = 4`                                       |
| `log`      | Returns the logarithm of a given number in a given base                                                     | `log(50, 10) = 1.6989700043360185`                                     |   
| `max`      | Returns the maximum from a two or more input numbers                                                        | `max(12, 54, 3) = 54`, `max([12, 54, 3]...) = 54`                      |
| `min`      | Return the minimum from a two or more input numbers                                                         | `min(12, 54, 3) = 3`, `min([12, 54, 3]...) = 3`                        |
| `parseint` | Parses a the given string represenation of an integer in the provided base and return the result            | `parseint("100", 10) = 100`, `parseint("1011111011101111", 2) = 48879` |
| `pow`      | Calcuates the expoonent, first argument to the power of second argument                                     | `pow(5, 3) = 125`                                                      |
| `signum`   | Determines the sign of a number, returning -1, 0, 1 for negative, zero, positive numbers respectively       | `signum(-13) = -1`, `signum(0) = 0` , `signum(13) = 1`                 |

### String Functions

| Function           | Description                                                                              | Example                                                                                                                             |
|--------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `appendifmissing`  | Appends a suffix to the end of the string if not present                                 |                                                                                                                                     |
| `capitalize`       |                                                                                          |                                                                                                                                     |
| `chomp`            | Remove new line character(s) from end of a string                                        | `chomp("hello\n\n") = hello`, `chomp("hello\r\n") = hello`                                                                          |
| `chop`             | Remove the last character from a string                                                  |
| `center`           | Centers a string in larger string of size `size` using a space character(` `)            |                                                                                                                                     |
| `empty`            | Check if a string contains text                                                          |                                                                                                                                     |
| `endswith`         |                                                                                          |                                                                                                                                     |
| `format`           | Produce a formatted string according to the format specifier                             | `format("hello in Sinhala: , %s!", "ආයුබෝවන්") = hello in Sinhala: ආයුබෝවන්!`, `format("Hello, %s!", var.greeting) = Hello, there!` |
| `formatlist`       |                                                                                          |                                                                                                                                     |
| `indent`           | Add specified number of spaces in a multi-line funciton, except first line               |                                                                                                                                     |
| `indexof`          | Check the index of a chracter                                                            |                                                                                                                                     |
| `isalpha`          |                                                                                          |                                                                                                                                     |
| `isnumeric`        |                                                                                          |                                                                                                                                     |
| `iswhitespace`     |                                                                                          |                                                                                                                                     |
| `iswhitespace`     |                                                                                          |                                                                                                                                     |
| `lastindexof`      | Check the last index of a character                                                      |                                                                                                                                     |
| `join`             | Produce a string concatinating all the elements of the speficied list with the seperator | `join(" ", ["hello", "world"]) = hello world`                                                                                       |
| `lower`            |                                                                                          |                                                                                                                                     |
| `leftpad`          |                                                                                          |                                                                                                                                     |
| `prependifmissing` | Prepends a prefix to the start of the string if not present                              |                                                                                                                                     |
| `regex`            |                                                                                          |                                                                                                                                     |
| `regexall`         |                                                                                          |                                                                                                                                     |
| `replace`          |                                                                                          |                                                                                                                                     |
| `repeat`           |                                                                                          |                                                                                                                                     |
| `remove`           | Remove part of a string, if avaiable                                                     |                                                                                                                                     |
| `reverse`          |                                                                                          |                                                                                                                                     |
| `reversedelimited` |                                                                                          |                                                                                                                                     | 
| `rightpad`         |                                                                                          |                                                                                                                                     |
| `rotate`           |                                                                                          |                                                                                                                                     |  
| `split`            |                                                                                          |                                                                                                                                     |
| `startswith`       |                                                                                          |                                                                                                                                     |
| `strcontains`      |                                                                                          |                                                                                                                                     |
| `strrev`           |                                                                                          |                                                                                                                                     |
| `swapcase`         |                                                                                          |                                                                                                                                     |
| `substr`           |                                                                                          |                                                                                                                                     |
| `substrbefore`     |                                                                                          |                                                                                                                                     |
| `substrafter`      |                                                                                          |                                                                                                                                     |
| `substrbetween`    |                                                                                          |                                                                                                                                     |
| `templatestring`   |                                                                                          |                                                                                                                                     |
| `title`            |                                                                                          |                                                                                                                                     |
| `trim`             |                                                                                          |                                                                                                                                     |
| `trimprefix`       |                                                                                          |                                                                                                                                     |
| `trimsuffix`       |                                                                                          |                                                                                                                                     |
| `trimspace`        |                                                                                          |                                                                                                                                     |
| `upper`            |                                                                                          |                                                                                                                                     |

### Collection Functions

| Function          | Description | Example |
|-------------------|-------------|---------|
| `alltrue`         |             |         |
| `anytrue`         |             |         |
| `chunklist`       |             |         |
| `colesce`         |             |         |
| `colescelist`     |             |         |
| `compact`         |             |         |
| `concat`          |             |         |
| `contains`        |             |         |
| `distinct`        |             |         |
| `element`         |             |         |
| `flattern`        |             |         |
| `index`           |             |         |
| `keys`            |             |         |
| `len`             |             |         |
| `lookup`          |             |         |
| `matchkeys`       |             |         |
| `merge`           |             |         |
| `one`             |             |         |
| `range`           |             |         |
| `reverse`         |             |         |
| `setintersection` |             |         |
| `setproduct`      |             |         |
| `setsubtract`     |             |         |
| `setunion`        |             |         |
| `slice`           |             |         |
| `sort`            |             |         |
| `sum`             |             |         |
| `transpose`       |             |         |
| `values`          |             |         |
| `zipmap`          |             |         |

### Encoding Functions

| Function       | Description | Example |
|----------------|-------------|---------| 
| `base64decode` |||
| `base64encode` |||
| `csvdecode`    |||
| `jsondecode`   |||
| `urlencode`    |||

### Filesystem Functions

| Function     | Description | Example |
|--------------|-------------|---------|
| `abspath`    |||
| `dirname`    |||
| `pathexpand` |||
| `basename`   |||
| `file`       |||
| `fileexists` |||
| `filebase64` |||

### Date/Time Functions

| Function          | Description | Example |
|-------------------|-------------|---------|
| `formatdate`      |             |         |
| `formatdatetime`  |             |         |
| `currentdate`     |             |         |
| `currenttime`     |             |         |
| `datetime`        |             |         |
| `dayfromdate`     |             |         |
| `dayfromdatetime` |             |         |
| `datepart`        |             |         |
| `timezeon`        |             |         |
| `plaintimestamp`  |             |         |
| `timeadd`         |             |         |
| `timecmp`         |             |         |
| `timestamp`       |             |         |

### Hash and Cryptographic Functions

| Function       | Description | Example |
|----------------|-------------|---------|
| `base64sha256` |||       
| `base64sha512` |||       
| `bcrypt`       |||       
| `filemd5`      |||       
| `filesha1`     |||
| `filesha256`   |||
| `filesha512`   |||
| `md5`          |||
| `sha1`         |||
| `sha256`       |||
| `sha512`       |||
| `uuid`         |||
| `uuidv5`       |||

### Type Conversion Functions

| Function   | Description | Example |
|------------|-------------|---------|
| `can`      |||
| `tobool`   |||
| `tolist`   |||
| `tomap`    |||
| `tonumber` |||
| `toset`    |||
| `tostring` |||

### AWS Functions 

| Function | Description                                                 | Example                                  |
|----------|-------------------------------------------------------------|------------------------------------------|
| `awsssm` | Read a ParameterStore param from the given profile and path | `awsssm("default", "/rest/db/username")` |
|          |                                                             |                                          |

### XML Functions

| Function | Description | Example |
|----------|-------------|---------|
|          |             |         |
|          |             |         |
|          |             |         |
