# Catatan Visual Basic .Net

_Catatan ini dibuat sebagai pengingat tentang pemrograman VB .Net_ . Di VB .Net mengerjakan project yg berkaitan dengan **aplikasi database untuk perkantoran** . Jadi kebanyakan data-datanya  berupa data text. Bisa untuk aplikasi di bidang administrasi atau keuangan (Akuntansi) . Sedang fokus ke pembuatan DataSet. Masih kesulitan memahami tentang table di dataset & bagaimana  melakukan query layaknya di table database **MySQL** . Ingin bisa menampilkan di console, data nama kolom dan data baris baris yg ada di bawah nama kolom itu. Untuk file yg di eksekusi sebagai sumber data sudah berupa **XML** . File XML ini di generate dari database MYSQL, yang di generate adalah data dari tabel nya.

Selanjutnya yg masih menjadi masalah adalah bagaimana bagamimana melakukan query terhadap data XML ini. Dibutuhkan kemampuan untuk mengenerate data dari tabel MySQL, melakukan query terhadap data yg ada di file XML dan kemudian menampilkannya di _console_ . Juga dibutuhkan kemampuan untuk melakukan **delete**, **update**, **insert** data ke file XML. Kemudian data di file XML ini dimasukan kembali ke database MySQL.


Akan mencoba tutorial di sini:

1. [DataSet](https://www.dotnetperls.com/dataset-vbnet)

   Setelah mengikuti tutorial di atas, pencapaian dalam percobaan coding yg berhasil hingga saat ini bisa di lihat di bawah ini:
   
   ![Tampilan Program Ketika Dijalankan](screenShootMembuatDatasetVB.png)


   Untuk source code dari program di atas bisa dilihat disini:
   
   ```vb.net
   Imports System

   Imports System.Console

   Imports System.Data.SqlClient

   Imports System.Data

   Imports System.Data.Odbc

   Public Class Form1
      Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

         ' Dua Tabel

         Dim table1 As DataTable = New DataTable("pasien")

         table1.Columns.Add("idPasien")

         table1.Columns.Add("namaPasien")

         table1.Rows.Add(1, "Sam")

         table1.Rows.Add(2, "Mark")


         Dim table2 As DataTable = New DataTable("Obat")

         table2.Columns.Add("idObat")

         table2.Columns.Add("namaObat")

         table2.Rows.Add(1, "atenolol")

         table2.Rows.Add(2, "amoxilin")


         ' Membuat sebuah Dataset, dan meletakan kedua tabel di dalam dataset itu.

         Dim set1 As DataSet = New DataSet("office")

         set1.Tables.Add(table1)

         set1.Tables.Add(table2)


         ' Visualize DataSet

         Console.WriteLine(set1.GetXml())

      End Sub
   End Class
   
   ```
   
   selanjutnya akan mencoba membuat agar apa yang sebelumnya ditampilkan di **Console/Terminal** bisa di simpan ke dalam bentuk file XML.
   
   Berikut ini tampilan visual dari program yang memiliki kemampuan untuk menyimpan ke dalam file XML, dataset yg saya buat diatas dan      telah saya tampilkan ke dalam Terminal:
   
   ![Tampilan program ketika dijalankan](screenShootBikinFileXMLDataSet.png)
   
   Di bawah ini screen shoot dari file XML yang berhasil kita buat. File XML telah tersimpan di dalam direktori, sesuai dengan alamat      direktori yang telah ditulis di codingan program ini.
   
   ![File XML tersimpan di dalam direktory](screenShootFileXMLData1.png)
   
   Di bawah ini screen shoot dari tampilan isi file XML yang berhasil dibuat:
   
   ![Isi file XML ditampilkan di Notepad++](screenShootXMLData1.png)
   
   Untuk source code dari program yg bisa menyimpan Dataset yang telah dibuat ke dalam file XML, bisa dilihat di bawah ini:
   
   ```vb.net
   Imports System

   Imports System.Console

   Imports System.Data.SqlClient

   Imports System.Data

   Imports System.Data.Odbc



   Public Class Form2
      Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

         ' Dua Tabel

         Dim tabel1 As DataTable = New DataTable("pasien")

         tabel1.Columns.Add("idPasien")

         tabel1.Columns.Add("namaPasien")

         tabel1.Rows.Add(1, "Sam")

         tabel1.Rows.Add(2, "Mark")


         Dim tabel2 As DataTable = New DataTable("obat")

         tabel2.Columns.Add("idObat")

         tabel2.Columns.Add("namaObat")

         tabel2.Rows.Add(1, "atenolol")

         tabel2.Rows.Add(2, "amoxilin")


         Dim set1 As DataSet = New DataSet("office")

         set1.Tables.Add(tabel1)

         set1.Tables.Add(tabel2)


         set1.WriteXml("D:\StevenNathaniel\Proyek VB NET\DevExpress7\DevExpress7\data1.xml")


      End Sub
   End Class
   
   ```
   File yang berhasil dibuat dari program diatas, bisa dilihat [**disini**](https://github.com/rootonunix/gambar/blob/master/data1.xml)
## Query File XML

Selanjutnya akan mencoba melakukan query terhadap file XML , untuk menampilkan column dan data tertentu. Mencoba mencari info dengan kata kunci:

**vb .net + query file xml**

Menemukan halaman ini:

[.NET Language-Integrated Query for XML Data](https://msdn.microsoft.com/en-us/library/bb308960.aspx)

jadi harus belajar tentang **LINQ**, mencoba memahirkan penggunaan LINQ di file **XML**. sambil juga  mencoba untuk menerapkan XML yg sudah ada di **DevExpress Report** . 

_Ada tutorial tentang membuat file XML dari scratch:_

[Creating XML from Scratch](https://msdn.microsoft.com/en-us/library/bb308960.aspx#xlinqoverview_topic2e)


_Tutorial tentang membuat file XML menggunakan LINQ tapi masih tanpa ada source code VB .NET nya. masih cari yg ada VB .NET nya:_

[LINQ to XML : Creating complete XML document](https://blogs.msdn.microsoft.com/wriju/2008/02/28/linq-to-xml-creating-complete-xml-document/)

sudah berhasil melakukan **query** terhadap file XML menggunakan **LINQ** dengan mengikuti tutorial di sini:

[LINQ to XML in VB.NET](http://stackoverflow.com/questions/1066213/linq-to-xml-in-vb-net/1066418#1066418)

**Source code yang di uji cobakan di Visual Studio 2015:**

```vb.net
Imports System

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Data.Odbc


Module fileXML

    Dim data1Xml = <Xml>
                       <office>
                           <pasien>
                               <idPasien>1</idPasien>
                               <namaPasien>Sam</namaPasien>
                           </pasien>
                           <pasien>
                               <idPasien>2</idPasien>
                               <namaPasien>Mark</namaPasien>
                           </pasien>
                           <obat>
                               <idObat>1</idObat>
                               <namaObat>atenolol</namaObat>
                           </obat>
                           <obat>
                               <idObat>2</idObat>
                               <namaObat>amoxilin</namaObat>
                           </obat>
                       </office>
                   </Xml>

    Sub xmlKueri()

        Dim data1Doc = System.Xml.Linq.XDocument.Parse(data1Xml.ToString())

        Dim obats = From obat In data1Doc...<obat> Select obat


        For Each obat In obats

            Console.WriteLine("ID obat {0}", obat.<idObat>.Value)

            Console.WriteLine("Nama obat {0}", obat.<namaObat>.Value)
        Next

    End Sub




End Module

Public Class Form3

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click


        Call xmlKueri()


    End Sub
End Class
```

sekarang sudah berhasil membuat query menggunakan **LINQ** untuk menampilkan data dari file XML yg merupakan _hasil generate dari server MySQL_. Source code nya bisa dilihat di bawah ini:

```vb.net
Imports System

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Data.Odbc



Module fileXML2

    Dim data2XML = <?xml version="1.0" standalone="yes"?>
                   <NewDataSet>
                       <xs:schema id="NewDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
                           <xs:element name="NewDataSet" msdata:IsDataSet="true" msdata:UseCurrentLocale="true">
                               <xs:complexType>
                                   <xs:choice minOccurs="0" maxOccurs="unbounded">
                                       <xs:element name="Table">
                                           <xs:complexType>
                                               <xs:sequence>
                                                   <xs:element name="idpegawai" type="xs:string" minOccurs="0"/>
                                                   <xs:element name="namapegawai" type="xs:string" minOccurs="0"/>
                                                   <xs:element name="alamat" type="xs:string" minOccurs="0"/>
                                               </xs:sequence>
                                           </xs:complexType>
                                       </xs:element>
                                   </xs:choice>
                               </xs:complexType>
                           </xs:element>
                       </xs:schema>
                       <Table>
                           <idpegawai>PG00001</idpegawai>
                           <namapegawai>Steven Nathaniel</namapegawai>
                           <alamat>Pasar Baru</alamat>
                       </Table>
                       <Table>
                           <idpegawai>PG00002</idpegawai>
                           <namapegawai>Steve Jobs</namapegawai>
                           <alamat>Klandasan</alamat>
                       </Table>
                       <Table>
                           <idpegawai>PG00004</idpegawai>
                           <namapegawai>Yulia</namapegawai>
                           <alamat>Kampung Baru</alamat>
                       </Table>
                       <Table>
                           <idpegawai>PG00005</idpegawai>
                           <namapegawai>Maria</namapegawai>
                           <alamat>Klandasan</alamat>
                       </Table>
                       <Table>
                           <idpegawai>PG00007</idpegawai>
                           <namapegawai>Budi</namapegawai>
                           <alamat>Komplek Wika</alamat>
                       </Table>
                       <Table>
                           <idpegawai>PG00008</idpegawai>
                           <namapegawai>Ahmad</namapegawai>
                           <alamat>BDS</alamat>
                       </Table>
                   </NewDataSet>


    Sub xmlQueri2()

        Dim data2DOC = System.Xml.Linq.XDocument.Parse(data2XML.ToString())

        Dim Tables = From Table In data2DOC...<Table> Select Table

        For Each Table In Tables

            Console.WriteLine("ID Pegawai{0}", Table.<idpegawai>.Value)

            Console.WriteLine("Nama Pegawai{0}", Table.<namapegawai>.Value)

            Console.WriteLine("Alamat Pegawai{0}", Table.<alamat>.Value)


        Next




    End Sub

End Module

Public Class Form4
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Call xmlQueri2()

    End Sub
End Class

```
Dalam contoh-contoh di atas, data XML nya masih dimasukan ke dalam module, _akan mencoba yang data XML nya di load dari file XML_.

Berikut ini contoh source code yang berhasil meload data dari file XML dan menampilkannya di console:

```vb.net
Imports System

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Xml


Public Class Form6
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim xmlDataSet As New DataSet()

        xmlDataSet.ReadXml("D:\StevenNathaniel\Proyek VB NET\DevExpress7\DevExpress7\datasetPegawai.xml")

        Console.WriteLine(xmlDataSet.GetXml())

    End Sub
End Class
```

hasil tampilan dari source code diatas berupa **layout XML** yang dimulai dan diakhiri dengan tag **Dataset**.

Source code berikut ini berhasil melakukan query data dari file **XML**, jadi dari source code di atas dimasukan data XML yg berhasil di dapatkan ke dalam query **LINQ** dan ditampilkan hasil query nya di console. Jadi data yang ditampilkan tidak lagi berwujud XML:

```vb.net
Imports System

Imports System.Linq

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Xml

Public Class Form7
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim xmlDataSet As New DataSet()

        xmlDataSet.ReadXml("D:\StevenNathaniel\Proyek VB NET\DevExpress7\DevExpress7\datasetPegawai.xml")

        Console.WriteLine(xmlDataSet.GetXml)


        Dim data2Doc = System.Xml.Linq.XDocument.Parse(xmlDataSet.GetXml)

        Dim Tables = From Table In data2Doc...<Table> Select Table

        For Each Table In Tables

            Console.WriteLine("ID Pegawai {0}", Table.<idpegawai>.Value)

            Console.WriteLine("Nama Pegawai {0}", Table.<namapegawai>.Value)

            Console.WriteLine("Alamat {0}", Table.<alamat>.Value)

        Next

    End Sub
End Class
```

Format tampilan cetak data ke console nya sudah diperbaiki dari source code diatas, sehingga tampilan data di console nya lebih rapi dan mudah di baca. Source code penyempurnaannya seperti di bawah ini:

```vb.net
Imports System

Imports System.Linq

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Xml

Public Class Form7
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim xmlDataSet As New DataSet()

        xmlDataSet.ReadXml("D:\StevenNathaniel\Proyek VB NET\DevExpress7\DevExpress7\datasetPegawai.xml")

        Console.WriteLine(xmlDataSet.GetXml)


        Dim data2Doc = System.Xml.Linq.XDocument.Parse(xmlDataSet.GetXml)

        Dim Tables = From Table In data2Doc...<Table> Select Table

        For Each Table In Tables

            Console.WriteLine("ID Pegawai {0} : {1}", Chr(9), Table.<idpegawai>.Value)

            Console.WriteLine("Nama Pegawai {0} : {1}", Chr(9), Table.<namapegawai>.Value)

            Console.WriteLine("Alamat {0} {1} : {2}", Chr(9), Chr(9), Table.<alamat>.Value)

            Console.WriteLine()


        Next

    End Sub
End Class
```

Source code untuk menyusun hasil query yang menampilkan data-data dari file XML ke dalam bentuk tabel di console:

```vb.net
Imports System

Imports System.Linq

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Xml


Public Class Form10
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim xmlDataSet As New DataSet()

        xmlDataSet.ReadXml("D:\StevenNathaniel\Proyek VB NET\DevExpress7\DevExpress7\datasetPegawai.xml")

        Dim data2Doc = System.Xml.Linq.XDocument.Parse(xmlDataSet.GetXml)

        Dim Tables = From Table In data2Doc...<Table> Select Table

        Console.WriteLine("{0, -15} {1, -20} {2, -5}", "ID Pegawai", "Nama Pegawai", "Alamat")

        For Each Table In Tables


            Console.WriteLine("{0, -15} {1, -20} {2, -5}", Table.<idpegawai>.Value, Table.<namapegawai>.Value, Table.<alamat>.Value)



        Next

        Console.ReadKey()


    End Sub
End Class
```

_XML_ dan _JSON_ sangat penting dalam urusan _web service_, kedua type file ini wajib dikuasai penggunaannya bersama dengan _Visual Basic .Net_ dan _C#_ di _Visual Studio_. Untuk membangun web service yang sepertinya mudah dan bisa dikerjakan untuk saat ini adalah dengan menggunakan **WCF** dan **ASP .NET** . Untuk web server nya menggunakan _IIS (Internet Information Service)_ yang versi **Express** .


Nantinya web service ini berguna untuk komunikasi data antara aplikasi **desktop**, **mobile** dengan **server MySQL** . Sehingga untuk interface aplikasi tetap menggunakan aplikasi desktop dan mobile. teknologi web hanya berlaku di backend. web service ini akan memperluas jangkauan dari hanya LAN sehingga bisa mencapai seluruh dunia menggunakan internet.


## Keberhasilan Membuat Fitur untuk Search Data dari Server MySQL dan Kemudian Simpan Data Ke Dalam File XML, Untuk Kemudian Di Buat Report, Bisa Preview Report atau Langsung Simpan Report ke Dalam Bentuk File PDF


Source code nya:

```vb.net
Imports Microsoft.VisualBasic

Imports System

Imports System.Linq

Imports System.Console

Imports System.Data.SqlClient

Imports System.Data

Imports System.Data.Odbc

Imports System.Xml

Imports System.Drawing

Imports System.Drawing.Printing

Imports System.Windows.Forms

Imports DevExpress.XtraReports.UI

Imports DevExpress.Data

Imports DevExpress.DataAccess

Imports DevExpress.DataAccess.ObjectBinding

Imports DevExpress.DataAccess.Sql

Imports DevExpress.Data.Linq

Imports DevExpress.DataAccess.ConnectionParameters

Imports System.Collections.Generic



Module TulisFileXML2

    'Dim koneksi As New OdbcConnection("DSN=latihan")

    'Dim perintah As OdbcCommand

    'Dim myData As New DataSet

    'Dim kotakID As String


    'Public Sub tulisDataXML()



    '    Try



    '        koneksi.Open()

    '        Console.WriteLine("Koneksi Berhasil")

    '        Dim dAdaptar As OdbcDataAdapter = New OdbcDataAdapter()
    '    Catch ex As Exception

    '    End Try
    'End Sub

End Module


Public Class Form5
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim koneksi As New OdbcConnection("DSN=latihan")

        Dim perintah As OdbcCommand

        Dim myData As New DataSet

        Dim kotakID As String



        Try



            koneksi.Open()

            Console.WriteLine("Koneksi Berhasil")

            ' Dim dAdaptar As OdbcDataAdapter = New OdbcDataAdapter("SELECT * FROM pegawai where idpegawai='PG00001'", koneksi)

            Dim dAdaptar As OdbcDataAdapter = New OdbcDataAdapter("SELECT * FROM pegawai where idpegawai='" + TextBox1.Text + "'", koneksi)

            dAdaptar.Fill(myData)

            myData.WriteXml("D:\StevenNathaniel\Proyek VB NET\DevExpress8\DevExpress8\dataPegawai.xml", XmlWriteMode.WriteSchema)

            Console.WriteLine("Behasil Tulis Data Ke XML")

            koneksi.Close()



        Catch ex As OdbcException

            Console.WriteLine("Terjadi Error : " & ex.ErrorCode & " - " & ex.Message)

        Finally

            koneksi.Dispose()


        End Try


        Dim laporan As New XtraReport1()

        'Dim printTool As New ReportPrintTool(laporan)

        'printTool.Report.CreateDocument()

        'printTool.ShowPreviewDialog()

        laporan.ExportToPdf("D:\StevenNathaniel\Proyek VB NET\DevExpress8\DevExpress8\laporan1.pdf")

    End Sub
End Class
```



**Source code yang shahih untuk membuat file PDF yang berisi 1 halaman PDF:**

```vb.net
Imports DevExpress.Pdf

Imports System

Imports System.Drawing

Imports System.IO


Public Class Form4
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        'Buat dokumen PDF dengan 1 halaman kosong ukuran letter

        Dim dokumenPDF As New PdfDocumentProcessor

        dokumenPDF.CreateEmptyDocument()

        Dim halamanPDF As PdfPage = dokumenPDF.AddNewPage(PdfPaperSize.Letter)

        dokumenPDF.SaveDocument("C:\Users\StevenNathaniel\AppData\Local\Temp\file5.pdf")


    End Sub
End Class
```

**Source code yang sudah berhasil untuk membuat file PDF dan menyimpannya menggunakan FileSaveDialog, dengan file name dan file directory masih ditentukan secara manual oleh user:**

```vb.net
Imports DevExpress.Pdf

Imports System

Imports System.Drawing

Imports System.IO




Public Class Form6

    Dim namafile As String

    Dim alamatFile As String

    Dim dokumenPDF As New PdfDocumentProcessor

    Dim halamanPDF As PdfPage

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        SaveFileDialog1.ShowDialog()



    End Sub

    Private Sub SaveFileDialog1_FileOk(sender As Object, e As ComponentModel.CancelEventArgs) Handles SaveFileDialog1.FileOk

        dokumenPDF.CreateEmptyDocument()

        halamanPDF = dokumenPDF.AddNewPage(PdfPaperSize.Letter)


        namafile = SaveFileDialog1.FileName

        Console.WriteLine(namafile)

        dokumenPDF.SaveDocument(namafile)


    End Sub

    Private Sub Form6_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        SaveFileDialog1.Filter = "pdf file (*.pdf)|*.pdf"

        SaveFileDialog1.DefaultExt = "pdf"

        SaveFileDialog1.InitialDirectory = "C:\Users\StevenNathaniel\AppData\Local\Temp"

        'Dim dokumenPDF As New PdfDocumentProcessor

        'dokumenPDF.CreateEmptyDocument()

        'halamanPDF = dokumenPDF.AddNewPage(PdfPaperSize.Letter)

    End Sub
End Class
```


**Source code yang sudah berhasil untuk membuat file XML dan menyimpannya menggunakan FileSaveDialog, dengan file name dan file directory masih ditentukan secara manual oleh user:**

```vb.net
Imports System.Console

Imports System.IO

Imports System.Data.SqlClient

Imports System.Data

Imports System.Data.Odbc

Imports System.Xml

Imports System.Drawing

Imports System.Drawing.Printing

Imports System.Windows.Forms

Imports DevExpress.XtraReports.UI

Imports DevExpress.Data

Imports DevExpress.DataAccess

Imports DevExpress.DataAccess.ObjectBinding

Imports DevExpress.DataAccess.Sql

Imports DevExpress.Data.Linq

Imports DevExpress.DataAccess.ConnectionParameters

Imports System.Collections.Generic



Public Class Form2

    Dim koneksi As New OdbcConnection("DSN=latihan")

    Dim perintah As New OdbcCommand

    Dim myData As New DataSet

    Dim kotakID As String

    Dim xmlDataSet As New DataSet

    Dim path As String = My.Application.Info.DirectoryPath

    Dim namaFile As String


    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Try

            Dim dAdapter As OdbcDataAdapter = New OdbcDataAdapter("SELECT * FROM pegawai WHERE idpegawai='" + TextBox1.Text + "'", koneksi)

            dAdapter.Fill(myData)

            SaveFileDialog1.ShowDialog()



        Catch ex As Exception

        End Try



    End Sub

    Private Sub Form2_Load(sender As Object, e As EventArgs) Handles Me.Load

        SaveFileDialog1.Filter = "XML File(*.xml)|*.xml"

        SaveFileDialog1.DefaultExt = "xml"

        SaveFileDialog1.InitialDirectory = "C:\Users\StevenNathaniel\AppData\Local\Temp"

        Try

            koneksi.Open()

            Console.WriteLine("Koneksi Berhasil")
        Catch ex As Exception

        End Try

    End Sub

    Private Sub SaveFileDialog1_FileOk(sender As Object, e As System.ComponentModel.CancelEventArgs) Handles SaveFileDialog1.FileOk

        namaFile = SaveFileDialog1.FileName

        Console.WriteLine(namaFile)

        Console.WriteLine()

        myData.WriteXml(namaFile, XmlWriteMode.WriteSchema)

        Console.WriteLine("Berhasil Tulis Data XML")

        Console.WriteLine()

        Console.WriteLine("Tampilan Isi File XML:")

        Console.WriteLine()

        Console.WriteLine(myData.GetXml)

        Console.WriteLine()

        Console.WriteLine("Data yang ditulis dalam file XML:")

        Console.WriteLine()


        ' Tampilkan data dalam format tabel sederhana

        Dim data2Doc = System.Xml.Linq.XDocument.Parse(myData.GetXml)

        Dim Tables = From Table In data2Doc...<Table> Select Table

        Console.WriteLine("{0, -15} {1, -20} {2, -5}", "ID Pegawai", "Nama Pegawai", "Alamat")

        For Each Table In Tables

            Console.WriteLine("{0, -15} {1, -20} {2, 5}", Table.<idpegawai>.Value, Table.<namapegawai>.Value, Table.<alamat>.Value)

            Console.WriteLine()

        Next

        koneksi.Close()

        koneksi.Dispose()

    End Sub
End Class
```

**Source code untuk menyimpan file PDF hasil dari report yg dikonversi ke file PDF. Pembuatan program ini melibatkan DevExpress:**
```vb.net
Imports System.Console

Imports DevExpress.Pdf

Imports System

Imports System.IO

Imports System.Data.SqlClient

Imports System.Data

Imports System.Data.Odbc

Imports System.Xml

Imports System.Drawing

Imports System.Drawing.Printing

Imports System.Windows.Forms

Imports DevExpress.XtraReports.UI

Imports DevExpress.Data

Imports DevExpress.DataAccess

Imports DevExpress.DataAccess.ObjectBinding

Imports DevExpress.DataAccess.Sql

Imports DevExpress.Data.Linq

Imports DevExpress.DataAccess.ConnectionParameters

Imports System.Collections.Generic



Public Class Form3

    Dim namaFile As String

    'Dim laporan As New XtraReport1()

    'Dim printTool As New ReportPrintTool(laporan)



    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click

        Dim laporan As New XtraReport1

        Dim printTool As New ReportPrintTool(laporan)

        printTool.Report.CreateDocument()

        printTool.ShowPreviewDialog()


        SaveFileDialog1.ShowDialog()


    End Sub

    Private Sub Form3_Load(sender As Object, e As EventArgs) Handles MyBase.Load

        'Dim laporan As New XtraReport1()

        SaveFileDialog1.Filter = "PDF File(*.pdf)|*.pdf"

        SaveFileDialog1.DefaultExt = "pdf"

        SaveFileDialog1.InitialDirectory = "C:\Users\StevenNathaniel\AppData\Local\Temp"

    End Sub

    Private Sub SaveFileDialog1_FileOk(sender As Object, e As System.ComponentModel.CancelEventArgs) Handles SaveFileDialog1.FileOk

        Dim laporan As New XtraReport1()


        namaFile = SaveFileDialog1.FileName

        laporan.ExportToPdf(namaFile)


    End Sub
End Class
```

