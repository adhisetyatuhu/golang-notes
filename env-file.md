# .env
To use a `.env` file to save an API key in Go, follow these steps:

## 1. Create a `.env` File
Create a `.env` file in the root of your project and store your API key in it. For example:
```
API_KEY=your_api_key_here
```

## 2. Install the `godotenv` Package
Use the `godotenv` package to load the `.env` file into your Go application. Install it using 
the following command:
```go.mod
go get github.com/joho/godotenv
```

## 3. Update Your Go Code
Modify your Go code to load the `.env` file and access the API key using `os.Getenv`.
```go
package main

import (
    "fmt"
    "log"
    "os"

    "github.com/joho/godotenv"
)

func main() {
    // Load the .env file
    err := godotenv.Load()
    if err != nil {
        log.Fatalf("Error loading .env file")
    }

    // Get the API key from the environment
    apiKey := os.Getenv("API_KEY")
    if apiKey == "" {
        log.Fatalf("API_KEY is not set in the .env file")
    }

    // Use the API key
    fmt.Println("Your API Key is:", apiKey)
}
```

## 4. Add `.env` to `.gitignore`
To prevent the `.env` file from being committed to version control (e.g., Git), add it to your `.gitignore` file:
```
.env
```

## Key Points
+ **Store Sensitive Data**: Use `.env` to store sensitive data like API keys, database credentials, etc.
+ **Access with `os.Getenv`**: Use `os.Getenv("KEY_NAME")` to retrieve values from the environment.
+ **Secure Your `.env` File**: Never commit `.env` files to public repositories.

This approach ensures that sensitive information like API keys is kept secure and separate from your source code.
