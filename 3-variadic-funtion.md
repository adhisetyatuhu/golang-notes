## Variadic Function
Variadic function di Go adalah _function_ yang dapat menerima sejumlah argumen yang tidak terbatas 
dari tipe tertentu. Argumen-argumen ini dikumpulkan menjadi sebuah slice di dalam _function_. Variadic 
function dideklarasikan dengan menggunakan tiga titik (`...`) sebelum tipe data parameter terakhir.

### Contoh
```go
package main

import "fmt"

// Variadic function menerima sejumlah argumen integer
func sum(numbers ...int) int {
    total := 0
    for _, number := range numbers {
        total += number
    }
    return total
}

func main() {
    // Memanggil variadic function dengan berbagai jumlah argumen
    fmt.Println(sum(1, 2, 3))        // Output: 6
    fmt.Println(sum(10, 20, 30, 40)) // Output: 100
    fmt.Println(sum())               // Output: 0
}
```

### Menggunakan Slice sebagai Argumen
Jika kita sudah memiliki slice dan ingin menggunakannya sebagai argumen variadic, kita bisa menggunakan 
operator spread (`...`):
```go
nums := []int{1, 2, 3, 4}
fmt.Println(sum(nums...)) // Output: 10
```
> #### Catatan
> - Variadic parameter harus menjadi parameter terakhir dalam deklarasi _function_.
> - Anda hanya dapat memiliki satu variadic parameter dalam sebuah _function_.
