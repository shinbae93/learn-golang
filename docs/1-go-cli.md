# Go CLI Commands

The Go CLI provides several commands to build, run, format, install, fetch, and test Go programs. Below are the most commonly used commands:

## 1. `go build`

- Compiles a bunch of Go source code files.

## 2. `go run`

- Compiles and executes one or more Go source files in a single step.

## 3. `go fmt`

- Formats all the code in each file in the current directory.

## 4. `go install`

- Compiles and installs a package.
- Places the resulting binary in the `$GOPATH/bin` (or module-aware `bin` directory).

## 5. `go get`

- Downloads the raw source code of someone else’s package.
- Also updates dependencies in your module (`go.mod`).

## 6. `go test`

- Runs tests associated with the current project.
- By default, looks for files ending with `_test.go`.
