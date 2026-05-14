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

| Function          | Description                                                                                                                                | Example                                                                                                                                                          |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `appendifmissing` | Appends a suffix to the end of the string if not present                                                                                   | `appendifmissing("abc","xyz","") = "abc"`, `appendifmissing("abcXYZ", "xyz", "mno") = "abcXYZ"`                                                                  |
| `can`             | Evaluate of the expression can be evaluated                                                                                                | `can(pi()) = true`, `can(pii()) = false` Note: no standard library function called `pii().                                                                       |
| `chomp`           | Remove new line character(s) from end of a string                                                                                          | `chomp("hello\n\n") = hello`, `chomp("hello\r\n") = hello`                                                                                                       |
| `chop`            | Remove the last character from a string                                                                                                    | `chop("hello") = hell`, `chop("\n") = ""`, `chop("\r\n") = ""`                                                                                                   
| `center`          | Centers a string in larger string of size `size` using a space character(` `)                                                              | `center("ab", 4) = "  ab  "`, `center("abcd", 2) = "abcd"`, `center("a", 4) = " a  "`                                                                            |
| `empty`           | Check if a string contains text                                                                                                            | `empty("") = true`, `empty("hello") = false`                                                                                                                     |
| `endswith`        | Tests if a string end with a specified suffix                                                                                              | `endswith("abcdef","def") = true`, `endswith("ABCDEF", "def") = false`, `endwith("ABCDEF", upper("def")) = true`                                                 |
| `format`          | Produce a formatted string according to the format specifier                                                                               | `format("hello in Sinhala: , %s!", "ආයුබෝවන්") = hello in Sinhala: ආයුබෝවන්!`, `format("Hello, %s!", var.greeting) = Hello, there!`                              |
| `formatlist`      | Produces a list of strings by formatting a number of other values according to a specification string                                      | `formatlist("Hello, %s!", ["Valentina", "Ander"]) = ["Hello, Valentina!", "Hello, Ander!"]`                                                                      |
| `indent`          | Add specified number of spaces in a multi-line funciton, except first line                                                                 | `indent(2, "\nhello world")`                                                                                                                                     |
| `isalpha`         | Check if the input contains only unicode letters                                                                                           | `isalpha("abc") = true`, `islapha("ab2c") = false`, `isalpha("ab-c") = false`                                                                                    |
| `isnumeric`       | Check if the input contains only unicode digits                                                                                            | `isnumeric("123") = true`, `isnumeric("12 3") = false`, `isnumeric("12.3") = false`                                                                              |
| `iswhitespace`    | Check if the input contaons only unicode spaces `'\t', '\n', '\v', '\f', '\r', ' ', U+0085 (NEL), U+00A0 (NBSP)`                           | `iswhitespace("") = true`, `iswhitespace("\t") = true`                                                                                                           |
| `lastindexof`     | Check the last index of the occurence of a substring ina string                                                                            | `lastindexof("go gopher", "go") = `, `lastindexof("go gopher", "rodent") = -1`                                                                                   |
| `join`            | Produce a string concatinating all the elements of the speficied list with the seperator                                                   | `join(" ", ["hello", "world"]) = hello world`                                                                                                                    |
| `lower`           | Convert unicode string to lowercase                                                                                                        | `lower("HELLO") = "hello"`                                                                                                                                       |
| `leftpad`         | Left pad a string with specified string with number of time(s)                                                                             | `leftpad("bat", 5, "yz")  = "yzbat"`, `leftpad("bat", 3, "yz")  = "bat"`                                                                                         |
| `regex`           | Apply the regex and return the matching string                                                                                             | `regex("[a-z]+", "53453453.345345aaabbbccc23454") = aaabbbccc`                                                                                                   |
| `regexall`        | Apply the regex and return the list of matching strings                                                                                    | `regexall("[a-z]+", "1234abcd5678efgh9") = ["abcd", "efgh"]`                                                                                                     |
| `replace`         | Replace all occureces of the given substring                                                                                               | `replace("1 + 2 + 3", "+", "-") = "1 - 2 - 3"`                                                                                                                   |
| `reverse`         | Reverse an unicode string                                                                                                                  | `reverse("dlrow olleh") = "hello world"`                                                                                                                         |
| `repeat`          | Returns padding using the specified delimiter repeated to a given length                                                                   | `repeat("e", 0)  = "", repeat("e", 3)  = "eee", repeat("e", -2) = ""`                                                                                            |
| `resplit`         | Split a string into a list of substrings based on the specified regular expression pattern and limit by the number (-1 for all substrings) | `resplit("a b c", "\s", 2) = ["a", "b"]`, `resplit("2006-12-25T12:15:00", "[\-T:]", -1) = ["2006", "12", "25", "12", "15", "00"]`, `resplit("a,xb,xc", ", \|,x")` |
| `reverse`         | Reverse an unicode string                                                                                                                  | `reverse("dlrow olleh") = "hello world"`                                                                                                                         |
| `rightpad`        | Right pad a string with specified string with number of time(s)                                                                            | `rightpad("bat", 5, "yz")  = "batyz"`, `rightpad("bat", 3, "yz")  = "bat"`                                                                                       |
| `rotate`          | Rotate a string to given number of shifts (circular shift)                                                                                 | `rotate("abcdefg", 0)   = "abcdefg"`, `rotate("abcdefg", 2)   = "fgabcde"`                                                                                       |  
| `split`           | Produces a list by splitting a given string using the given separator                                                                      | `split(",", "foo,bar,baz") = ["foo", "bar", "baz"]`                                                                                                              |
| `startswith`      | Check if the string starts with the provided prefix                                                                                        | `startswith("abcdef", "abc") = true`, `startswith("ABCDEF", "abc") = false`, `startswith("ABCDEF", upper("abc")) = true`                                         |
| `strcontains`     | Check if second argument is inside the first argument                                                                                      | `strcontains("hello world", "wor") = true`, `strcontains("hello world", "wod") = false`                                                                          |
| `strlen`          | Returns the length of the unicode string                                                                                                   | `strlen("HELLO") = 5`                                                                                                                                            |
| `swapcase`        | Swaps the case of a string by chaning upper to lower and vice versa                                                                        | `swapcase("The dog has a BONE") = "tHE DOG HAS A bone"`                                                                                                          |
| `substr`          | Extract a substring from the given string                                                                                                  | `substr("hello world", 1, 4) = ello`, `substr("🤔🤷", 0, 1) = 🤔`                                                                                                |
| `substrbefore`    | Get the substring before the last occurrence of a seprator                                                                                 | `substrbefore("abcba", "b") = "abc"`, `substrbefore("abc", "c")   = "ab"`                                                                                        |
| `substrafter`     | Get the substring after the last occurrence of a seprator                                                                                  | `substrafter(" abc", 32) = "abc"`, `substrafter("abcba", "b") = "cba"`                                                                                           |
| `substrbetween`   | Gets the String that is nested in between two Strings. Only the first match is returned                                                    | `substrbetween("yabczyabcz", "y", "z")   = "abc"`                                                                                                                |
| `templatestring`  | Renders a string as a template using a set of variables                                                                                    |                                                                                                                                                                  |
| `title`           | Conver first letter of each word to uppercase                                                                                              | `title("hello world") = Hello World`                                                                                                                             |
| `trim`            | Remove the given characters from the string from the start and end                                                                         | `trim("?!hello?!", "!?") = hello`                                                                                                                                |
| `trimprefix`      | Removes the specified prefix from the start of the given string, but only once                                                             | `trimprefix("helloworld", "hello") = world`                                                                                                                      |
| `trimspace`       | Removes any space characters from the start and end of the given string                                                                    | `trimspace("  hello\n\n") = "hello"`                                                                                                                             |
| `trimsuffix`      | Removes the specified suffix from the end of the given string, but only once, even if the suffix appears multiple times                    | `trimsuffix("helloworld", "world") = hello`                                                                                                                      |
| `upper`           | Convert unicode string to uppercase                                                                                                        | `upper("hello") = "HELLO"`                                                                                                                                       |

### Collection Functions

| Function          | Description                                                                                                             | Example                                                                            |
|-------------------|-------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| `alltrue`         | Returns true if all elements in a given collection are true/"true"                                                      | `alltrue(["true", true]) = true`                                                   |
| `anytrue`         | Returns true if any element in a given collection is true/"true"                                                        | `anytrue([true, false]) = true`                                                    |
| `chunklist`       | Splits a list into fixed size lists                                                                                     | `chunklist(["a", "b", "c", "d", "e"], 2) = [["a, b"],["c","d], ["e"]]`             |
| `colesce`         | Takes a variable number of arguments and returns the first one that isn't empty                                         | `coalesce("a", "b") = a`, `coalesce("", "b") = b`                                  |
| `colescelist`     | Takes a variable number of list arguments and returns the first list that isn't empty                                   | ` coalescelist(["a", "b"], ["c", "d"]) = ["a", "b"]`                               |
| `compact`         | Takes a list of strings and returns a new list with any null or empty string elements removed                           | `compact(["a", "", "b", "c"]) = ["a", "b", "c"]`                                   |
| `concat`          | Takes a list of list and combines them into a single list                                                               | `concat(["a", ""], ["b", "c"]) = ["a", "", "b", "c"]`                              |
| `contains`        | Check if the the value is in the list                                                                                   | `contains(["a", "b", "c"], "a") = true`                                            |
| `distinct`        | Return a new list with duplicates removed                                                                               | `distinct(["a", "b", "a", "c", "d", "b"]) = ["a", "b", "c", "d"]`                  |
| `element`         | Retrives a single elmenet from a list                                                                                   | `element(["a", "b", "c"], 1) = "b"`                                                |
| `flattern`        | Take a list of lists and produce a single list with a flattened sequence                                                | `flatten([["a", "b"], [], ["c"]])`                                                 |
| `index`           | Find the first element index of a given value in the list                                                               | `index(["a", "b", "c"], "b") = 1`                                                  |
| `keys`            | Returns the key set from a map                                                                                          | `keys({a=1, c=2, d=3}) = ["a", "c", "d"]`                                          |
| `len`             | Returns the number of elements in a given collection                                                                    | `length(["a", "b"]) = 2`                                                           |
| `lookup`          | Retrieves the value of a single element from a map, given its key. Return the default value if key not present          | `lookup({a="ay", b="bee"}, "a", "what?") = "ay"`                                   |
| `merge`           | Merge an arbitrary number of maps or objects, and returns a single map or object that contains a merged set of elements | `merge({a="b", c="d"}, {e="f", c="z"}) = {"a" = "b", "c" = "d", "e" = "f"}`        |
| `range`           | Generate a list of numbers using a start, a limit, and a step value                                                     | `range(3) = [0, 1, 2]`, `range(1, 4) = [1, 2, 3]`, `range(1, 8, 2) = [1, 3, 5, 7]` |
| `reverse`         |                                                                                                                         |                                                                                    |
| `setintersection` |                                                                                                                         |                                                                                    |
| `setproduct`      |                                                                                                                         |                                                                                    |
| `setsubtract`     |                                                                                                                         |                                                                                    |
| `setunion`        |                                                                                                                         |                                                                                    |
| `slice`           |                                                                                                                         |                                                                                    |
| `sort`            |                                                                                                                         |                                                                                    |
| `sum`             |                                                                                                                         |                                                                                    |
| `transpose`       |                                                                                                                         |                                                                                    |
| `values`          |                                                                                                                         |                                                                                    |
| `zipmap`          |                                                                                                                         |                                                                                    |

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
