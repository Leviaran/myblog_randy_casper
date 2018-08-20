---
title: "Recycler View dengan Anko Layout"
category: "android"
author: "randy"
date: "2018-08-20"
cover: "/images/image.jpg"
tags:
    - anko
    - android
---

**Introduction**

Apabila Anda mengimplementasikan Recycler view dengan cara membuat layout di xml itu sudah *main stream*. Mari kita membangun recycler view tanpa harus menggunakan XML dengan Anko Layout.

Untuk mewujudkan itu, kita akan menggunakan [**Anko Layout**](https://github.com/Kotlin/anko/wiki/Anko-Layouts). Apa itu Anko layout? Anko layout merupakan library pihak ketiga Kotlin untuk membangun layout dan merupakan sublibrary dari [Anko](https://github.com/Kotlin/anko). Anko mengklaim mampu membantu mengembangkan aplikasi dengan cepat dan mudah. Anko dikhususkan uituk meningkatkan keterbacaan alias kemudahan membaca kode. Berikut beberapa libary Anko yang lain:

1. **Anko Common**; library Anko yang digunakan sebagai kebutuhan dan mendukung fitur-fitur Activity di Android, sebagai contoh adalah penggunaan Intent. Kita akan bahas di lain waktu untuk penggunaan library ini.
2. **Anko SQLite**; library yang satu ini merupakan sebuah query DSL tambahan dan beberapa koleksi parser khusus Android SQLite.
3. **Anko Coroutines;** Library yang digunakan untuk mendukung kotlinx.Coroutines

Kembali lagi ke Anko layout, Anda pasti bertanya-tanya mengapa harus memakai Anko layout? secara garis besar Anko layout merupakan sarana salah satu alternatif untuk pembuatan layout selain xml, artinya kita akan membuat layout langsung dalam kelas Kotlin. Beberapa kekurangan XML;

1. Tidak *Type Safety*.
2. *Null Pointer Exception*(NPE).
3. Tidak *concise*, tidak *reuse*.
4. Memperlambat pemrosesan dan boros baterai karena proses parser XML melibatkan CPU dan baterai.

Akibat membangun layout secara programmatically, kemudahan penulisan akan terasa lebih sulit dibandingkan membangun dengan XML. Tapi jangan khawatir tim Jetbrain membangun fitur khusus pada Anko menggunakan Domain Spesific Language(DSL) sehingga penulisan DSL lebih mudah dan dinamis. Penggunaan DSL dapat meningkatkan keterbacaan pada logika kode, penulisannya lebih nyaman, dan tidak menyebabkan *runtime overhead* Berikut contoh penggunaan DSL pada Anko layout.

```kotlin
linearLayout {
    orientation = LinearLayout.HORIZONTAL
    lparams(matchParent, wrapContent)
    padding = dip(16)

    imageView{
        id = imageId
        imageResource = R.drawable.img_arsenal

    }.lparams(dip(50), dip(50))

    textView {
        id = nameId
        text = "Coba FC"
    }.lparams(matchParent, wrapContent){
        margin = dip(10)
        gravity = Gravity.CENTER_VERTICAL
    }

}
```



**Create Recycler View**

Tidak perlu basa-basi lagi, mari kita buat bersama-sama.

Tambahakn kode berikut pada Dependencies pada build.gradle level App.

```kotlin
implementation "org.jetbrains.anko:anko-sdk15:0.10.5"
implementation "org.jetbrains.anko:anko-appcompat-v7:0.10.5"
implementation "org.jetbrains.anko:anko-recyclerview-v7:0.10.5"
implementation 'com.github.bumptech.glide:glide:4.7.1'
```

Selanjutnya penggunaan Recyclerview pada kelas MainActivity;

```kotlin
class MainActivity : AppCompatActivity() {

    var footballItem : MutableList<Football> = mutableListOf()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        initData()
        
        verticalLayout { 
            lparams(matchParent, matchParent)
            orientation = LinearLayout.VERTICAL

            recyclerView {
                lparams(matchParent, matchParent)
                layoutManager = LinearLayoutManager(context)
                adapter = FootballAdapter(footballItem){
                    startActivity<SecondActivity>(SecondActivity.POSITIONEXTRA to it)
                    val toast = Toast.makeText(context, it.nama, Toast.LENGTH_SHORT)
                    toast.show()
                }
            }
        }
    }

    private fun initData(){
        val name = resources.getStringArray(R.array.club_name)
        val image = resources.obtainTypedArray(R.array.club_image)
        val keterangan = resources.getStringArray(R.array.club_info)

        footballItem.clear()

        for (i in name.indices){
            footballItem.add(Football(name[i], image.getResourceId(i,0), keterangan[i] ))
        }
        Log.e("info", footballItem.size.toString())

        image.recycle()

    }

}
```

```kotlin
          verticalLayout {
            lparams(matchParent, matchParent)
            orientation = LinearLayout.VERTICAL

            recyclerView {
                lparams(matchParent, matchParent)
                layoutManager = LinearLayoutManager(context)
                adapter = FootballAdapter(footballItem){
                    startActivity<SecondActivity>(SecondActivity.POSITIONEXTRA to it)
                    val toast = Toast.makeText(context, it.nama, Toast.LENGTH_SHORT)
                    toast.show()
                }
            }
        }
```

Pada potongaan kode diatas, kita membuat sebuah layout secara programmaticaly. Struktur kode juga tidak begitu rumit karena bantuan DSL. Sedangkan pada intent jangan pada bingung terlebih dahulu, intent disini menggunakan Anko Common yang disebut sebagai Intent Builder. Penggunaan intent builder cukup hanya inline code. 

Tahap berikutnya adalah membangun UI untuk item pada recycler view.

```kotlin
class FootballUI : AnkoComponent<ViewGroup> {

    companion object {
        val nameId = 1
        val imageId = 2
    }

    override fun createView(ui: AnkoContext<ViewGroup>) = with(ui){
        linearLayout {
            orientation = LinearLayout.HORIZONTAL
            lparams(matchParent, wrapContent)
            padding = dip(16)

            imageView{
                id = imageId
                imageResource = R.drawable.img_arsenal

            }.lparams(dip(50), dip(50))

            textView {
                id = nameId
                text = "Coba FC"
            }.lparams(matchParent, wrapContent){
                margin = dip(10)
                gravity = Gravity.CENTER_VERTICAL
            }

        }
    }
}
```

Satu item UI diatas dirancang dengan satu linear layout yang memiliki orientasi secara Horizontal dengan urutan image kemudian text dari kiri ke kanan. Masing-masing view pada layout pasti membutuhkan ID, id ini seharusnya harus dirancang secara mandiri alias berbeda tempat supaya bisa dikelompokan. Apabila view layout yang Anda buat lebih kompleks, Anda disarankan membangun folder ids.xml pada folder value Android dari pada membuat static value pada masing-masing kelas. 

```groovy
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <item name="name_id" type="id"/>
    <item name="image_id" type="id"/>
</resources>
```

Pasti and bertanya-tanya, bagaimana kita bisa melihat hasil layout yang telah kita buat? Di XML jelas segala bentuk xml kode yang kita bangun dapat kita lihat previewnya, lallu bagaimana dengan anko layout? 

Meski secara programmatically default Anda tidak bisa alias hanya menerawang saga, namun laternatifnya untuk melihat hasil capain layout view yang telah dibuat, Anda bisa menggunakan plugin pihak ketiga official dari jetbrain. Yakni [**Anko Support,**](https://github.com/Kotlin/anko/wiki/Anko-Layouts#anko-support-plugin) anda bisa menambahkan plugin ini pada repositori dengan cara masuk pada setting -> plugin -> browse repositories -> restart Android studio. Untuk melihat preview bisa pada tab menu paling kanan.

Perlu diperhatikan Anko Support ini hanya dapat menampilkan layout hanya jika layout dibangun diluar kelas alias kelas eksternal, sehingga Anko support tidak bisa menampilkan hasil jika dibangun pada satu kelas activity atau fragment kecuali nested class. Hasil *preview* akan ditampilkan apabila kelas DSL anko sudah ter-*generate*, sebaiknya Anda memastikannya dengan me-*rebuild* project setiap Anda membuat baru dan meng-update kelas. Anko Support juga mampu mengonversi xml ke dalam bentuk DSL anko layout, Namun fitur konversi ini masih belum mampu mengonversi secara baik. 

Kembali lagi ke kodingan kita, setelah kita mendifinisikan item UI untuk recycler view, selanjutnya kita akan membuat adapter untuk item dan recycler view. kelas Adapter adalah sebagai berikut,

```kotlin
class FootballAdapter(var list : MutableList<Football>, var listener : (Football) -> Unit) : RecyclerView.Adapter<FootballAdapter.FootballViewHolder>() {
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): FootballViewHolder {
        return FootballViewHolder(FootballUI().createView(AnkoContext.create(parent.context, parent)))
    }

    override fun getItemCount(): Int = list.size


    override fun onBindViewHolder(holder: FootballViewHolder, position: Int) {
        holder.bindItem(list[position], listener)

    }

    inner class FootballViewHolder(itemView : View) : RecyclerView.ViewHolder(itemView){
        var imageView : ImageView
        var textView : TextView

        init {
            imageView = itemView.findViewById(FootballUI.imageId)
            textView = itemView.findViewById(FootballUI.nameId)
        }

        fun bindItem (items : Football, listener : (Football) -> Unit){
            textView.text = items.nama
            Glide.with(itemView.context).load(items.image).into(imageView)
            itemView.setOnClickListener {
                listener(items)
            }
        }
    }

}
```

Adapter kelas yang kita bangun diatas hampir tidak ada perbedaan dengan adapter pada umumnya namun, jelas hasil kembalian pada view pada View Holder tidak menggunakan Layout inflater melainkan menggunakan kelas API dari anko layout komponen anko context.

Segala layout sudah kita definisikan dan kita bangun mari kita lengkapi beberapa kelas yang lain untuk menjalankan program recycler tersebut. dimulai dari model, kita harus membangun kelas model sebagai berikut,

```kotlin
@Parcelize
data class Football(val nama : String, val image : Int, val keterangan : String) : Parcelable
```

Kodingan diatas mengindikasikan pembuatan kelas data dengan atribut text nama, image gambar, dan kembalian berupa Parcelable. Biasanya saya selalu menggunakan generate parcelable dari plugin tambahan Android studio namun, Kotlin sudah menyediakan fitur untuk mengatasi itu semua. Apabila saya menggunakan Parcelable secara konvensional maka baris kode dipastikan sangat banyak sesuai jumlah atribut yang dibuat. Namun dengan fitur Parcelize milik kotlin hasil kodingan menjadi lebih sederhana, kenapa? Karena anotasi Parcelize membuat graph sendiri dan menggenerate kelas pada folder build Android Studio, sehingga pastikan Anda me-rebuild project atau make project sesudah membangun parcelize tersebut. Untuk memperoleh fitur tersebut Anda disarankan untuk menambahakan baris kode berikut ke dalam build.gradle level App.

```groovy
androidExtensions{
    experimental = true
}
```

Selanjutnya kita membangun kelas SecondActivity untuk membuat Activity lanjutan ketika user meng-klik item recycler view, nah disini kita akan menerapkan Anko layout dengan inner class sebagai User Interfacenya supaya dapat melihat hasil layout tersebut, catatan bahwa ada sebagian kelas yang memang tidak menampilkan pada Preview Anko Support hal ini menjadi issue tersendiri.

```kotlin
class SecondActivity : AppCompatActivity() {

    companion object {
        val keteranganID = 3
        val POSITIONEXTRA = "position_extra"
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val intent = intent
        val list = intent.getParcelableExtra<Football>(POSITIONEXTRA)

        SecondActivityUI(list).setContentView(this)

    }

    internal class SecondActivityUI(var list: Football) : AnkoComponent<SecondActivity>{

        @RequiresApi(Build.VERSION_CODES.JELLY_BEAN_MR1)
        override fun createView(ui: AnkoContext<SecondActivity>) = with(ui){
            var position = 0
            linearLayout {
                orientation = LinearLayout.VERTICAL
                lparams(matchParent, matchParent)

                imageView(){
                    Glide.with(this).load(list.image).into(this)
                    id = FootballUI.imageId
                    padding = dip(10)

                    this@linearLayout.gravity = Gravity.CENTER_HORIZONTAL
                }.lparams(dip(80), dip(80))

                textView{
                    id = FootballUI.nameId
                    text = list.nama
                    textSize = sp(10).toFloat()
                    gravity = Gravity.CENTER_HORIZONTAL
                    padding = dip(10)
                }

                textView{
                    id = keteranganID
                    text = list.keterangan
                    gravity = Gravity.CENTER_HORIZONTAL
                    textAlignment = View.TEXT_ALIGNMENT_CENTER
                    padding = dip(10)
                }

            }
        }

    }
}
```

Hasil akhir adalah sebagai berikut,

<img src="/image.jpg" alt="drawing" width="300px"/>



Kesimpulannya adalah Anko layout cukup baik digunakan karena dapat menggunakan kembali view, kode dapat langsung kita sambung pada kodingan karena bersifat programmatically dan hasil run pada android tidak akan membenai CPU dan baterai. Bahkan Anda bisa membuat extensions function ataupun membuat view custom dari DSL anko layout dan bisa memadukan library anko yang lain yang mampu menghindar Boilerplate dan mendapatkan clean code. Namun, kekurangannya terletak pada untuk melihat hasil tampilan cukup ribet karena harus rebuild setiap ada penggantian layout tampilan. Baik sekian dari saya kurang lebihnya mohon maaf. Untuk source code bisa diperoleh [disini](https://github.com/Leviaran/football_club).