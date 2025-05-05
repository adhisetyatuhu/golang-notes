# Random Number Generator
```go
import (
    "math/rand"
    "time"
)

func main() {
    // Create a new random number generator with a unique seed
	rng := rand.New(rand.NewSource(time.Now().UnixNano()))

    // Generate a random number (Output: either 0 or 1)
	randNum := rng.Intn(2)  // generate random int number from 0 to before 2
}
```
