## Standard Library

IntBricks Integration Service (IIS) standard library documentation.

### Numeric Functions

| Function   | Description                                                                                                | Example                                                                |
|------------|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| `abs`      | Returns the absoute value of a value                                                                       | `abs(23) = 23`, `abs(0) = 0`                                           |
| `acos`     | Returns the arc cosine of the given value(range -1 to 1)                                                   | `acos(0.25) = 1.318116071652818`                                       |
| `add`      | Return the sum of two given numbers                                                                        | `sum(10,10) = 10`, `sum(10,-10) = 0`                                   |
| `asin`     | Return the arc sine of the given number                                                                    | `asin(0) = 0`, `asin(1) = 1.5707963267948966`                          |
| `cbrt`     | Returns the cubic root of a value                                                                          | `cbrt(27) = 3`                                                         |
| `ceil`     | Returns the closest whole number that is greater than or equal to the given value, which may be a fraction | `ceil(5) = 5`, `ceil(5.1) = 6`                                         |
| `cos`      | Returns the cosine of the given number                                                                     | `cos(0) = 1`                                                           |
| `div`      | Divide the first number by the second number                                                               | `div(10,2) = 5`, `div(30,-5) = -6`                                     |
| `floor`    | Returns the closest whole number that is less than or equal to the given value, which may be a fraction    | `floor(5) = 5`, `floor(4.9) = 4`                                       |
| `log`      | Returns the logarithm of a given number in a given base                                                    | `log(50, 10) = 1.6989700043360185`                                     |   
| `max`      | Returns the maximum from a two or more input numbers                                                       | `max(12, 54, 3) = 54`, `max([12, 54, 3]...) = 54`                      |
| `min`      | Return the minimum from a two or more input numbers                                                        | `min(12, 54, 3) = 3`, `min([12, 54, 3]...) = 3`                        |
| `mul`      | Multiple two numbers by each other                                                                         | `multiply(10,10) = 100`, `multiply(10,-10) = -100`                     |
| `parseint` | Parses a the given string represenation of an integer in the provided base and return the result           | `parseint("100", 10) = 100`, `parseint("1011111011101111", 2) = 48879` |
| `pow`      | Calcuates the expoonent, first argument to the power of second argument                                    | `pow(5, 3) = 125`                                                      |
| `pi`       | Returns the value of Pi                                                                                    | `pi() = 3.141592653589793`                                             |
| `signum`   | Determines the sign of a number, returning -1, 0, 1 for negative, zero, positive numbers respectively      | `signum(-13) = -1`, `signum(0) = 0` , `signum(13) = 1`                 |
| `sin`      | Returns the sine of a given number                                                                         | `sin(0) = 0`                                                           |
| `sub`      | Returns the difference between two given numbers                                                           | `sub(10,2) = 8`, `sub(10,20) = -10`                                    |
| `tan`      | Returns the tagnet of the given number                                                                     | `tan(1) = 1.5430806348152437`                                          |

### String Functions

| Function           | Description                                                                                                      | Example                                                                                                                             |
|--------------------|------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `appendifmissing`  | Appends a suffix to the end of the string if not present                                                         | `appendifmissing("abc","xyz","") = "abc"`, `appendifmissing("abcXYZ", "xyz", "mno") = "abcXYZ"`                                     |
| `can`              | Evaluate of the expression can be evaluated                                                                      | `can(pi()) = true`, `can(pii()) = false` Note: no standard library function called `pii().                                          |
| `chomp`            | Remove new line character(s) from end of a string                                                                | `chomp("hello\n\n") = hello`, `chomp("hello\r\n") = hello`                                                                          |
| `chop`             | Remove the last character from a string                                                                          | `chop("hello") = hell`, `chop("\n") = ""`, `chop("\r\n") = ""`                                                                      
| `center`           | Centers a string in larger string of size `size` using a space character(` `)                                    | `center("ab", 4) = "  ab  "`, `center("abcd", 2) = "abcd"`, `center("a", 4) = " a  "`                                               |
| `empty`            | Check if a string contains text                                                                                  | `empty("") = true`, `empty("hello") = false`                                                                                        |
| `endswith`         | Tests if a string end with a specified suffix                                                                    | `endswith("abcdef","def") = true`, `endswith("ABCDEF", "def") = false`, `endwith("ABCDEF", upper("def")) = true`                    |
| `format`           | Produce a formatted string according to the format specifier                                                     | `format("hello in Sinhala: , %s!", "ආයුබෝවන්") = hello in Sinhala: ආයුබෝවන්!`, `format("Hello, %s!", var.greeting) = Hello, there!` |
| `formatlist`       | Produces a list of strings by formatting a number of other values according to a specification string            | `formatlist("Hello, %s!", ["Valentina", "Ander"]) = ["Hello, Valentina!", "Hello, Ander!"]`                                         |
| `indent`           | Add specified number of spaces in a multi-line funciton, except first line                                       | `indent(2, "\nhello world")`                                                                                                        |
| `isalpha`          | Check if the input contains only unicode letters                                                                 | `isalpha("abc") = true`, `islapha("ab2c") = false`, `isalpha("ab-c") = false`                                                       |
| `isnumeric`        | Check if the input contains only unicode digits                                                                  | `isnumeric("123") = true`, `isnumeric("12 3") = false`, `isnumeric("12.3") = false`                                                 |
| `iswhitespace`     | Check if the input contaons only unicode spaces `'\t', '\n', '\v', '\f', '\r', ' ', U+0085 (NEL), U+00A0 (NBSP)` | `iswhitespace("") = true`, `iswhitespace("\t") = true`                                                                              |
| `lastindexof`      | Check the last index of the occurence of a substring ina string                                                  | `lastindexof("go gopher", "go") = `, `lastindexof("go gopher", "rodent") = -1`                                                      |
| `join`             | Produce a string concatinating all the elements of the speficied list with the seperator                         | `join(" ", ["hello", "world"]) = hello world`                                                                                       |
| `lower`            | Convert unicode string to lowercase                                                                              | `lower("HELLO") = "hello"`                                                                                                          |
| `leftpad`          | Left pad a string with specified string with number of time(s)                                                   | `leftpad("bat", 5, "yz")  = "yzbat"`, `leftpad("bat", 3, "yz")  = "bat"`                                                            |
| `regex`            | Apply the regex and return the matching string                                                                   | `regex("[a-z]+", "53453453.345345aaabbbccc23454") = aaabbbccc`                                                                      |
| `regexall`         | Apply the regex and return the list of matching strings                                                          | `regexall("[a-z]+", "1234abcd5678efgh9") = ["abcd", "efgh"]`                                                                        |
| `replace`          | Replace all occureces of the given substring                                                                     |                                                                                                                                     |
| `reverse`          | Reverse an unicode string                                                                                        | `reverse("dlrow olleh") = "hello world"`                                                                                            |
| `repeat`           |                                                                                                                  |                                                                                                                                     |
| `remove`           | Remove part of a string, if avaiable                                                                             |                                                                                                                                     |
| `reverse`          | Reverse an unicode string                                                                                        | `reverse("dlrow olleh") = "hello world"`                                                                                            |
| `reversedelimited` |                                                                                                                  |                                                                                                                                     | 
| `rightpad`         | Right pad a string with specified string with number of time(s)                                                  | `rightpad("bat", 5, "yz")  = "batyz"`, `rightpad("bat", 3, "yz")  = "bat"`                                                          |
| `rotate`           |                                                                                                                  |                                                                                                                                     |  
| `split`            |                                                                                                                  |                                                                                                                                     |
| `startswith`       |                                                                                                                  |                                                                                                                                     |
| `strcontains`      |                                                                                                                  |                                                                                                                                     |
| `strrev`           |                                                                                                                  |                                                                                                                                     |
| `swapcase`         |                                                                                                                  |                                                                                                                                     |
| `substr`           |                                                                                                                  |                                                                                                                                     |
| `substrbefore`     |                                                                                                                  |                                                                                                                                     |
| `substrafter`      |                                                                                                                  |                                                                                                                                     |
| `substrbetween`    |                                                                                                                  |                                                                                                                                     |
| `templatestring`   |                                                                                                                  |                                                                                                                                     |
| `title`            |                                                                                                                  |                                                                                                                                     |
| `trim`             |                                                                                                                  |                                                                                                                                     |
| `trimprefix`       |                                                                                                                  |                                                                                                                                     |
| `trimsuffix`       |                                                                                                                  |                                                                                                                                     |
| `trimspace`        |                                                                                                                  |                                                                                                                                     |
| `upper`            | Convert unicode string to uppercase                                                                              | `upper("hello") = "HELLO"`                                                                                                          |

### Collection Functions

| Function          | Description                                                                                   | Example                                                           |
|-------------------|-----------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| `alltrue`         |                                                                                               |                                                                   |
| `anytrue`         |                                                                                               |                                                                   |
| `chunklist`       |                                                                                               |                                                                   |
| `colesce`         |                                                                                               |                                                                   |
| `colescelist`     |                                                                                               |                                                                   |
| `compact`         | Takes a list of strings and returns a new list with any null or empty string elements removed | `compact(["a", "", "b", "c"]) = ["a", "b", "c"]`                  |
| `concat`          |                                                                                               |                                                                   |
| `contains`        | Check if the the value is in the list                                                         | `contains(["a", "b", "c"], "a") = true`                           |
| `distinct`        | Return a new list with duplicates removed                                                     | `distinct(["a", "b", "a", "c", "d", "b"]) = ["a", "b", "c", "d"]` |
| `element`         |                                                                                               |                                                                   |
| `flattern`        |                                                                                               |                                                                   |
| `index`           |                                                                                               |                                                                   |
| `keys`            |                                                                                               |                                                                   |
| `len`             |                                                                                               |                                                                   |
| `lookup`          |                                                                                               |                                                                   |
| `matchkeys`       |                                                                                               |                                                                   |
| `merge`           |                                                                                               |                                                                   |
| `one`             |                                                                                               |                                                                   |
| `range`           |                                                                                               |                                                                   |
| `reverse`         |                                                                                               |                                                                   |
| `setintersection` |                                                                                               |                                                                   |
| `setproduct`      |                                                                                               |                                                                   |
| `setsubtract`     |                                                                                               |                                                                   |
| `setunion`        |                                                                                               |                                                                   |
| `slice`           |                                                                                               |                                                                   |
| `sort`            |                                                                                               |                                                                   |
| `sum`             |                                                                                               |                                                                   |
| `transpose`       |                                                                                               |                                                                   |
| `values`          |                                                                                               |                                                                   |
| `zipmap`          |                                                                                               |                                                                   |

### Encoding Functions

| Function       | Description | Example |
|----------------|-------------|---------| 
| `base64decode` |             |         |
| `base64encode` |             |         |
| `csvdecode`    |             |         |
| `jsondecode`   |             |         |
| `urlencode`    |             |         |

### Filesystem Functions

| Function     | Description | Example |
|--------------|-------------|---------|
| `abspath`    |             |         |
| `dirname`    |             |         |
| `pathexpand` |             |         |
| `basename`   |             |         |
| `file`       |             |         |
| `fileexists` |             |         |
| `filebase64` |             |         |

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
| `base64sha256` |             |         |       
| `base64sha512` |             |         |       
| `bcrypt`       |             |         |       
| `filemd5`      |             |         |       
| `filesha1`     |             |         |
| `filesha256`   |             |         |
| `filesha512`   |             |         |
| `md5`          |             |         |
| `sha1`         |             |         |
| `sha256`       |             |         |
| `sha512`       |             |         |
| `uuid`         |             |         |
| `uuidv5`       |             |         |

### Type Conversion Functions

| Function   | Description | Example |
|------------|-------------|---------|
| `can`      |             |         |
| `tobool`   |             |         |
| `tolist`   |             |         |
| `tomap`    |             |         |
| `tonumber` |             |         |
| `toset`    |             |         |
| `tostring` |             |         |

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
