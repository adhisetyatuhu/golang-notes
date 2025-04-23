## Common String Format  
| Format | Usage for | Example                         | Output     | 
|:------:|-----------|---------------------------------|------------|
|   %s   | String    | `fmt.Printf("%s", "a string"`   | `a string` |
|   %d   | Integer   | `fmt.Printf("%d", 10)`          | `10`       |
|   %f   | Decimal   | `fmt.Printf("%f", 3.141592)`    | `3.141592` |
|  %.2f  | Decimal   | `fmt.Printf("%f", 3.141592)`    | `3.14`     |
|   %t   | Boolean   | `fmt.Printf("%t", false)`       | `false`    |
|   %T   | Type of   | `fmt.Printf("%T", false)`       | `bool`     |


## Array
```go
scores := [5]float64{0.8867, 0.7654, 0.6543, 0.5432, 0.4321}

for i, score := range scores {
  fmt.Printf("Subject %d: %.2f\n", i+1, score*100)
}

for i := 0; i < len(scores); i++ {
  fmt.Printf("Subject %d: %.2f\n", i+1, scores[i]*100)
}
```
```go
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
```
