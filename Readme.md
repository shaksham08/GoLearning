# Go learning

## Week 1

Below are some of the pre reads before starting Go , these basically explains the basic understanding of why Go was created and a glimpse into its origins.

- Simplicity is Complicated by Rob Pike (one of the creators of Go): <a href="https://www.youtube.com/watch?v=rFejpH_tAHM">Watch the video</a>
- Less is more by Rob Pike: <a href="https://www.google.com/url?q=https%3A%2F%2Fcommandcenter.blogspot.com%2F2012%2F06%2Fless-is-exponentially-more.html&sa=D&sntz=1&usg=AOvVaw1Qeto1xW0n9WY_X3Izr0xh">Read the article</a>

Some important points :-

- Go is known best for its simplicity.
- it lets programmers in general to write a code in a single pattern only. i.e everyone will be using simple for look itself for looping as there is no map , filter etc which in turn makes debugging very easy.
- More of this can be explored in the above pre reads.

Lets start with basic program in go

```go
// package is just a way of organizing code
package main

import "fmt"

// hello world program

func main() {
	fmt.Println("Hello world")
}
```

Note: **Whenver you want to read about something in go just search `go doc fmt Println`**

- To run the above program just run `go run main.go`

- This main function is special like other main function in other programming language
- This is the entry point of the program

To add comments we just use

```go
// single line comment

/*
This is a multi line comment
*/
```

### Data types

- Go is a statically typed language
- go has concept of types
- In go we can expicitly declare the type or it is infered by the compiler , but once set it cannot be changes

```go
var i int = 10;
k := 10;
```

- this is how we set an integer
- there are other as well float64, float32 , boolean etc

```go
package main

import "fmt"

func main() {
	bool_var := true
	if bool_var {
		fmt.Println("True")
	}
	fmt.Println("Hello world")
}
```

- the syntax to declare a variable is `var variable_name data_type = value `

```go
package main

import "fmt"

func main() {
	var a int = 10
	var b float64 = 2.0
	var c bool = false
	var d string = "string"
	fmt.Println(a, b, c, d)
}
```

- there is another way as well to define the variable

```go
package main

import "fmt"

func main() {
	var a, b int
	a = 10
	b = 20
	var c, d int = 40, 50

	fmt.Println(a, b, c, d)
}
```

- the shorted way to create a variable in go is

```go
s := "this is a string"
```

- other way to define multiple variables is

```go
var (
		s string = "string"
		b int    = 10
	)
```

### Printing in go

- for printing we use fmt package

```go
package main

import "fmt"

func main() {
	name := "shaksham"
	fmt.Printf("%v\n", name)
	fmt.Printf("%d\n", 10)
	fmt.Printf("%0.2f\n", 1.234566)
}
```

- using format specifiers gives more readability while someone is reading the code
- Also it gives more control over printing

### Variable scoping

- in go we can use `{ }` for declaring a block

```go
package main

import "fmt"

func main() {
	name := "Anne"
	{
		last_name := "Brown"
		fmt.Println(name, last_name)
	}
	fmt.Println(name)
}
```

- Here we cannot access `last_name` outside the block but we can access `name` insights the block
- We wont be using this much , but we will be seeing this as local variable and global variables
- A local variables are variables declared insights insights loops , functions etc.

```go
package main

import "fmt"

var name string = "Anne"

func main() {
	name := "Shaksham"
	{
		last_name := "Brown"
		fmt.Println(name, last_name)
	}
	fmt.Println(name)
}
```

### default values

```go
package main

import "fmt"

var name string = "Anne"

func main() {
	var (
		a int
		b bool
		c string
		d float64
	)
	fmt.Printf("%d\n%t\n%q\n%0.00f\n", a, b, c, d)
}
```

- the output is

```
0
false
""
0
```

### User Input

```go
package main

import "fmt"

func main() {
	var name string
	fmt.Println("Enter you name")
	n, err := fmt.Scanf("%q", &name)
	fmt.Println(name)
	fmt.Println(n, err)
}
```

- output is

```bash
Enter you name
"shaksham sinha"
shaksham sinha
1 <nil>
```

### Typecasting

- we can convert data from one type to another using typecasting but this does not make sure that our data will remain intact.

```go
package main

import "fmt"

func main() {
	var a int = 20
	var b float64 = float64(a)
	fmt.Printf("%0.02f\n", b)
}
```

- there is a package called as `strconv`
- this is used to convert from integer to string or string to integer

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var a int = 20
	var s string = strconv.Itoa(a)
	d, err := strconv.Atoi(s)
	fmt.Println(s, d, err)
}
```

### Constants in go

- Untyped constants
  - `const age = 10`
- Typed constants

  - `const name string= "name"`

- constants cannot be re initialized again , it will remain same throughout the program
- shorthand operator will not work with constant

### Operators in go

- below are the comparison operators in go

```go
a := 10
b := 20

fmt.Println(a == b)
fmt.Println(a != b)
fmt.Println(a > b)
fmt.Println(a < b)
fmt.Println(a >= b)
fmt.Println(a <= b)
```

- similarly we have arithmetic operator as well
- there are other logical operator as well - `&&` , `||` and `!`

- we also have assignment operator eg `a += b`

- we also have bit wise operator which performs operation at bit level i.e `& , OR - | , XOR - ^ , >> , <<`
