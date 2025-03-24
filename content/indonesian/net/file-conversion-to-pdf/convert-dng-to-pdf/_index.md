---
title: Konversi Gambar DNG ke PDF
linktitle: Konversi Gambar DNG ke PDF
second_title: GroupDocs.Konversi .NET API
description: Pelajari cara mengonversi gambar DNG ke PDF dengan mudah menggunakan GroupDocs.Conversion untuk .NET. Ikuti panduan langkah demi langkah kami untuk konversi yang lancar.
weight: 21
url: /id/net/file-conversion-to-pdf/convert-dng-to-pdf/
---

# Konversi Gambar DNG ke PDF

## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses mengonversi gambar DNG ke PDF menggunakan GroupDocs.Conversion untuk .NET. DNG (Digital Negative) adalah format file yang digunakan untuk fotografi digital. Dengan mengonversi gambar DNG ke PDF, Anda dapat dengan mudah membagikan atau menyimpannya dalam format yang lebih diterima secara universal.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Conversion untuk .NET: Unduh dan instal pustaka GroupDocs.Conversion untuk .NET dari[Di Sini](https://releases.groupdocs.com/conversion/net/).
2. File DNG Sumber: Anda memerlukan file gambar DNG yang ingin Anda konversi ke PDF.
3. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan pengembangan .NET.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek Anda. Tambahkan arahan penggunaan berikut ke file kode Anda:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Langkah 1: Muat File DNG Sumber
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Muat file DNG sumber
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Lanjutkan dengan proses konversi
}
```
 Pada langkah ini, Anda menentukan folder keluaran tempat file PDF yang dikonversi akan disimpan. Pastikan untuk mengganti`"Your Document Directory"` dengan jalur ke direktori yang Anda inginkan. Kemudian, Anda menentukan nama dan jalur file PDF keluaran.
## Langkah 2: Konversi DNG ke PDF
```csharp
var options = new PdfConvertOptions();
// Simpan file PDF yang dikonversi
converter.Convert(outputFile, options);
```
 Di sini, Anda membuat sebuah instance dari`PdfConvertOptions` untuk mengatur opsi spesifik apa pun untuk konversi PDF, jika diperlukan. Kemudian, Anda menelepon`Convert` metode`converter`objek, meneruskan jalur file keluaran dan opsi konversi.
## Langkah 3: Tangani Penyelesaian Konversi
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Setelah proses konversi selesai, Anda akan melihat pesan sukses beserta direktori tempat file PDF yang dikonversi berada.

## Kesimpulan
Kesimpulannya, mengonversi gambar DNG ke PDF dapat dilakukan dengan mudah menggunakan GroupDocs.Conversion untuk .NET. Dengan mengikuti langkah-langkah sederhana yang diuraikan dalam tutorial ini, Anda dapat mengonversi file DNG ke format PDF secara efisien, menjadikannya lebih mudah diakses dan dibagikan.
## FAQ
### Apakah GroupDocs.Conversion for .NET kompatibel dengan semua versi .NET?
Ya, GroupDocs.Conversion untuk .NET kompatibel dengan .NET Framework 4.6.1 dan yang lebih baru, serta .NET Core 2.0 dan yang lebih baru.
### Bisakah saya mengonversi beberapa file DNG ke PDF secara bersamaan?
Ya, Anda dapat mengonversi beberapa file DNG ke PDF dengan mengulangi setiap file dan melakukan proses konversi untuk masing-masing file.
### Apakah ada batasan ukuran file DNG yang dapat dikonversi?
GroupDocs.Conversion untuk .NET tidak memiliki batasan khusus mengenai ukuran file DNG yang dapat dikonversi. Namun, kinerja dapat bervariasi berdasarkan ukuran dan kompleksitas file masukan.
### Bisakah saya menyesuaikan opsi konversi untuk keluaran PDF?
 Ya, Anda dapat menyesuaikan berbagai opsi seperti ukuran halaman, orientasi, kompresi, dan lainnya menggunakan`PdfConvertOptions`kelas yang disediakan oleh GroupDocs.Conversion untuk .NET.
### Apakah dukungan teknis tersedia untuk GroupDocs.Conversion untuk .NET?
 Ya, dukungan teknis tersedia melalui forum GroupDocs[Di Sini](https://forum.groupdocs.com/c/conversion/11), di mana Anda dapat mengajukan pertanyaan dan mendapatkan bantuan dari para ahli.