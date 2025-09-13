# Variables in Go

Variables are used to store data in Go programs. They have a name, a type, and a value.

---

## 1. Declaring Variables

### 1.1 Using `var`

```go
var age int
age = 30
```

You can also initialize at declaration:

```go
var name string = "Gopher"
```

### 1.2 Type Inference

Go can infer the type if you provide an initial value:

```go
var score = 100 // score is int
```

### 1.3 Short Declaration (`:=`)

> **Note:** Short declaration (`:=`) must be used **inside functions**.  
> At the package level, you can only use `const` and `var` declarations.

Inside functions, you can use `:=` for quick variable declaration and initialization:

```go
message := "Hello, Go!"
count := 5
```

### 1.4 Multiple Variables

Declare multiple variables at once:

```go
var x, y int = 1, 2
a, b := "foo", "bar"
```

## 2. Zero Values

Variables declared without an initial value get a **zero value**:

| Type     | Zero Value |
| -------- | ---------- |
| int      | 0          |
| float64  | 0.0        |
| string   | ""         |
| bool     | false      |
| pointers | nil        |

## 3. Constants

Use `const` for values that never change:

```go
const Pi = 3.14
const Greeting = "Hello"
```

## 4. Variable Scope

- **Global:** Declared outside functions, accessible everywhere in the package.
- **Local:** Declared inside functions, accessible only within that function.

## 5. Example

```go
package main

import "fmt"

func main() {
    var language string = "Go"
    version := 1.21
    const creator = "Google"

    fmt.Println(language, version, creator)
}
```

## 6. Summary

- Use `var` or `:=` to declare variables.
- Variables have types and zero values.
- Use `const` for constants.
- Scope determines where a variable can be accessed in the code.
