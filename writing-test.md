# Writing Test
Writing a test is just like writing a function, with a few rules

+ It needs to be in a file with a name like `xxx_test.go`
+ The test function must start with the word `Test`
+ The test function takes one argument only `t *testing.T`
+ To use the `*testing.T` type, you need to `import "testing"`, like we did with `fmt`

### Example

```go
// hello.go
package main

import "fmt"

func Hello() string {
	return "Hello, World!"
}

func main() {
	fmt.Println(Hello())
}

```

```go
// hello_test.go
package main

import "testing"

func TestHello(t *testing.T) {
	got := Hello()
	want := "Hello, World!"

	if got != want {
		t.Errorf("got %q want %q", got, want)
	}
}

```

> ### Note
> Use `!reflect.DeepEqual` to compare slices (note that it is not type-safe, so it
> will compile regardless of the types being compared). From **Go 1.21**, slices standard
> package is available, which has `slices.Equal` function to do a simple shallow compare
> on slices, where you don't need to worry about the types like the above case. Note
> that this function expects the elements to be comparable. So, it can't be applied to
> slices with non-comparable elements like 2D slices.

[Here is a good reference to learn go with TDD](https://quii.gitbook.io/learn-go-with-tests/)
