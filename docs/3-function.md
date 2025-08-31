# Functions in Go

This note explains everything about **functions** in Golang, including syntax, parameters, return values, and advanced topics.

---

## 📌 What is a Function in Go?

A **function** is a **reusable block of code** that performs a specific task. Functions help you **organize code**, **avoid repetition**, and **make programs easier to read and maintain**.

In Go, every function has:

- **A name**
- **Optional parameters** (inputs)
- **Optional return values** (outputs)
- **A body** that contains the code to execute

---

## 🔹 Function Syntax

```go
func functionName(parameterName type, ...) returnType {
    // function body
    return value
}
```

**Example:**

```go
package main

import "fmt"

// Function that adds two integers and returns the result
func add(a int, b int) int {
    return a + b
}

func main() {
    sum := add(2, 3)
    fmt.Println("Sum:", sum) // Output: Sum: 5
}
```

---

## 🔹 Key Points

### 1. Function Parameters

You can pass multiple parameters.

If consecutive parameters have the same type, you can write the type once:

```go
func multiply(a, b int) int {
    return a * b
}
```

### 2. Return Values

Functions can return multiple values:

```go
func swap(x, y string) (string, string) {
    return y, x
}
```

### 3. Named Return Values

You can name the return values in the function signature:

```go
func divide(a, b float64) (quotient float64, remainder float64) {
    quotient = a / b
    remainder = float64(int(a) % int(b))
    return
}
```

### 4. Variadic Functions

Functions can accept a variable number of arguments using `...`:

```go
func sum(numbers ...int) int {
    total := 0
    for _, n := range numbers {
        total += n
    }
    return total
}
```

### 5. Anonymous Functions

Functions can be defined without a name and assigned to a variable or called immediately:

```go
func() {
    fmt.Println("Hello from anonymous function")
}()
```

Or assigned to a variable:

```go
greet := func(name string) {
    fmt.Println("Hello,", name)
}
greet("Go")
```

### 6. Functions as First-Class Citizens

In Go, functions are **first-class citizens**. This means:

- You can assign functions to variables.

```go
func greet() {
    fmt.Println("Hello, Go!")
}

var myFunc func() = greet
myFunc() // Calls the greet function
```

- You can pass functions as arguments to other functions.

```go
func operate(f func(int, int) int, x, y int) int {
    return f(x, y)
}

func add(a, b int) int { return a + b }
func multiply(a, b int) int { return a * b }

result1 := operate(add, 2, 3)      // 5
result2 := operate(multiply, 2, 3) // 6
```

- You can return functions from functions.

```go
func makeMultiplier(factor int) func(int) int {
    return func(x int) int {
        return x * factor
    }
}

double := makeMultiplier(2)
fmt.Println(double(5)) // Output: 10
```

- You can store functions in data structures (like slices or maps).

```go
operations := map[string]func(int, int) int{
    "add": func(a, b int) int { return a + b },
    "sub": func(a, b int) int { return a - b },
}

result := operations["add"](10, 5) // result is 15
```

Treating functions as values allows for flexible and powerful programming patterns, such as callbacks, higher-order functions, and custom behaviors.

---

## ⚡ Summary

- Functions encapsulate logic and promote code organization in Go.
- They can accept parameters and return single or multiple values.
- Functions can be named, anonymous, or variadic.
- Functions are first-class citizens: they can be assigned to variables, passed as arguments, returned from other functions, and stored in data structures.
- Leveraging functions enables reusable, modular, and flexible code—supporting patterns like callbacks and higher-order
