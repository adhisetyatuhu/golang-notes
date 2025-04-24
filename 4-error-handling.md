# Error Handling
Error handling in Go is explicit and straightforward, relying on the use of the built-in 
error type. Here's an explanation of how error handling works in Go:

## 1. The `error` Type
The `error` type is an interface in Go that represents an error condition. It is commonly used 
as a return value from functions to indicate whether an operation succeeded or failed.

```go
package main

import (
    "errors"
    "fmt"
)

func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero is not allowed")
    }
    return a / b, nil
}

func main() {
    result, err := divide(10, 0)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Println("Result:", result)
}
```
> **Explanation:**
> + The `divide` function returns a result and an `error`.
> + If `b` is zero, an error is created using `errors.New`.
> + In the `main` function, the error is checked using `if err != nil`.


## 2. Creating Custom Errors
You can create custom error messages using the `errors` package or `fmt.Errorf`.

```go
package main

import (
    "fmt"
)

func checkAge(age int) error {
    if age < 18 {
        return fmt.Errorf("age %d is below the minimum requirement", age)
    }
    return nil
}

func main() {
    err := checkAge(16)
    if err != nil {
        fmt.Println("Error:", err)
    } else {
        fmt.Println("Age is valid")
    }
}
```
> **Explanation:**
> + `fmt.Errorf` is used to create a formatted error message.
> + The error is checked and handled in the `main` function.


## 3. Using `panic` and `recover`
For critical errors that cannot be handled gracefully, Go provides `panic` and `recover`. 
However, these are not recommended for regular error handling.

```go
package main

import "fmt"

func riskyFunction() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from panic:", r)
        }
    }()
    panic("something went wrong")
}

func main() {
    riskyFunction()
    fmt.Println("Program continues after recovery")
}
```

> **Explanation:**
> + `panic` stops the normal execution of the program.
> + `recover` is used to catch and handle the panic, allowing the program to continue.


## 4. Wrapping and Unwrapping Errors
Go 1.13 introduced `errors.Is` and `errors.As` for wrapping and unwrapping errors.
```go
package main

import (
    "errors"
    "fmt"
)

var ErrNotFound = errors.New("item not found")

func findItem(id int) error {
    if id != 1 {
        return fmt.Errorf("findItem: %w", ErrNotFound)
    }
    return nil
}

func main() {
    err := findItem(2)
    if errors.Is(err, ErrNotFound) {
        fmt.Println("Error: Item not found")
    } else {
        fmt.Println("Item found")
    }
}
```
> **Explanation:**
> + `%w` in `fmt.Errorf` wraps an error.
> + `errors.Is` checks if an error matches a specific error.


## 5. Idiomatic Error Handling
The idiomatic way to handle errors in Go is to check the error immediately after 
a function call and handle it appropriately.

```go
file, err := os.Open("example.txt")
if err != nil {
    fmt.Println("Error opening file:", err)
    return
}
defer file.Close()
```

---

## Key Points
1. **Explicit Error Handling**: Errors are returned as values and must be explicitly checked.
2. **No Exceptions**: Go does not use exceptions for error handling, making it simpler and more predictable.
3. **Use `panic` and `recover` Sparingly**: These are reserved for critical, unrecoverable errors.
4. **Error Wrapping**: Use `errors.Is` and `errors.As` for more advanced error handling.

This approach ensures that errors are handled explicitly and predictably, making Go programs more robust and 
easier to debug.
