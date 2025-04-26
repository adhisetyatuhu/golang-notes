# Webserver
Here is a simple example of webserver in go.
```go
package main

import (
    "fmt"
    "net/http"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello, World!") // Write response to the client
}

func main() {
    // Register the handler for the "/" route
    http.HandleFunc("/", helloHandler)

    // Start the server on port 8080
    fmt.Println("Starting server on :8080")
    err := http.ListenAndServe(":8080", nil)
    if err != nil {
        fmt.Println("Error starting server:", err)
    }
}
```
