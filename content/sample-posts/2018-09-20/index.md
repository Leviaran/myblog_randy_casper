---
title: "Android Road Map 1"
category: "android"
author: "randy"
date: "2018-09-20"
cover: "/images/roadmap/map.jpeg"
tags:
    - kotlin
    - android
    - android roadmap 
---

**Mungkin dari teman-teman** masih bingung apa saja yang diperlukan untuk memulai perjalanan  menjadi Android Developer. Sayangnya perjalanan itu sangat jauh, perlu bekal seperti latihan dan proses yang panjang. Namun, sebelum Anda memulai perjalan itu Anda harus tahu tujuan, kenapa memilih mengikuti perjalanan ini? Kalau Anda sedang mencari kerja atau belajar silakan ikuti. Tapi Anda harus ingat dalam setiap perjalanan bahwa setiap langkah atau proses memerlukan konsistensi. Apabila Anda enggan melakukannya jangan harap bisa memperoleh hasilnya yang maksimal. Saya akan membuat tahapan belajar Android development, ini opini saya pribadi, referensi dari pengembangan Ios, dan inspirasi saya dari Mindork. Karena tulisan ini begitu panjang, tentu saya akan pisah menjadi dua tulisan. Perlu diperhatikan bahwa yang saya tuliskan diini berdasarkan pengalaman saya, dan beberapa referensi tulisan yang ada.

##### Tulisan ini akan terus diperbaiki dan ditambahkan berdasarkan teknologi yang berkembang saat ini.



#### Perjalanan ini ditujukan bagi:

- Siapapun yang ingin belajar menjadi developer Android
- Android Developer yang menjadi lebih ahli dan berkembang
- Android Developer yang menyiapkan interview dan pengetahuan tambahan



#### Syarat utama:

- Jangan malas membaca terkhusus membaca dokumentasi.

- Jangan mudah putus asa.

- Berani mengambil resiko dan bersiap untuk gagal.

- Mampu berbahasa Inggris.


------



1. ### **Problem Solving** 

   Kenapa problem solving? sebelum Anda jauh melangkah problem solving merupakan bekal pertama yang harus Anda bawa. Kenapa? karena selama Anda mengembangkan sesuatu khususnya Android, Anda akan dituntut untuk menyelesaikan permasalahan secara jelas dan runtut sesuai alur. Tentunya hal ini tidak hanya digunakan untuk masalah pengembangan saja namun lebih umum. Problem solving disini mengacu pada Algoritma atau secara luas adalah computer science untuk menyelesaikan masalah yang berkaitan dengan logika. Apalagi problem solving biasanya diterapkan pada saat test masuk kerja dalam perusahaan, Anda akan diuji sejauh mana. Sekilas mirip-mirip TPA untuk berpikir secara kritis. Untuk mengukur sejauh mana problem solving yang dapat Anda selesaikan, Anda bisa membuka [Hackerrank](https://www.hackerrank.com), [Hackerearth](https://www.hackerearth.com/), [TopCoder](https://www.topcoder.com/challenges/), [Coderbyte](https://www.coderbyte.com/), [Codility](https://app.codility.com/programmers/) lalu latih setiap hari. 

      ![hackerrank](https://cdn-images-1.medium.com/max/800/1*FmGJWaYjW-v4OmWDSAPXeQ.png)

   Coba perhatikan data berikut yang saya ambil dari laman [Hackerrank](https://research.hackerrank.com/developer-skills/2018/). Nah berdasarkan data diatas jelas Problem solving merupakan prioritas utama untuk suatu pekerjaan terkhusus pekerjaan yang berkaitan dengan Pemrograman. Selama Anda memegang Problem solving dengan baik Anda mampu untuk menyelesaikan masalah secara efektif dan efisien. Meski semua orang akan memperoleh problem solving yang berbeda-beda tapi indikator problem solving tetap berdasarkan pada asas efektif dan efisien. 



2. ### **Kuasai Bahasa pemrograman terlebih dahulu**

   Meski klasik tapi bahasa pemrograman merupakan hal yang fundamental, bagaimana bisa kamu membuat program komputer tanpa dapat berkomunikasi dengannya? Bahasa juga harus dipilih jika Ingin membuat Android maka bahasa yang digunakan secara pengembangan native dapat menggunakan bahasa Java dan Kotlin. Namun, apabila Anda tidak bersedia membuat pengembangan Android secara native alternatif lain bisa menggunakan React native, Vue Native, dan Flutter. Dua diantaranya menggunakan bahasa Javascript sedangkan Flutter menggunakan Bahasa Dart. Kunci mempelajari Bahasa komputer adalah dengan mengetahui paradigma bahasa yang digunakan, di masa modern ini Object Oriented Programming (OOP) masih relevan digunakan dan fundamental hampir di setiap bahasa pemrograman. Paradigma merupakan kunci untuk mengusai alur bahasa yang digunakan. Selain OOP, ada juga yang terus berkembang dan mulai banyak digunakan yakni paradigma functional programming dan reactive programming. Ketika Anda sudah mengusai paradigma dengan baik maka selama bahasa pemrograman yang Anda gunakan berganti-ganti Anda tidak akan kesulitan untuk mengimplementasikanya. Berbedaan diantara bahasa pemrograman yang ada terletak pada keyword, API, sintaksis, Flow, dan compiler. Anda bisa belajar bahasa dengan mudah di [tutorial point](https://www.tutorialspoint.com/). Banyak bahasa tersedia disana dan dapat diakses secara gratis baik online maupun offline bisa juga di [Kotlin](https://try.kotlinlang.org/), [Kotlin Blog](https://blog.kotlin-academy.com), atau [Kotlin indonesia](http://kotlin.id/). Bagi yang mau referensi bisa nge-blog di [Dzone](https://dzone.com/java-jdk-development-tutorials-tools-news), [Baeldung](https://www.baeldung.com/kotlin-lazy-initialization), [Kotlin AntonioLeiva](https://antonioleiva.com/kotlin/) khusus bahasa indonesia di [Codepolitan](https://www.codepolitan.com/interactive-coding/java). Bagi yang memerlukan pdf bisa mampir di [GoalKicker](http://goalkicker.com/), [Packtpub](https://www.packtpub.com/packt/offers/free-learning).

3. ### **Kenali Kotlin** 

   Apakah saya harus belajar Java atau Kotlin dulu? Pertanyaan tersebut sering saya lihat dan bolak-balik ditanyakan. Saya sarankan Anda langsung belajar Kotlin, Kotlin sebenarnya bukan barang yang tidak wajib tapi setidaknya direkomendasikan. Saya perlu tekankan bahwa bahasa pemrograman semakin banyak, kita tidak tahu kedepan ada bahasa baru atau tidak untuk pengembangan Android. Konsep bahasa pada setiap platfom pada dasarnya memiliki persamaan, semua kembali pada paradigma yang kita gunakan untuk membuat suatu program. Anda harus menguasai dasar apa itu paradigma seperti OOP, Functional programming, dengan membawa bekal seperti itu niscaya Anda tidaka kesulitan untuk migrasi atau mempelajari bahasa pemrograman baru. 

   ​	Kotlin sendiri menjadi bahasa resmi Android pada Google I/O tahun 2017 kemarin. Karena kenyamanan fitur-fitur yang diberikan oleh kotlin, maka banyak developer mulai migrasi dari Java ke Kotlin, sehingga perkembangan dari segi projek Android, Kotlin semakin meningkat pesat.

4. ### **Kenali Android Studio IDE**

   Ini jelas penting, Anda yang setiap waktu mengembangkan Android pasti berkutat dengan editor Android Studio. Sebelum menggunakannya Anda harus belajar beradaptasi bagaimana cara menavigasikan menu-menu yang ada pada Android Studio. Saya tidak akan membahas kegunaan masing-masing menu yang ada. Anda harus mengeksplor sendiri menu-menu baru, usahakan untuk memaksimalkan fitur-fitur Android studio untuk membantu mempercepat pengembangan. Anda bisa mendapatkan pengalaman tips dan trik di laman [berikut](https://medium.com/@mmbialas/50-android-studio-tips-tricks-resources-you-should-be-familiar-with-as-an-android-developer-af86e7cf56d2). Anda wajib mengenali navigasi gradle, logcat, terminal, tools, build, message, plugin, navigation view, build variant, dan git.

5. ### **Kenali Version Control GIT**

   Bagi yang suka bergelut dibidang kode pasti Anda sudah mengenal Github. Namun harus saya tekankan, **Github** berbeda dengan **Git**. Github adalah provider untuk menyimpan proyek secara bersama yang dikenal sebagai repositori menggunakan sistem pengontrol Git. Sedangkan Git digunakan untuk mengatur atau mengelola versi dari kode sumber program, saya analogikan bahwa Git merupakan mesin Github. Alternatif Github juga bisa kita pakai, contoh Gitlab, SourceForge, dan Bitbucket. Anda bisa belajar bagaimana menjalankan Git di laman [berikut](https://guides.github.com/activities/hello-world/), atau dalam [bahasa Indonesia](https://github.com/petanikode/belajar-git), atau yang [interaktif](https://try.github.io/). Anda mungkin bertanya-tanya mengapa ini penting? Contoh kasus adalah Anda membuat projek, Anda akan selalu menambah-nambah kode untuk fungsi-fungsi baru, nah apabila ternyata pada fungsi yang baru ada yang bermasalah Anda bisa kembali ke kode yang belum ditambahkan, mirip checkpoint atau pembuatan restore point. Contoh lain adalah saat membangun projek secara komunal, Git akan membantu Anda untuk mengerjakan kode secara bersama-sama misal ada penambahan dari berbagai pihak oleh karena itu open source merupakan barang populer untuk Git.

6. ### **Kenali Komponen Utama Pengembangan Android**

   - Ada [empat komponen utama](https://developer.android.com/guide/components/fundamentals) dalam Android yakni Activity, Service, Broadcast Receiver, dan Content provider. Selain itu Anda harus mengetahui dan memahami [Activity Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle) yang merupakan bagian dari Activity. 

   - Memahami dan mengetahui [Fragment](https://developer.android.com/guide/components/fragments), khususnya Fragment Lifecycle fragment. Meski sama dengan Activity namun fragment ini lebih dinamis dibandingkan dengan Activity. Banyak yang bertanya pada saya perbedaan Fragment dengan Activity. Sederhananya Fragment itu adalah ruang, sedangkan Activity adalah rumahnya. Jadi dalam rumah itu bisa ada banyak ruang, bisa Anda perbesar, ganti, atau bahkan hilangkan ruangan dari dalam rumah. Artinya fragment tidak dapat ditampilkan tanpa adanya Activity, Fragment bersifat dinamis, bisa diperbesar diperbanyak asal resource mencukupi ataupun diganti dengan fragment lain. Namun Fragment ini terkadang lebih susah mengimplementasikannya dan mengatur urutan/stack. Oleh karena itu Google merilis library khusus yakni [Navigation library](https://developer.android.com/topic/libraries/architecture/navigation/) yang merupakan salah satu dari komponen [Android Jetpack](https://developer.android.com/jetpack/). 

   - [Debugging](https://developer.android.com/studio/debug/), Debugging ini yang paling krusial, kadang banyak yang bertanya soal masalah debugging, contoh paling banyak adalah kenapa tidak menampilkan sesuatu.  Debugging bisa dilakukan dengan menelusuri kode yang dieksekusi bisa dari Method atapun class, apabila debugging diandroid, Anda biasanya akan berurusan dengan debugging lifecycle. Debugging bisa dilakukan dengan membuat perintah `Log.e(" track isi data adalah ${}")`,Buatlah Log tersebut dengan memperhatikan eksekusi Kode, kode dieksekusi secara interpreter sehingga dibaca dari atas kebawah. Anda bisa saja men-debug menggunakan [Timber](https://github.com/JakeWharton/timber). Konsep timber kurang lebih sama, namun lebih efektif karena tidak perlu mendefinisikan nama log. Debugging bisa dicek pada `logcat` pada Android Studio bila sembari menjalankan Aplikas sedangkan apabila debugging pada generate misal generate module Anda bisa mengecek pada `Build gradle`. Debugging juga bisa dilakukan menggunakan library pihak ketiga seperti [Stetho](https://facebook.github.io/stetho/). 

   - [Context](https://developer.android.com/reference/android/content/Context), Anda setidaknya mengetahui apa itu [context](https://blog.mindorks.com/understanding-context-in-android-application-330913e32514) pada Android, baik context Android activity maupun context application. Context berguna untuk mengambil segala resource yang ada pada Lingkungan Android. Context juga wajib dikelola, apabila Anda tidak mengelola Context dengan baik maka aplikasi Anda akan bermasalah seperti out of memory dll. Anda juga harus mampu membedakan level context, kesalaha penggunaan level context dapat mengakibatkan force close, seperti penggunaan application context dalam setiap Activity, nah application context sangatlah mahal, dan jangan sering-sering digunakan, gunakan hanya waktu pembuatan database atau komputasi utama yang melibatkan resource aplikasi secara keseluruhan, ada baiknya Anda membaca [ini](https://blog.mindorks.com/understanding-context-in-android-application-330913e32514), atau [ini](https://medium.freecodecamp.org/mastering-android-context-7055c8478a22).

   - [Configuration Change](https://developer.android.com/guide/topics/resources/runtime-changes), terkadang komponen ini tidak selalu diperhatikan dan selalu di matikan. apa itu configuration change? secara sederhananya perubahan konfigurasi saat Android dijalankan seperti perubahan rotasi layar. Nah, perubahan rotasi layar ini biasanya dimatikan oleh para pengembang Android, kenapa? karena saat layar berotasi baik desain mapun data juga akan berubah, Android akan berada pada state onCreate lagi, jadi tahapan saat layar berotasi pada lifecycle adalah onPause -> onSaveStateInstance -> onStop -> onDestroy -> onCreate -> onStart -> onResume. Desain juga berubah yang tadinya ditampilkan secara protrait lalu landscape, perilaku ini mirip responsive desain pada web, apabila tidak responsive maka hasil tampilan akan berantakan. Data juga akan berubah, sebaiknya apabila data terakhir mau ditampilkan kembali saat rotasi berlangsung bisa disimpan terlebih dahulu pada onSaveStateInstance(). 

   - Database Sqlite dan SharedPreferences,  Apabila membutuhkan penyimpanan dalam Android Anda dapat menggunakan Database Sqlite. Database Sqlite menyimpan data secara ERD dan kompleks sedangkan SharedPreferences merupakan data yang hanya mampu menyimpan satu jenis tipe data saja seperti String, tipe data primitif(int, short, long, byte, boolean, float, double ). Apabila Anda membutuhkan penyimpanan yang kompleks seperti sistem informasi maka Sqlite menjadi solusinya sedangkan untuk penyimpanan yang sederhana bisa menggunakan SharedPreferences seperti penyimpanan Cookies, Password, username, dll, tentunya sebelum menyimpan pastikan dienkripsi terlebih dahulu. Pengembangan Android tidak hanya terpatok pada Sqlite saja ada beberapa database yang dapat digunakan selain Sqlite, seperti Realm, Object Box, Room. dll. Apabila ingin tetap Sqlite dan mendukung ORM silakan coba GreenDao, DBFlow, ORMlite, dan SugarORM. 

   - Rest dan HTTP, Nah untuk pertukaran data ke Web diperlukan alat pendukung. secara konvensional tanpa library pun dapat dilakukan dengan memparsing json secara manual, namun tindakan ini sudah ditinggalkan karena membuat boilerplate atau kode makin banyak. Ada library khusus yang mampu menangani pertukaran data tersebut, yang paling terkenal adalah Retrofit dan Fast Android Networking (FAN). Sedangkan yang lain seperti Volley, okHttp juga masih dapat digunakan. 

   - [Thread](https://developer.android.com/reference/java/lang/Thread), siapapun yang pernah mengembangankan aplikasi secara paralel dengan java pasti sudah mengenal Thread. Thread digunakan untuk mengelola proses, bisa digunakan secara paralel ataupun seri, asynchronous, ataupun synchronous. Kenapa Perlu ada thread? secara sederhana Thread dapat mempercepat banyak pekerjaan dalam satu waktu secara bersamaan, mirip model pipelining, multitask, dll. Namun, Anda harus benar-benar mengalokasikan thread dengan tepat, kesalahan pengelolaan bisa mengakibatkan out of memory. Khusus Android Thread utama untuk mengelola tampilan atau disebut MainThread. Thread ini sebaiknya tidak diusik oleh thread lain. seperti pemanggilan API, pemrosesan yang membutuhkan waktu lama, dll. 

   - Service dan IntentService, Coba kenali Service dan intentService untuk membuat proses yang berjalan dilatar belakang/background process. contoh kasus adalah pembuatan alarm, music, network transaction, interaction content provider, dll. background service ini tidak memerlukan tampilan yang patut diperhatikan adalah reseouce yang digunakan untuk menjalankan dibelakang, usahakn untuk menggunakan resouce yang efektif dan mengoptimasi komputasi proses karena ini akan mempengaruhi kinerja baterai.

   - Kenali library-library pihak ketiga untuk mempercepat pengembangan Androidmu. Apabila ingin membuat library sendiri, usahakan untuk meriset dan memiliki perbedaan yang cukup signifikan. Jangan membuat library yang sudah ada, karena hanya membuang waktu Anda, kecuali Anda ingin meriset dan tentunya ada keunikan tersendiri. 

7. ### **Improve performa Android**

   - Gunakan [SparseArray atau ArrayMap](https://blog.mindorks.com/android-app-optimization-using-arraymap-and-sparsearray-f2b4e2e3dc47)

   - Menggunakan Caching 

   - Mendeteksi kebocoran memory, Anda bisa menggunakan [Leak Canary](https://github.com/square/leakcanary) untuk mendeteksi kelas atau fungsi mana yang mengonsumsi banyak resource atau RAM sehingga mengakibatkan Out Of Memory(OOM).

   - Mengelola penggunaan baterai.

   - Mengelola seberapa lama aplikasi dibuka.

   - [Mengurangi ukuran aplikasi](https://blog.mindorks.com/how-to-reduce-apk-size-in-android-2f3713d2d662) supaya lebih efektif dan efisien. Anda dapat menggunakan [Native code](https://randyarba.me/mengurangi-size-apk-pada-native-code) dan [App Bundle](https://medium.com/mindorks/android-app-bundle-6c65ce8105a1).

   - Mengelola alokasi ukuran bitmap/image pada Android supaya tidak terlalu besar. Hal ini dapat mempengaruhi proses dan menimbulkan OOM. Biasanya dengan menggunakan library pihak ketiga seperti Glide, Picasso, dll dapat mengatasi hal tersebut. Namun tetap saja apabila kita memuat image data dari asset dengan ukuran yang belum dioptimasi akan menimbulkan masalah yang sama. Anda bisa saja mengkonversi Bitmap/image tersebut kedalam WebP supaya ukuran menjadi lebih kecil supaya ukuran image pada asset tidak terlalu besar.

8. ### **Kenali [Android Architecture Component](https://developer.android.com/topic/libraries/architecture/)**

   Android Architecture Component(AAC) merupakan library yang dikembangkan oleh google untuk membantu pengembangan Android supaya lebih terstruktur dan sesuai standar google  sehingga menghasilkan aplikasi yang efektif dan efisien. AAC ini memuat banyak library dikhususkan untuk memperoleh pattern yang tepat untuk mengembangkan aplikasi Android. AAC sendiri apabila dilihat secara umum menggunakan pattern MVVM, namun tidak menutup kemungkinan Anda bisa mengimplementasikan MVP juga ddengan AAC.

   ​	Di tahun 2018 AAC menjadi salah satu komponen Android Jetpack. Android Jetpack kaya akan library-library yang menunjang pengembangan Android. Bila Anda sudah selesai dalam pengenalan AAC Anda bisa mempelajari Android Jetpack secara keberlanjutan dikarenakan Android Jetpack sendiri memiliki banyak fitur-fitur, Anda harus benar-benar fokus untuk mempelajari beberapa fitur tersebut. 

9. ### **Membuat Test Android**

   **Manual Testing**

   Testing merupakan hal yang penting guna memverifikasi apakah aplikasi sudah sesuai atau belum. pengecekan ini akan melibatkan instrumen dan indikator apakah fungsi-fungsi pada aplikasi sudah tervalidasi. Pengecekan ini dapat dilakukan di Android studio. Android studio sendiri memiliki fitur untuk membuat testing. Ada dua testing yang dapat dilakukan di Android studio, pertama unit testing untuk mengetahui fungsi, logika, dan alur yang bersifat abstrak tanpa melibatkan tampilan. 

   Contoh, jika Anda membuat aplikasi kalkulator, Anda diharuskan untuk memverifikasi hasil pengurangan apakah sudah sesuai atau belum. Karena tidak melibatkan tampilan otomati pengujian melalui unit testing tidak memerlukan emulator atau perangkat sungguhan. Berbeda dengan pengujian instrumen Android, Anda harus memvalidasi setiap alur interaksi/aktivitas user saat melakukan sesuatu dan memperoleh hasilnya hal ini melibatkan tampilan, sebagai contoh adalah menguji aplikasi berita, alur pertama user melihat pertama kali tampilan cardview, nah apakah cardview ini tertampil atau tidak, selanjutnya ada tampilan recyclerview, apakah recyclerview sudah sesuai tampilanny dan memiliki jumlah list yang sesuai pula. 

   Manual testing diatas dapat ditangani dengan memanfaatkan library yang tersedia, sebagai contoh untuk Unit Testing Anda dapat melakukannya dengan menggunakan JUnit, dan [Mockito](https://site.mockito.org/). Sedangkan pengujian Instrument Android dapat menggunakan [Esspresso Android testing](https://developer.android.com/training/testing/espresso/).



   **Automatic Testing**

   Pengujian secara otomatis ini hanya bisa dilakukan di cloud. pengujian ini tidak memerlukan bantuan android studio, Anda hanya cukup mengunggah file aplikasi (APK) dan serahkan semuanya ke cloud untuk menetahui hasilnya dari segi kualitas performanya. Anda juga dapat meng-emulasi banyak device jika Anda mengingkannya. katakanlah Anda membutuhkan 100 Android yang harus diuji, maka Anda tinggal mengklasifikasikan dan mengakategorikan Android apa saja yang akan Anda uji. 

   Anda juga dapat mengkustomasi instrument apa yang akan diuji, misal Anda sudah membuat file instrumen dari Android studio kemudian unggah file tersebut beserta aplikasinya. Perlu diketahui bahwa Automatic testing ini diperlukan biaya untuk menggunakannya, meski ada yang bersifat gratis namun hanya bersifat trial, diukur seberapa perangkat yang diuji dalam satu hari atau batas maksimal jumlah Android yang diemulasi. Anda bisa menggunakan automatic testing di Android Device Farm milik AWS, Testlab milik Google Firebase, dan Bitbar.


10. ### **Mempelajari RxJava**

  Bagi yang belum mengerti apa itu RxJava Anda bisa membuka link [berikut](https://github.com/ReactiveX/RxJava). RxJava merupakan library yang mampu mengelola konsep asynchronous dan program event based dengan menggunakan obesrvable. RxJava ini sangat populer sekali dikalangan Android Developer. Jika Anda sudah mengenal konsep dasar Android, Anda patut mempelajari library ini. RxJava memiliki paradigma reactive programming, dimana jargon mereka adalah *data adalah event dan event adalah data*. 

  Tentu yang paling mengesankan mengenai RxJava adalah kaya dengan operator untuk mengatur observable. Observable itu mirip kumpulan operan yang mengalir untuk dikelola atau diatur lebih lanjut hasil keluaran diatur oleh subscriber dan dikonsumsi oleh observer. Nah untuk lebih jelasnya soal observable dan subscriber Anda harus mengunjungi laman [ini](https://guides.codepath.com/android/RxJava). 



![gif code](https://media.giphy.com/media/Lny6Rw04nsOOc/giphy-downsized.gif)



