# Catatan Visual Basic .Net

_Catatan ini dibuat sebagai pengingat tentang pemrograman VB .Net_ . Di VB .Net mengerjakan project yg berkaitan dengan **aplikasi database untuk perkantoran** . Jadi kebanyakan data-datanya  berupa data text. Bisa untuk aplikasi di bidang administrasi atau keuangan (Akuntansi) . Sedang fokus ke pembuatan DataSet. Masih kesulitan memahami tentang table di dataset & bagaimana  melakukan query layaknya di table database **MySQL** . Ingin bisa menampilkan di console, data nama kolom dan data baris baris yg ada di bawah nama kolom itu. Untuk file yg di eksekusi sebagai sumber data sudah berupa **XML** . File XML ini di generate dari database MYSQL, yang di generate adalah data dari tabel nya.

Selanjutnya yg masih menjadi masalah adalah bagaimana bagamimana melakukan query terhadap data XML ini. Dibutuhkan kemampuan untuk mengenerate data dari tabel MySQL, melakukan query terhadap data yg ada di file XML dan kemudian menampilkannya di _console_ . Juga dibutuhkan kemampuan untuk melakukan **delete**, **update**, **insert** data ke file XML. Kemudian data di file XML ini dimasukan kembali ke database MySQL.


Akan mencoba tutorial di sini:

1. [DataSet](https://www.dotnetperls.com/dataset-vbnet)

   Setelah mengikuti tutorial di atas, pencapaian dalam percobaan coding yg berhasil hingga saat ini bisa di lihat di bawah ini:
   
   ![Tampilan Program Ketika Dijalankan](screenShootMembuatDatasetVB.png)



_XML_ dan _JSON_ sangat penting dalam urusan _web service_, kedua type file ini wajib dikuasai penggunaannya bersama dengan _Visual Basic .Net_ dan _C#_ di _Visual Studio_. Untuk membangun web service yang sepertinya mudah dan bisa dikerjakan untuk saat ini adalah dengan menggunakan **WCF** dan **ASP .NET** . Untuk web server nya menggunakan _IIS (Internet Information Service)_ yang versi **Express** .


Nantinya web service ini berguna untuk komunikasi data antara aplikasi **desktop**, **mobile** dengan **server MySQL** . Sehingga untuk interface aplikasi tetap menggunakan aplikasi desktop dan mobile. teknologi web hanya berlaku di backend. web service ini akan memperluas jangkauan dari hanya LAN sehingga bisa mencapai seluruh dunia menggunakan internet.
