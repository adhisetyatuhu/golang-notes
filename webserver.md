# Webserver
A web server in Go is a program that listens for HTTP requests and responds to them. 
Go's standard library provides the `net/http` package, which makes it easy to create 
a web server without requiring external dependencies.

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
> **1. Handler Function:**  
> + `helloHandler` is a function that takes `http.ResponseWriter` (to write the response) and `*http.Request` (to read the request).   
> + It writes `"Hello, World!"` to the response.  
> 
> **2. Registering the Handler:**
> + `http.HandleFunc("/", helloHandler)` registers the helloHandler function to handle requests to the root path (`/`).
> 
> **3. Starting the Server:**
> + `http.ListenAndServe(":8080", nil)` starts the server on port `8080`.
> + The second argument (`nil`) means the default `http.DefaultServeMux` is used for routing.
>
