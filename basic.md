## Common String Format  
| Format | Usage for | Example                         | Output     | 
|:------:|-----------|---------------------------------|------------|
|   %s   | String    | `fmt.Printf("%s", "a string"`   | `a string` |
|   %d   | Integer   | `fmt.Printf("%d", 10)`          | `10`       |
|   %f   | Decimal   | `fmt.Printf("%f", 3.141592)`    | `3.141592` |
|  %.2f  | Decimal   | `fmt.Printf("%.2f", 3.141592)`  | `3.14`     |
|   %t   | Boolean   | `fmt.Printf("%t", false)`       | `false`    |
|   %T   | Type of   | `fmt.Printf("%T", false)`       | `bool`     |


## Array
```go
var students = [5]string{"John", "Jane", "Alice", "Bob", "Charlie"}

for i := 0; i < len(students); i++ {
  fmt.Printf("Student seating number %d: %s\n", i+1, students[i])
}
```
```go
scores := [...]float64{0.8867, 0.7654, 0.6543, 0.5432, 0.4321}

for i, score := range scores {
  if percent := score * 100; score >= 0.8 {
    fmt.Printf("Subject %d: %.2f, Grade A\n", i+1, percent)
  } else if score >= 0.7 {
    fmt.Printf("Subject %d: %.2f, Grade B\n", i+1, percent)
  } else if score >= 0.6 {
    fmt.Printf("Subject %d: %.2f, Grade C\n", i+1, percent)
  } else if score >= 0.5 {
    fmt.Printf("Subject %d: %.2f, Grade D\n", i+1, percent)
  } else {
    fmt.Printf("Subject %d: %.2f, Grade E\n", i+1, percent)
  }
}

total := 0.0
for _, score := range scores {
  total += score
}
fmt.Printf("My total score is %.2f\n", total*100)
```

## Slice
An array has a fixed size. A slice, on the other hand, is a dynamically-sized, flexible view into the elements of an array.  
```go
var fruits = []string{"Apple", "Banana", "Cherry", "Date", "Elderberry"}
fmt.Println(fruits)
// Output: [Apple Banana Cherry Date Elderberry]

fruits = append(fruits, "Fig", "Grape")
fmt.Println(fruits)
// Output: [Apple Banana Cherry Date Elderberry Fig Grape]
```
Slices are like references to arrays
|      Code     |                      Output                       | Explanation |
|---------------|---------------------------------------------------|-------------|
| `fruits[0:2]` | `[Apple Banana]`                                  | Elements from index 0 to before index 2 |
| `fruits[2:2]` | `[]`                                              | An empty slice |
| `fruits[:]`   | `[Apple Banana Cherry Date Elderberry Fig Grape]` | All elements |
| `fruits[2:]`  | `[Cherry Date Elderberry Fig Grape]               | Elements from index 2 to the last index |
| `fruits[:2]`  | `[Apple Banana]`                                  | Every elements before index 2, kinda similar to `fruits[0:2]` |

### Slice implementation (delete)
```go
fruits := []string{"Apple", "Banana", "Cherry", "Date", "Elderberry"}

deletedFruitIndex := 2
fruits = append(fruits[:2], fruits[deletedFruitIndex+1:]...)

fmt.Println(fruits)
// Output: [Apple Banana Date Elderberry]
```
