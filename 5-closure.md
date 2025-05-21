# Closure
A closure is a function value that references variables from outside its body. 
These variables are captured by the closure and remain accessible even after 
the outer function has returned. Closures are often used to create functions 
dynamically or to maintain state between function calls.

## How Closures Work
A closure "closes over" the variables in its surrounding scope, allowing it 
to access and modify them even after the scope has exited.

```go
package main

import "fmt"

func counter() func() int {
    count := 0 // Variable in the outer scope
    return func() int {
        count++ // Captures and modifies the outer variable
        return count
    }
}

func main() {
    increment := counter() // Create a closure
    fmt.Println(increment()) // Output: 1
    fmt.Println(increment()) // Output: 2
    fmt.Println(increment()) // Output: 3

    anotherIncrement := counter() // Create a new closure
    fmt.Println(anotherIncrement()) // Output: 1
}
```
> **Explanation:**
> + The `counter` function returns an anonymous function (a closure).
> + The closure captures the `count` variable from the outer function.
> + Each call to `increment()` modifies the `count` variable, maintaining its state between calls.


### Key Characteristics of Closures
1. **Captures Variables**: Closures can access and modify variables from their enclosing scope.
2. **Stateful**: Closures can maintain state between function calls.
3. **Independent Instances**: Each closure instance has its own copy of the captured variables.

<br />

## Practical Use Cases
1. **Encapsulation of State**: Closures are often used to encapsulate state in a function without exposing it globally.
   ```go
   func adder(x int) func(int) int {
     return func(y int) int {
       return x + y
     }
   }

   func main() {
     addFive := adder(5)
     fmt.Println(addFive(3)) // Output: 8
     fmt.Println(addFive(10)) // Output: 15
   }
   ```
3. **Callbacks**: Closures are useful for defining inline functions, such as callbacks.
   ```go
   package main

   import "fmt"

   func process(numbers []int, callback func(int)) {
     for _, n := range numbers {
       callback(n)
     }
   }

     func main() {
     nums := []int{1, 2, 3, 4}
     process(nums, func(n int) {
       fmt.Println(n * n) // Output: 1, 4, 9, 16
     })
   }
   ```
4. **Dynamic Function Creation**: Closures can be used to create functions dynamically based on input.
   ```go
   func multiplier(factor int) func(int) inÂt {
     return func(x int) int {
       return x * factor
     }
   }

   func main() {
     double := multiplier(2)
     triple := multiplier(3)

     fmt.Println(double(4)) // Output: 8
     fmt.Println(triple(4)) // Output: 12
   }
   ```

## Key Points
+ A closure is a function that captures variables from its surrounding scope.
+ Closures are useful for maintaining state, creating dynamic functions, and implementing callbacks.
+ Each closure instance has its own independent copy of the captured variables.

Closures are a powerful feature in Go that enable functional programming patterns and dynamic behavior.
