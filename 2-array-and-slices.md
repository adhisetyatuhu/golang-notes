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
fmt.Printf("My total score in percent is %.2f\n", total*100)
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
| `fruits[2:]`  | `[Cherry Date Elderberry Fig Grape]`               | Elements from index 2 to the last index |
| `fruits[:2]`  | `[Apple Banana]`                                  | Every elements before index 2, kinda similar to `fruits[0:2]` |

### Slice implementation (delete an element)
```go
fruits := []string{"Apple", "Banana", "Cherry", "Date", "Elderberry"}

deletedFruitIndex := 2
fruits = append(fruits[:2], fruits[deletedFruitIndex+1:]...)

fmt.Println(fruits)
// Output: [Apple Banana Date Elderberry]
```
Did you notice in the code above, we use [spread operator](3-variadic-funtion.md#menggunakan-slice-sebagai-argumen) to append the fruits? The spread operator (`...`) is used to "unpack" the elements of the slice `fruits[deletedFruitIndex+1:]` and append them as individual elements to the slice `fruits[:2]`. It is because The append function in Go expects individual elements (not a slice) as its arguments after the first slice. Therefore the spread operator is used so that the slice are passed in elements (as individual arguments) to append.
