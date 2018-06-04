# dasar-belang
Belajar Golang dasar

# package
setiap aplikasi go harus punya **package**. contoh:
```
package main
```
1. main = executable package
**main** adalah package default, dan cuma package ini yang bisa di **build**.
2. !main = reusable package

variable global / fungsi, bisa diakses asalkan di satu package

# komentar
- oneline = //
- multiline = /* */

# tipe data:
semua varibel wajib dideklarasikan tipe datanya (**manifest typing**)
## contoh deklarasi variabel
### inisiasi variabel
```
var firstName string = "portgas"
var lastName string
lastName = "d. ace"
```
atau dengan **type inference**:
```
firstName := "portgas"
lastName := "d. ace"
```
> := cuma bisa dipake didalam func
> := cuma dipakai buat **inisialiasi pertama**
### multi variabel
```
var firstName, middleName, lastName string
firstName, middleName, lastName = "portgas", "d.", "ace"
```
```
var firstName, middleName, lastName string = "portgas", "d.", "ace"
```
```
firstName, middleName, lastName, bisaInteger := "portgas", "d.", "ace", 100
```

## undescore ( _ ) / tong sampah
semua variable di golang **wajib** dipake, kalo mau tampung variable ga kepake pake _
contoh:
```
for _, values := range names {
    fmt.Println(values)
}
```

## keyword **new**
keyword __new__ dipake buat cetak data **pointer**
```
name := new(string)

fmt.Println(name)   // 0x20818a220
fmt.Println(*name)  // ""
```

## keyword **make**
cuma bisa dipake by: **channel, slice, map**

## numerik
### bulat
- uint : bilangan bulat positif 0 <> xxxx
- int : bilangan bulat positif negatif -xxxx <> xxxx

### desimal
- float32
- float64

## boolean
- bool: true false, huruf kecil

## string
```
var firstName string = "portgas"
```
bisa pake backtick **`**, semua karakter yang diketik = ouput.

## konstanta
```
const phi float32 = 3.14
```

## array
1. array = tuples (static / immutable)
2. slice = array (dynamic / mutable)
    An array and a structure that records the length of the slice, the capacity of the slice, and a reference to the underlying array

## slice
sliceName[0:2] => ambil data index sampai 2, tidak termasuk 2 (0, 1)
sliceName[:2] == sliceName[0:2] => true

## struct
struktur data. koleksi dari properties yang berhubungan satu sama lain.
contain suit and value

## map
kalau dibahasa lain = ruby: hash, js: object, python: dict
**tipe data key = other key, values = other values, key != values

## nil
- bisa dipake di tipe data: **pointer, func, slice, map, channel, interface**
- karena punya nilai default sendiri, jadi ga bisa dipake di:
    * string default-nya =  "" (string kosong)
    * bool default-nya = false
    * tipe numerik non-desimal default-nya = 0
    * tipe numerik desimal default-nya = 0.0

# kondisi
- if, else if, else
percent = temporary varibel, perlu diinget setelah if wajib ":=", selebihnya "="
```
var point = 8840.0

if percent := point / 100; percent >= 100 {
    fmt.Printf("%.1f%s perfect!\n", percent, "%")
} else if percent >= 70 {
    fmt.Printf("%.1f%s good\n", percent, "%")
} else {
    fmt.Printf("%.1f%s not bad\n", percent, "%")
}
```
- switch
> ga ada **break**, tapi tetep bakal berhenti kalo kondisi terpenuhi. kalau tetep mau di terusin, tambahin **fallthrough**
> case bisa multiple kondisi, tinggal ditambahkan aja **,**
> bisa pakai gaya if else ```point == 8```
```
var point = 6

switch point {
    case point == 8:
        fmt.Println("perfect")
    case 7, 6, 5, 4:
        fmt.Println("awesome")
        fallthrough
    default:
        {
            fmt.Println("not bad")
            fmt.Println("you need to learn more")
        }
}
```
> golang **ga dukung** ternary operation boleh = abc == true ? "boleh" : "ga boleh"

# perulangan
## for
- standar
```
for i := 0; i < 5; i++ {
    fmt.Println("Nomor ke: ", i)
}
```
- pertengahan
```
var i = 0

for i < 5 {
    fmt.Println("Nomor ke: ", i)
    i++
}
```
- whaatt
```
var i = 0

for {
    fmt.Println("Nomor ke: ", i)
    i++
    if i == 5 {
        break
    }
}
```

