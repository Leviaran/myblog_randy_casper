---
title: "Meningkatkan Performa Kotlin dengan Inline Class"
category: "android"
author: "randy"
date: "2018-09-03"
cover: "/images/kotlin_gradle/Kotlin_inline_class.jpg"
tags:
    - kotlin
    - android
---

**Kotlin Strong type and simple value**

Terkadang developer atau programmer dalam mengetikan kode, lebih memilih untuk meneruskan pass Integer, float, dan boolean pada basis kode yang dibuat dari pada membungkus kelas nilai sederhana atau class warper. sebagai contohnya adalah sebagai berikut,

Kita memiliki kelas interface yang berupa interface notifikasi yang didalamnya terdapat fungsi mengirim notifikasi.

```kotlin
interface BroadcastNotification{
    fun sendNotif(idUser : User, delay : Int)
}
```

Interface tersebut lalu diimplementasikan kedalam sebuah fungsi kelas lain,

```kotlin
fun sendNotif(idUser : User){
    broadcastNotification.sendNotif(idUser, DELAY * 24 *60 )
}
```

Hmm, ternyata bisa saja kita memilih mengisi parameter tersebut dengan menit atau bahkan jam. kita balik lagi kemungkinan Int bukan tipe yang tepat untuk parameter yang berhubungan dengan waktu. Coba kita ganti menjadi tipe menit.

```kotlin
interface BroadcastNotification{    
    fun sendNotif(idUser : User, delay : Minute)
}
```

Kalau sudah seperti diatas developer akan memaksakan untuk memasukkan delay dalam tipe menit daripada tipe Integer. Artinya apabila format delay dalam sebuah parsing Json berupa hari maka kita harus mengubah hari tersebut ke dalam format menit.

```kotlin
val defaultTime = Day(4)
fun sendNotif(idUser : User){    
    broadcastNotification.sendNotif(idUser, defaultTime.toMinute() )
}
```

Nah apabila Anda cermati sebenarnya kita memakai beberapa objek saat menginisiasi fungsi tersebut, seperti objek Day, User, dan Menit. Padahal bukankah kita hanya mengnisiasi berupa angka saja untuk mengetahui berapa lama delay yang terjadi. Pembuatan objek pada sebuah fungsi yang tidak terlalu signifikan tentu akan terasa sia-sia. Kenapa? karena jelas semakin banyak objek yang dibuat maka jelas mempengaruhi performa. 

Dulu pernah kita bersinggunan dengan tipe data primitif bukan? java membuat tipe data primitif untuk mengurangi resource yang dibutuhkan, apalagi yang berdampak pada performa device yang menjalankannya. Nah tipe data primitif ini seperti float, integer, boolean, dll bisa menunjang performa device, maklum waktu itu device tidak seperti sekarang ini resource Ram, processor, dll sangatlah minim. Nah tipe data primitif ini disimpan dalam bagian JVM yang dikenal sebagai "stack".

Sebaliknya Objek harus di-instansiasi terlebih dahulu untuk membuatnya. Objek dibuat dengan menyimpan objek tersebut pada Heap. Menyimpan di Heap berdampak pada performa karena alokasi dalam Heap dan memori pendukungnya memerlukan reseource yang mahal. Apabila jika Objek di buat dalam jumlah cukup atau sedikit tidak akan berdampak apa-apa. Namun, bagaimana jadinya bila Heap terlalu banyak, jelas akan mempengaruhi performa saat kode dijalankan. Tentu akan lebih baik jika kita bisa menggunakan Heap tanpa mempengaruhi performa.

Saya perkenalkan **inline class** kotlin, inline class ini merupakan fitur yang cukup baru, meski sudah di kembangkan lama tetapi fitur ini masih belum final sampai sekarang. inline class dapat diimplementasi dengan mudah dengan menuliskan kode sebagai berikut,

```kotlin
inline class Minute(val value : Int){
    fun toHour() = Hour(value / 60)
}
```

Kelas yang kita buat diatas sudah menjadi atau berlaku sebagai strong type. Meski Strong type pembuatan atau instansiasi objek pada inline class tersebut tidak mempengaruhi performa. Anda dapat membuat objek atau Instansiasi inline class dengan pembutan objek biasa seperti pembuatan objek pada kelas kelas lain (non-inline class). 

Coba perhatikan kode diatas, kelas "Minute" merupakan nama inline class, didalamnya terdapat parameter value dengan type integer serta immutable(val). Nah, "value" disebut sebagai nilai yang harus diisi dengan tipe Integer, Integer disini berlaku sebagai **[underlying type](https://stackoverflow.com/a/1122128)**. Underlying type merupakan tipe enumerasi integral yang dapat mempresentasikan semua tipe enumerasi yang telah didefinisikan. 

inline class pada kelas minute tersebut akan dikompile ke dalam integer bukan sebagai objek Minute. Lalu apabila dikompile ke Integer artinya kita tidak bisa mengakses fungsi `toHour()`, bukankah Int tidak memiliki fungsi `toHour()`? Jawabannya tentu saja bisa, inline class mengompile fungsi-fungsi didalamnya sebagai fungsi dengan tipe statik. Hasil compile inline class Minute diatas akan menjadi,

```java
public static final int toHour(int $this){
    return $this /60;
}
```

sehingga ketika kita memanggil kode `Minute(60).toHour()` pada Kotlin akan dikompile menjadi `toHour(60)`.



**Kenapa Inline class lebih baik?** 

Baiklah, kembali lagi pertanyaan awal. Kenapa inline class lebih baik dari pada class biasa?

Kita coba dengan instansiasi dengan kode berikut,

```kotlin
val minute = Minute(60)
```

Instansiasi objek tersebut sebenarnya tidak diInstansiasi saat kode terkompile. faktanya, selama dijalankan dengan JVM maka kode tersebut dieksekusi sama dengan berikut,

```java
int minute = 60;
```

Menarik bukan? Dalam kompilasinya tidak ada objek "Minute" hanya langsung menetapkan nilai underlying type sebagai variabel integer. Hal ini juga berlaku dalam penggunaan fungsi,

```kotlin
fun delay(period : Minute){}
```

berdasarkan kodingan diatas akan dikompile sebagai berikut,

```java
void delay(int period){}
```

sehingga pada inline class mengompile kode hanya menggunakan tipe integer, dengan begitu pembuatan objek pada Heap bisa dihindari. 



**Limitasi pembuatan Inline class**

Setelah Anda tahu bahwa nilai pada inline class dapat direpresentasikan ke underliying value pada saat kompilasi, kita harus mengetahui limitasi atau batas-batasn yang ada pada penggunaan inline class. 

1. Inline class harus memiliki underlying value

   Artinya inline class harus memiliki primary konstruktor yang berisi underliying value pada parameter yang bersifat immutable(harus val bukan var).

   ```kotlin
   inline class Hour(val delay : Int)  //perfect,
   inline class Hour(delay : Int) 		//nope, nilai delay harus property
   inline class Hour(var delay : Int) 	//nope, harus immutable
   inline class Hour() 				//nope, harus dapat menerima nilai
   ```

2. Konstruktor harus bersifat publik

   konstruktor pada inline class harus bersifat publik artinya dapat diakses secara publik tidak boleh memiliki akses modifier lain seperti private atau protected. Namun, akses modifier private atau protecte dapat digunakan pada parameter.

   ```kotlin
   inline class Hour (private val delay : Int)				// perfect
   inline class Hour private constructor(val delay : Int) // nope, 
   ```

3. Tidak boleh memiliki blok initialize

   Blok initialize tidak boleh digunakan pada inline class dikarenakan akan mempengaruhi interoperate dengan kompilasi byte code java.

   ```kotlin
   inline class Hour(val delay : Int){
       init {
           condition(delay > 0)
       }
   }
   ```

4. Tidak boleh memiliki parameter lebih dari satu

   Underlying value hanya menerima satu dan tidak boleh lebih, namun inline class dapat mengakses properties selama masih dalam satu dengan underlying value, serta dari value yang berasala dari objek statik semisal dari Singleton, Top level objek, dll.

   ```kotlin
   object StaticTime{
       const val Hour_Per_Day = 24   
   }
   
   inline class Hour(val delay : Int){
       val delayAsDay get() = delay * StaticTime.Hour_Per_day
   }
   ```

5. Inline class tidak dapat meng-extends kelas lain

   Untuk versi saat ini inline class tidak diizinkan untuk menge-extends kelas lain, begitu juga sebaliknya kecuali interface. Namun, kemungkinan kedepan inline class dapat meng-extends kelas lain untuk lihat trackingnya dapat dilihat di [sini](https://youtrack.jetbrains.net/issue/KT-26120). 

   ```kotlin
   open class TimeConvertion
   inline class Hour(val delay : Int) : TimeConvertion //nope
   open inline class Hour(val delay : Int) //nope
   
   interface TimeConvertion {val delay : Int}
   inline class Hour(val delay : Int) : TimeConvertion // perfect
   ```

6. Inline class wajib pada di deklarasikan pada top level 

   Artinya inline class tidak dapat di implementasikan pada kelas bersarang(nested class)

   ```kotlin
   class Day {
       inline class Hour(val delay : Int) //nope
   }
   ```


Baiklah cukup sekian dari dokumentasi saya mengenai Inline class selanjutnya teman-teman perlu memahami bahwa inline class ini masih bersifat experimental. Teman-teman tidak bisa langsung mengimplementasikan, melainkan harus meng-enable experimental serta versi inline class ini dapat dijalankan pada kotlin 1.3-M1. 