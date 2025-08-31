# 📦 Packages in Go

A **package** in Go is a way to organize, modularize, and reuse code.  
Every Go source file belongs to a package. When you compile a Go program, all files within the same package are compiled together.

---

## 🔑 Key Concepts

### 1. Package Declaration

At the top of every `.go` file:

```go
package main
```

- `main` → special package that defines an executable program.
- Other names (e.g., `fmt`, `math`, `utils`) → define libraries that can be imported.

---

### 2. Importing Packages

Use the `import` keyword:

```go
import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

You can import multiple packages:

```go
import (
    "fmt"
    "strings"
)
```

---

### 3. Exported vs Unexported Identifiers

- **Exported (Public):** Names starting with a capital letter.
- **Unexported (Private):** Names starting with a lowercase letter.

Example:

```go
package greetings

func Hello() string { // Exported
    return "Hello!"
}

func secret() string { // Unexported
    return "shhh..."
}
```

---

### 4. Standard Library Packages

Go comes with a rich standard library. Common ones include:

| Package  | Purpose                        |
| -------- | ------------------------------ |
| fmt      | Formatting, printing, scanning |
| os       | Operating system interaction   |
| strings  | String manipulation            |
| math     | Math utilities & constants     |
| time     | Time/date handling             |
| net/http | Build HTTP clients & servers   |

---

### 5. Creating Custom Packages

**Project Structure:**

```
myapp/
├── main.go        # package main
└── utils/
    └── math.go    # package utils
```

**utils/math.go**

```go
package utils

func Add(a, b int) int {
    return a + b
}
```

**main.go**

```go
package main

import (
    "fmt"
    "myapp/utils"
)

func main() {
    fmt.Println(utils.Add(2, 3)) // 5
}
```

---

### 6. Package Initialization

A package can have an `init()` function that runs automatically when imported.  
Used for setup (e.g., registering drivers, initializing variables).

```go
package config

import "fmt"

func init() {
    fmt.Println("Config package initialized")
}
```

---

### 7. main Package

Every Go program must have a `main` package.  
Must contain a `main()` function, the entry point of the program.

```go
package main

import "fmt"

func main() {
    fmt.Println("Program starts here!")
}
```

---

### 8. Package Visibility

Packages are imported using their module path.  
In Go modules (`go.mod`), your package path depends on your module name.

Example:

```bash
go mod init github.com/username/myapp
```

Now you can import:

```go
import "github.com/username/myapp/utils"
```

---

## ⚡ Summary

- A package is a collection of `.go` files in the same directory.
- `main` package → builds executables.
- Other packages → libraries you can reuse.
- Capitalized names are exported (public).
- Use `init()` for automatic initialization.
- Organize projects into meaningful packages for clarity and reusability.
