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

Note: **Whenever you want to read about something in go just search `go doc fmt Println`**

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

### Simple CLI based project (Todo's)

- we can add , view , delete , mark complete task
- All these will be done by CLI itself
- We can add simple and deadline task

```go
package main

import "fmt"

func main() {
	var task_name string
	fmt.Println("Enter the task")

	fmt.Scanf("%s", &task_name)

	fmt.Println("The task you entered is : ", task_name)

}
```

- lets ask user if its a simple task or deadline task and then we will aks for the task itself

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"

	fmt.Println("Enter the task type ")

	fmt.Scanf("%q", &task_type)

	if task_type == SIMPLE_TASK {
		fmt.Println("Enter the simple task")
		fmt.Scanf("%q", &task_name)

		fmt.Println("Your simple task is :", task_name)
	} else if task_type == DEADLINE_TASK {
		fmt.Println("Enter the de adline task")
		fmt.Scanf("%q", &task_name)

		fmt.Println("Your deadline task is :", task_name)
	} else {
		fmt.Println("Invalid i/p")
	}

}
```

- we can use switch cases for this

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"

	fmt.Println("Enter the task type ")

	fmt.Scanf("%s", &task_type)

	switch task_type {
	case SIMPLE_TASK:
		fmt.Println("Enter the simple task")
		fmt.Scanf("%s", &task_name)

		fmt.Println("Your simple task is :", task_name)

	case DEADLINE_TASK:
		fmt.Println("Enter the deadline task")
		fmt.Scanf("%s", &task_name)

		fmt.Println("Your deadline task is :", task_name)
	default:
		fmt.Println("Invalid i/p")
	}

}
```

- Here we don't need to add break statement , also we can simplify this as well

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"

	fmt.Println("Enter the task type ")

	fmt.Scanf("%s", &task_type)

	switch task_type {
	case SIMPLE_TASK, DEADLINE_TASK:
		fmt.Println("Enter your", task_type)
		fmt.Scanf("%s", &task_name)
		fmt.Printf("Your %s is %s", task_type, task_name)

	default:
		fmt.Println("Invalid i/p")
	}

}
```

- Lets say we want to use loop here

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"
	const EXIT string = "exit"

	for {
		fmt.Printf("Enter the task type(%s , %s)  or %s to quit\n", SIMPLE_TASK, DEADLINE_TASK, EXIT)

		fmt.Scanf("%s", &task_type)

		switch task_type {
		case SIMPLE_TASK, DEADLINE_TASK:
			fmt.Println("Enter your", task_type)
			fmt.Scanf("%s", &task_name)
			fmt.Printf("Your %s is %s\n", task_type, task_name)

		case EXIT:
			return

		default:
			fmt.Println("Invalid i/p")
		}
	}

}
```

### Arrays in Go

- Basic initialization of arrays

```go
package main

import "fmt"

func main() {
	var tasks [10]string = [10]string{"hello", "world"}
	fmt.Println(tasks)
}
```

- we can use shorthand operator as well

```go
tasks := [10]string{"hello", "world"}
```

- here this ellipsis tells the length which we initialize

```go
tasks := [...]string{"hello", "world"}
fmt.Println(tasks)
fmt.Println(len(tasks))
fmt.Println(cap(tasks))
```

```go
tasks := [...]string{"hello", "world"}
fmt.Println(tasks)
fmt.Println(len(tasks))
fmt.Println(cap(tasks))

var new_tasks [10]string = [10]string{"hello", "world"}
fmt.Println(new_tasks)
fmt.Println(len(new_tasks))
fmt.Println(cap(new_tasks))

fmt.Println(new_tasks[1])
```

- Some usage of iteration over array

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	//var tasks [10]string = [10]string{"hello", "world"}
	//tasks := [10]string{"hello", "world"}
	tasks := [...]string{"hello", "world"}
	fmt.Println(tasks)
	fmt.Println(len(tasks))
	fmt.Println(cap(tasks))

	var new_tasks [10]string = [10]string{"hello", "world"}
	fmt.Println(new_tasks)
	fmt.Println(len(new_tasks))
	fmt.Println(cap(new_tasks))

	fmt.Println(new_tasks[1])

	for i := 0; i < len(new_tasks); i++ {
		new_tasks[i] = "task : " + strconv.Itoa(i)
	}

	for i := 0; i < len(new_tasks); i++ {
		fmt.Println(new_tasks[i])
	}
}
```

- now coming back to our old tasks cli tool we can use array to store tasks there as well

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"
	const EXIT string = "exit"
	const VIEW_TASKS = "view_tasks"

	var tasks [10]string

	idx := 0

	for {
		fmt.Printf("Enter the task type(%s , %s) , %s  or %s to quit\n", SIMPLE_TASK, DEADLINE_TASK, VIEW_TASKS, EXIT)

		fmt.Scanf("%s", &task_type)

		switch task_type {
		case SIMPLE_TASK, DEADLINE_TASK:
			fmt.Println("Enter your", task_type)
			fmt.Scanf("%s", &task_name)
			fmt.Printf("Your %s is %s\n", task_type, task_name)
			tasks[idx] = task_name
			idx++

		case VIEW_TASKS:
			for i := 0; i < len(tasks); i++ {
				fmt.Println(tasks[i])
			}

		case EXIT:
			return

		default:
			fmt.Println("Invalid i/p")
		}
	}

}
```

### Slices in go

- Here we can slice an array from one index to another
- Also from the index where we slice the new array also points to the same memory reference from where it was sliced
- so we can see here the number 3 at position index 1 and position index 0 of s array will point to same memory address
- also the capacity will be till the last index of the array from where it was sliced

```go
package main

import "fmt"

func main() {
	primes := [6]int{2, 3, 5, 7, 11, 13}

	var s []int = primes[1:4]
	fmt.Println(s)
	fmt.Println(len(s)) //3
	fmt.Println(cap(s)) //5

	primes[1] = 22
	fmt.Println(s) // [22 5 7]
	fmt.Println(len(s)) //3
	fmt.Println(cap(s)) //5
}
```

### Append in slices

- if element can be inserted in an underlying array (if there is capacity) then keep adding in the same
- If the capacity is exceeded :
  - creates a new array with 2x the capacity of the original slice

```go
package main

import "fmt"

func main() {
	// primes := [6]int{2, 3, 5, 7, 11, 13}

	// var s []int = primes[1:4]
	// fmt.Println(s)
	// fmt.Println(len(s)) //3
	// fmt.Println(cap(s)) //5

	// primes[1] = 22
	// fmt.Println(s)
	// fmt.Println(len(s)) //3
	// fmt.Println(cap(s)) //5

	tasks := [5]string{"task1", "task2", "task3", "task4", "task5"}
	var sliced_task []string = tasks[1:3]

	fmt.Println(tasks)
	fmt.Println(sliced_task)
	fmt.Println(len(sliced_task))
	fmt.Println(cap(sliced_task))

	fmt.Println()

	sliced_task = append(sliced_task, "taskNew")
	fmt.Println(tasks)
	fmt.Println(sliced_task)
	fmt.Println(len(sliced_task))
	fmt.Println(cap(sliced_task))

	fmt.Println()

	sliced_task = append(sliced_task, "taskNew")
	fmt.Println(tasks)
	fmt.Println(sliced_task)
	fmt.Println(len(sliced_task))
	fmt.Println(cap(sliced_task))

	fmt.Println()

	sliced_task = append(sliced_task, "taskNew")
	fmt.Println(tasks)
	fmt.Println(sliced_task)
	fmt.Println(len(sliced_task))
	fmt.Println(cap(sliced_task))

	fmt.Println()

	sliced_task = append(sliced_task, "taskNew")
	fmt.Println(tasks)
	fmt.Println(sliced_task)
	fmt.Println(len(sliced_task))
	fmt.Println(cap(sliced_task))

	fmt.Println()

}
```

- the output of the above code is something like

```go
[task1 task2 task3 task4 task5]
[task2 task3]
2
4

[task1 task2 task3 taskNew task5]
[task2 task3 taskNew]
3
4

[task1 task2 task3 taskNew taskNew]
[task2 task3 taskNew taskNew]
4
4

[task1 task2 task3 taskNew taskNew]
[task2 task3 taskNew taskNew taskNew]
5
8

[task1 task2 task3 taskNew taskNew]
[task2 task3 taskNew taskNew taskNew taskNew]
6
8
```

- Here we can see its created a 2x Array as well and a new one
- This append function will always return me the slice
- There are some more things here like garbage collector , deleting something from a slice

- Now we can make use of the append in our todo cli app

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"
	const EXIT string = "exit"
	const VIEW_TASKS = "view_tasks"

	var tasks []string

	for {
		fmt.Printf("Enter the task type(%s , %s) , %s  or %s to quit\n", SIMPLE_TASK, DEADLINE_TASK, VIEW_TASKS, EXIT)

		fmt.Scanf("%s", &task_type)

		switch task_type {
		case SIMPLE_TASK, DEADLINE_TASK:
			fmt.Println("Enter your", task_type)
			fmt.Scanf("%s", &task_name)
			fmt.Printf("Your %s is %s\n", task_type, task_name)
			tasks = append(tasks, task_name)

		case VIEW_TASKS:
			for i := 0; i < len(tasks); i++ {
				fmt.Println(tasks[i])
			}

		case EXIT:
			return

		default:
			fmt.Println("Invalid i/p")
		}
	}

}
```

- Now we don't need to manage the length of the tasks array and go will manage that internally

- there is a clearer way too loop on something like this

```go
for i := 0; i < len(tasks); i++ {
	fmt.Println(tasks[i])
}
```

```go
for index, element := range tasks {
	fmt.Println(index, element)
}
```

### Maps in go

- This is basically key value pair
- Some operation are very efficient

- We will get the below error

```go
var complete_status map[int]bool
fmt.Println(complete_status)
complete_status[1] = true
fmt.Println(complete_status
```

- This will basically create a nil map

map[]
panic: assignment to entry in nil map

goroutine 1 [running]:
main.main()
/Users/shaksham/Documents/Personal/Learning/go/w1/main.go:17 +0x94
exit status 2

- to solve this and create an empty map we can make use of `make`

```go
var complete_status map[int]bool = make(map[int]bool)
fmt.Println(complete_status)
complete_status[1] = true
fmt.Println(complete_status
```

- Now the output will be

```
map[]
map[1:true]
```

- With maps we can have only unique keys

- We can iterate maps using same range

```go
for key, value := range complete_status {
		fmt.Println(key, value)
}
```

```go
package main

import "fmt"

func main() {
	var task_type, task_name string

	const SIMPLE_TASK string = "simple_task"
	const DEADLINE_TASK string = "deadline_task"
	const EXIT string = "exit"
	const VIEW_TASKS = "view_tasks"
	const COMPLETE_TASK = "complete"
	const VIEW_COMPLETED_TASK = "VIEW_COMPLETE"

	var tasks []string

	var complete_status map[int]bool = make(map[int]bool)
	idx := 0

	for {
		fmt.Printf("Enter the task type(%s , %s) , %s  or %s to quit\n", SIMPLE_TASK, DEADLINE_TASK, VIEW_TASKS, EXIT)

		fmt.Scanf("%s", &task_type)

		switch task_type {
		case SIMPLE_TASK, DEADLINE_TASK:
			fmt.Println("Enter your", task_type)
			fmt.Scanf("%s", &task_name)
			fmt.Printf("Your %s is %s\n", task_type, task_name)
			tasks = append(tasks, task_name)
			complete_status[idx] = false
			idx++

		case VIEW_TASKS:
			for index, element := range tasks {
				fmt.Println(index, element)
			}

		case VIEW_COMPLETED_TASK:
			for key, value := range complete_status {
				fmt.Println(key, value)
			}

		case COMPLETE_TASK:
			var task_id int
			fmt.Scanf("%d", &task_id)
			complete_status[task_id] = true

		case EXIT:
			return

		default:
			fmt.Println("Invalid i/p")
		}
	}

}
```

### Functions in go

```go
package main

import "fmt"

func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}
```

- Return and other important things in functions

```go

package main

import "fmt"

func main() {
	var line string

	line = join(",", "Sammy", "Jessica", "Drew", "Jamie")
	fmt.Println(line)

	line = join(",", "Sammy", "Jessica")
	fmt.Println(line)

	line = join(",", "Sammy")
	fmt.Println(line)
}

func join(values ...string, del string) string {
	var line string
	for i, v := range values {
		line = line + v
		if i != len(values)-1 {
			line = line + del
		}
	}
	return line
}
```

## Week 2

- Modules and Packages
- These are dependency management system in go
- Module is collection of packages

### Packages

- package are go ways of organizing code
- Packages can be imported from go registry
- packages should be focused and perform a single task
  - handling HTTP calls
  - drawing graphics etc.

### Modules

- Modules are collection of packages
- Created by having `go.mod` file at the root directory of your project
  - Can be managed by go cli
- Contains information about the project
  - Dependency , go version , package info
- All go projects have `go.mod` file

- To initialize a module we use `go mod init hosting/username/ModuleName` , eg `go mod init github.com/shaksham08/temp_mod`
- This will create a go mod file as well

```go
module github.com/shaksham08/temo_go_mod

go 1.22.0
```

- Now we try to add a new package from go `https://pkg.go.dev/github.com/sirupsen/logrus`

```go
package main

import (
	log "github.com/sirupsen/logrus"
)

func main() {
	log.WithFields(log.Fields{
		"animal": "walrus",
		"number": 1,
		"size":   10,
	}).Info("A walrus appears")
}
```

- Now to install the package locally we need to run the command `go get github.com/sirupsen/logrus`

- Now our go mod file is

```go
module github.com/shaksham08/temo_go_mod

go 1.22.0

require github.com/sirupsen/logrus v1.9.3

require golang.org/x/sys v0.0.0-20220715151400-c0bba94af5f8 // indirect
```

- We can run `go mod tidy` to always create latest version of mod file

- Now coming to **packages** , here is the folder structure for the same

```
go/
┣ constants/
┃ ┗ constants.go
┣ pkg/
┃ ┗ api/
┃   ┗ api.go
┣ go.mod
┣ go.sum
┗ main.go
```

- Coming to `constants.go` file

```go
package constants

var (
	LOG_LEVEL = "info"
)
```

- Now coming to `api.go`

```go
package api

import (
	"fmt"

	constants "github.com/shaksham08/temo_go_mod/constants"
)

func CallApi() {
	fmt.Println("Calling API.....")
	fmt.Println("LOG LEVEL is " + constants.LOG_LEVEL)
}
```

- Now `main.go`

```go
package main

import (
	"github.com/shaksham08/temo_go_mod/pkg/api"
	log "github.com/sirupsen/logrus"
)

func main() {
	log.WithFields(log.Fields{
		"animal": "walrus",
		"number": 1,
		"size":   10,
	}).Info("A walrus appears")

	api.CallApi()
}
```

- This is how modules , packages , import export works

**Note: This is the [basic style guide for go](https://github.com/golang-standards/project-layout) of a go project**

**Note: If you want to practice what we have learned you can go and find the Personal Finance Project here : https://github.com/shaksham08/go-accelerate.git**

**Note: We build our own command line application. But there are many frameworks/libraries that we can use to not build everything from scratch**

- One such example is Cobra -> **https://github.com/spf13/cobra**
- CLI as well -> **https://github.com/urfave/cli**

**Note: Also take sometime to go over the codebase and understand how it works**

- May be try reading this : **https://github.com/urfave/cli/blob/main/command.go**

### Go routines

- A very nice article on go routines : **https://vitalcs.substack.com/p/goroutines-under-the-hood**
- Read more about coroutines :- **https://en.wikipedia.org/wiki/Coroutine**
- Read basics on what go routines is : **https://gobyexample.com/goroutines**

- We will see hwo to create a go routine in go , lets consider this basic program , here it runs sequentially in main thread

```go
package main

import "fmt"

func addSum(a, b int) int {
	return a + b
}

func main() {
	fmt.Println("The sum is ", addSum(1, 2))
}
```

- Now how do we run this in a go routine

```go
package main

import "fmt"

func addSum(a, b int) {
	fmt.Println("The sum is ", a+b)
}

func main() {
	go addSum(1, 2)
}
```

- now this function will run in a diff thread and not in main thread
- Here one thing to notice is on running this program we don't see any output
- We're using goroutines with go addSum(1, 2) to execute the addSum function concurrently. However, when a Go program exits, it doesn't wait for other goroutines to finish. Since our main function completes execution immediately after spawning the goroutine, the program ends before the goroutine has a chance to execute fmt.Println.
- To ensure that we can see the output in the console, we can use synchronization mechanisms like **channels** or wait groups to wait for the goroutine to finish before the program exits
- We will read more about channels later

- We can also use `time.wait` for this, please note this is not correct way we are just using this temporary

```go
package main

import (
	"fmt"
	"time"
)

func addSum(a, b int) {
	fmt.Println("The sum is ", a+b)
}

func main() {
	go addSum(1, 2)
	time.Sleep(1 * time.Second)
}
```

- Now lets see this code

```go
package main

import (
	"fmt"
	"time"
)

func addSum(a, b int) {
	fmt.Println("The sum is ", a+b)
}

func main() {
	for i := 0; i < 10; i++ {
		go addSum(1, i)
	}
	time.Sleep(5 * time.Second)
}
```

- Here we are telling our main thread to wait for 5 seconds until all go routines is finished. Note that we are assuming that in 5s this all go routines will finish

- There is one thing to note here is in the output

```
The sum is  4
The sum is  10
The sum is  8
The sum is  9
The sum is  5
The sum is  6
The sum is  2
The sum is  1
The sum is  3
The sum is  7
```

- We can see the order is different , this is because we cannot guarantee which go routines will finish in which order
- The scheduler of the Go runtime decides when each goroutine runs, and it can vary based on factors like CPU availability and other concurrent operations

- Here's why the output order seems random:

1. Concurrency: When we launch multiple goroutines, they can execute concurrently, meaning they may overlap in execution time. The order in which they're executed is determined by the scheduler, which may not follow the sequential order of the loop.

2. Goroutine Scheduling: The Go runtime's scheduler is free to schedule goroutines in any order it sees fit, based on factors like available CPU resources and other runtime conditions. This means that even though you start them in order in your loop, they might not execute in the same order.

- There is one more way of creating a go routine i.e using anonymous functions

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	go func() {
		fmt.Println("hello world")
	}()
	time.Sleep(5 * time.Second)
}
```

### WaitGroups

- waitGroups is primitive that is used to synchronize go routines , allows go routines/ execution to wait for one another

- now we saw `time.Sleep(5 * time.Second)` is not the best way to wait, we have better way to wait around this when main thread ends

- lets consider this example

```go
package main

import (
	"fmt"
	"time"
)

func printAddress() {
	fmt.Println("This is address")
}

func printName() {
	go printAddress()
	fmt.Println("This is name")
}

func main() {
	go printName()
	time.Sleep(5 * time.Second)
}
```

- the output of this is

```
This is name
This is address
```

- The order in which go routines is not deterministic , the above output can swap as well

- we can make use of waitGroups

```go
package main

import (
	"fmt"
	"sync"
)

func printAddress() {
	fmt.Println("This is address")
}

func printName(wg *sync.WaitGroup) {
	go printAddress()
	fmt.Println("This is name")
	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	wg.Add(1) // setting the counter to 1 and also this expects one go routine
	go printName(&wg)
	wg.Wait()

}
```

- Another example where we are waiting for 2 go routines

```go
package main

import (
    "fmt"
    "sync"
)

func main() {
    var wg sync.WaitGroup

    wg.Add(2) // Expecting two goroutines

    // Launching first goroutine
    go func() {
        fmt.Println("First goroutine")
        wg.Done() // Signal completion explicitly
    }()

    // Launching second goroutine
    go func() {
        fmt.Println("Second goroutine")
        wg.Done() // Signal completion explicitly
    }()

    // Wait for all goroutines to finish
    wg.Wait()
    fmt.Println("All goroutines finished")
}
```

### Channels

- Channels in Go are a powerful construct for communicating and synchronizing between goroutines. They provide a way for goroutines to send and receive values to and from each other, allowing for safe communication and coordination.

1. Typed Communication: Channels can be typed, meaning they can only transmit values of a specific data type. For example, you can have a channel of type int, string, or even a custom struct.

2. Synchronization: Channels are inherently synchronized. When a value is sent into a channel, the sending goroutine blocks until another goroutine receives the value from the channel. This ensures safe communication between goroutines.

3. Buffered Channels: Channels can be buffered, meaning they can hold a limited number of values without a corresponding receiver. This allows goroutines to continue sending values to the channel without blocking until the buffer is full.

4. Unidirectional Channels: Channels can be either bidirectional (default) or unidirectional, meaning they can only be used for sending or receiving values.

```go
package main

import (
    "fmt"
)

func sender(ch chan<- int) {
    for i := 0; i < 5; i++ {
        ch <- i // Send value into the channel
    }
    close(ch) // Close the channel when done sending
}

func receiver(ch <-chan int) {
    for value := range ch {
        fmt.Println("Received:", value) // Receive value from the channel
    }
}

func main() {

    ch := make(chan int) // Create a new channel
	// var ch chan int -> we can also use this keyword to create a channel

    go sender(ch)   // Start sender goroutine
    go receiver(ch) // Start receiver goroutine

    // Wait for both goroutines to finish
    var input string
    fmt.Scanln(&input)
}
```

- Basically we have two go routines G1 and G2 then how do we communicate
- GR1 -> ch(int) <- GR2

- By default communication is bidirectional only
- Lets take another easy example as well

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	i := 100
	ch <- i
	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int)

	wg.Add(1)
	go produce(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- When we pass channel , this line ch <- i will be blocked untile this channel is consumed by other go routine.
- So go routine knows that this is not being consumed so it goes into deadlock situation and throws error
- So whenever we are producing we need to consume

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	i := 100
	ch <- i
	wg.Done()
}

func consume(wg *sync.WaitGroup, ch chan int) {
	i := <-ch
	fmt.Println(i)
	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int)

	wg.Add(2)
	go produce(&wg, ch)

	go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- This is how simple un buffered channel is created

- Lets see what are buffered channels

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	// fmt.Println("Producing...")
	i := 100
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	fmt.Println(len(ch))
	// fmt.Println("Produced", i)
	wg.Done()
}

// func consume(wg *sync.WaitGroup, ch chan int) {
// 	fmt.Println("Waiting for data...")
// 	i := <-ch
// 	fmt.Println("Consumed ", i)

// 	wg.Done()
// }

func main() {
	var wg sync.WaitGroup
	ch := make(chan int, 5)

	wg.Add(1)
	go produce(&wg, ch)

	// go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- The above programs runs very fine , also if we try to pass one more data to channel it will give error now because we only have 5 buffers

- Similary for consumer we can see it will not be deadlock situation

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	// fmt.Println("Producing...")
	i := 100
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	fmt.Println(len(ch))
	// fmt.Println("Produced", i)
	wg.Done()
}

func consume(wg *sync.WaitGroup, ch chan int) {
	fmt.Println("Waiting for data...")
	i := <-ch
	fmt.Println("Consumed ", i)

	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int, 5)

	wg.Add(2)
	go produce(&wg, ch)

	go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- Now lets add one more data to channel

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	// fmt.Println("Producing...")
	i := 100
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	fmt.Println(len(ch))
	ch <- i // here it will block and see for consumer
	// ch <- i // this will create panic
	// fmt.Println("Produced", i)
	wg.Done()
}

func consume(wg *sync.WaitGroup, ch chan int) {
	fmt.Println("Waiting for data...")
	i := <-ch
	fmt.Println("Consumed ", i)

	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int, 5)

	wg.Add(2)
	go produce(&wg, ch)

	go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}

```

- This would also not give error because the extra data that we passed got consumed by the consumer

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	// fmt.Println("Producing...")
	i := 100
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i

	close(ch)
	wg.Done()
}

func consume(wg *sync.WaitGroup, ch chan int) {
	fmt.Println("Waiting for data...")
	for value := range ch {
		fmt.Println("Received:", value) // Receive value from the channel
	}

	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int, 5)

	wg.Add(2)
	go produce(&wg, ch)

	go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- Checkout this code as well

```go
package main

import (
	"fmt"
	"sync"
)

func produce(wg *sync.WaitGroup, ch chan int) {
	// fmt.Println("Producing...")
	i := 100
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	ch <- i
	close(ch)
	fmt.Println(len(ch))
	wg.Done()
}

func consume(wg *sync.WaitGroup, ch chan int) {
	fmt.Println("Waiting for data...")
	for i := 0; i < 7; i++ {
		i, ok := <-ch
		fmt.Println("Received:", i, "ok ", ok)
	}
	i, ok := <-ch
	fmt.Println("Received:", i, "ok ", ok)

	wg.Done()
}

func main() {
	var wg sync.WaitGroup
	ch := make(chan int, 5)

	wg.Add(2)
	go produce(&wg, ch)

	go consume(&wg, ch)

	wg.Wait()
	fmt.Println("All goroutines finished")
}
```

- Here false value means that the channel is closed now

**Note: Some pre reads [Free code camp](https://www.freecodecamp.org/news/concurrent-programming-in-go/)**
**Note: check this out as well : https://github.com/shaksham08/go-accelerate/blob/main/goroutines.go**
