---
title: "Lazy Delegate kotlin"
category: "android"
author: "randy"
date: "2018-09-04"
cover: "/images/kotlin_inline_class/kotlin_inline_class.jpg"
tags:
    - kotlin
    - android
---

Lazy merupakan fungsi yang menerima lambda dan mengembalikan sebuah Instance sebagai delegasi property. Properti atribut lazy kotlin digunakan untuk mendeklarasikan nilai properti saat pertama kali dijalankan. Hal ini tentu berguna jika kita memperoleh kondisi dimana resource yang mahal untuk memperoleh sebuah data. Sebagai contoh, apabila Anda ingin mendeklarasikan nilai pada objek user, dimana dibutuhkan untuk pemanggilan microservice yang hanya sekali saja dipergunakan. Kamu harus selalu melakukan atau memasukkan nilai pada objek user apabila ingin menjalankannya, seharusnya Anda cukup melakukan deklarasi ketika Anda memperoleh data pertama kali. 

Kita akan membuat sebagian contoh, semisal Anda memanggil service pada suatu objek pada kelas, biasanya kita akan menggunakan konstruktor dimana konstruktor merupakan fungsi pertama kali dijalan saat pembuatan objek. 

```kotlin
class User {
    val name : String 
    
    constructor(idUser : Int){
        Thread.sleep(2000)
        name = "Randy"
    }
}

fun main(args : Array<String>) {
    val user = User(10)
    println(user.name)
}
```

Contoh lain adalah sebagai berikut,

```kotlin
class User {
    var name : String = ""
    
    fun access() {
        Thread.sleep(2000)
        name = "Randy"
    }
}

fun main(args : Array<String>) {
    val user = User(10)
    user.access()
    println(user.name)
}
```

Contoh kedua pada baris kode tersebut tentu tidak efektif dan efisien, mengingat jenis property yang digunakan pada "name" bersifat mutable artinya data dapat berubah-ubah sehingga mengurangi performa dari pada penggunaan val(immutable). Parahnya apabila kita tidak mendefinisikan atau mengimplementasi fungsi access maka println tidak memperoleh data apa-apa hanya data kosong. 

Solusinya adalah dengan menggunakan Lazy property, penggunaan lazy property jelas lebih baik dari hasil contoh yang telah saya berikan diatas, clean code dan tentunya efektif dan efisien. 

```kotlin
class User(val idUser : Int){
    val name : String by lazy {
        Thread.sleep(2000)
        "Randy"
    }
}

fun main(args : Array<String>){
    val user = User(10)
	println(user.name)
}
```

Sekilas ketika kita mengimplementasikan lazy diatas kita akan teringat dengan aslah satu pembuatan variabel yang dideklarasikan nanti sehingga mampu menghindari null. ya betul, jawabannya adalah penggunaan `lateinit`. kedua properti tersebut bisa digunakan untuk menghindari pembuatan property di konstruktor.



**Lateinit**

lateinit merupakan akronim dari late initialization atau dalam bahasa indonesia bisa diartikan sebagai di-inisiasi nanti. Biasanya lateinit ini digunakan saat kita tidak bisa memasukkan nilai secara langsung, melainkan hanya menampung terlebih dahulu yang nantinya bisa diisi null atau nonnull. Nah, kotlin tidak memperbolehkan membuat property yang nantinya menimbulkan Null Pointer Exception(NPE) apabila field property tidak berisi apa, meski kita bisa saja menggunakan variabel biasa dengan menambahkan questionmark misal `var user : String? = null` namun ini juga tidak disarankan kadang kita harus menambahkan questionmark secara berkelanjutan untuk memastikan field property tersebut tidak null apalagi bila chaining seperti `user?.atribut?.name?. . . .` tentunya menyebalkan bukan? Nah lateinit berguna untuk mengatasi hal tersebut, lateinit memperbolehkan nilai yang belum diisi tanpa embel-embel questionmark `lateinit var user : String`. Tetapi ingat property lateinit ini bukan berarti null tetapi non-null yang harus diisi nanti dan tentunya lateinit tidak mengizinkan tipe data primitif.

Lalu kapan lateinit dan lazy kita dapat gunakan?

- lazy hanya dapat diimpelementasikan atau digunakan untuk property yang bersifat immutable yakni penggunaan `val`. Sebaliknya lateinit hanya menerima property yang bersifat mutable atau `var`. Karena lateinit tidak dapat dikompile ke dalam final.
- lateinit dapat di-initialize dari manapun asal sesuai dengan scope objeknya. Gunakan lateinit apabila Anda ingin menginisiasi dengan nilai yang belum pasti yang ada di luar fungsi.

 

 