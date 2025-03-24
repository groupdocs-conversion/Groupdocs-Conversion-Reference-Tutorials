---
title: Konversi SVG ke PDF
linktitle: Konversi SVG ke PDF
second_title: GroupDocs.Konversi .NET API
description: Pelajari cara mengonversi SVG ke PDF menggunakan GroupDocs.Conversion untuk .NET dengan mudah. Sederhanakan proses manajemen dokumen Anda.
weight: 15
url: /id/net/file-format-conversion-convert-svg-to-pdf/
---
## Perkenalan
Dalam dunia pemrograman, mengonversi file dari satu format ke format lainnya adalah tugas yang umum. Baik Anda berurusan dengan gambar, dokumen, atau media lain, kemampuan mengonversi antar format dengan lancar sangatlah penting. Dalam tutorial ini, kita akan mempelajari cara mengonversi file SVG (Scalable Vector Graphics) ke PDF (Portable Document Format) menggunakan GroupDocs.Conversion untuk .NET.
## Prasyarat
Sebelum mendalami proses konversi, pastikan Anda telah menyiapkan prasyarat berikut:
### 1. Instal GroupDocs.Conversion untuk .NET
Pastikan Anda telah menginstal GroupDocs.Conversion for .NET di lingkungan pengembangan Anda. Jika Anda belum melakukannya, Anda dapat mengunduhnya dari[situs web](https://releases.groupdocs.com/conversion/net/).
### 2. Dapatkan Contoh File SVG
Anda memerlukan contoh file SVG untuk dikonversi ke PDF. Jika Anda tidak memilikinya, Anda dapat dengan mudah menemukan file SVG secara online atau membuatnya menggunakan berbagai alat desain grafis.
### 3. Pemahaman Dasar C#
Biasakan diri Anda dengan dasar-dasar bahasa pemrograman C#, karena kita akan menggunakannya untuk menulis kode konversi.

## Impor Namespace
Pertama, mari impor namespace yang diperlukan:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Langkah 1: Tentukan Folder dan File Output
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur ke direktori keluaran yang Anda inginkan.
## Langkah 2: Muat File SVG Sumber
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Kode konversi ada di sini
}
```
 Mengganti`Constants.SAMPLE_SVG` dengan jalur ke file SVG Anda.
## Langkah 3: Tetapkan Opsi Konversi
```csharp
var options = new PdfConvertOptions();
```
Di sini, kami menyiapkan opsi konversi khusus untuk keluaran PDF. Anda dapat menyesuaikan opsi ini berdasarkan kebutuhan Anda.
## Langkah 4: Lakukan Konversi
```csharp
converter.Convert(outputFile, options);
```
Baris ini menjalankan proses konversi, mengambil file sumber SVG dan mengonversinya menjadi PDF dengan opsi yang ditentukan.
## Langkah 5: Periksa Penyelesaian Konversi
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Baris ini menampilkan pesan yang mengonfirmasi keberhasilan penyelesaian proses konversi, bersama dengan direktori tempat file PDF yang dikonversi berada.

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara mengonversi file SVG ke PDF menggunakan GroupDocs.Conversion untuk .NET. Dengan mengikuti panduan langkah demi langkah dan memastikan Anda memiliki prasyarat, Anda dapat dengan lancar menggabungkan kemampuan konversi format file ke dalam aplikasi .NET Anda.
## FAQ
### Apakah GroupDocs.Conversion for .NET kompatibel dengan semua kerangka .NET?
Ya, GroupDocs.Conversion untuk .NET mendukung beberapa kerangka .NET, termasuk .NET Core dan .NET Framework.
### Bisakah saya menyesuaikan opsi konversi untuk format keluaran tertentu?
Sangat! GroupDocs.Conversion for .NET menyediakan opsi penyesuaian yang luas untuk setiap format output yang didukung.
### Apakah GroupDocs.Conversion untuk .NET mendukung konversi batch?
Ya, Anda dapat mengonversi banyak file secara bersamaan menggunakan GroupDocs.Conversion untuk .NET.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
 Ya, Anda dapat mengakses versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Conversion untuk .NET?
Anda dapat menemukan dukungan dan bantuan teknis di forum GroupDocs[Di Sini](https://forum.groupdocs.com/c/conversion/11).