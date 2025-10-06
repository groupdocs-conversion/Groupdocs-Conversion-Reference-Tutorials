---
"description": "Ubah JPG ke PDF dengan mudah menggunakan GroupDocs.Conversion for .NET. Ikuti tutorial langkah demi langkah ini untuk konversi dokumen yang lancar."
"linktitle": "Konversi JPG ke PDF"
"second_title": "API GroupDocs.Conversion .NET"
"title": "Konversi JPG ke PDF"
"url": "/id/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
type: docs
---
# Konversi JPG ke PDF

## Perkenalan

Apakah Anda ingin mengonversi file JPG ke PDF dengan mudah menggunakan GroupDocs.Conversion for .NET? Tutorial ini akan memandu Anda melalui proses ini langkah demi langkah. GroupDocs.Conversion for .NET adalah API canggih yang memungkinkan Anda mengonversi berbagai format dokumen, termasuk gambar, ke PDF dengan mudah. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

1. GroupDocs.Conversion untuk .NET: Pastikan Anda telah menginstal GroupDocs.Conversion untuk .NET. Anda dapat mengunduhnya dari [Di Sini](https://releases.groupdocs.com/conversion/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan, seperti Visual Studio, bersama dengan .NET Framework atau .NET Core.
3. Contoh Berkas JPG: Siapkan contoh berkas JPG yang ingin diubah ke PDF.

## Mengimpor Ruang Nama

Pertama, mari impor namespace yang diperlukan:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Sekarang, mari kita uraikan proses konversi menjadi beberapa langkah sederhana:

## Langkah 1: Tentukan Direktori Output dan Nama File

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Pastikan untuk menentukan direktori tempat Anda ingin menyimpan berkas PDF yang dikonversi dan nama berkas keluaran yang diinginkan.

## Langkah 2: Muat File JPG Sumber dan Konversi ke PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Inisialisasi `Converter` objek dengan jalur ke file JPG contoh Anda. Kemudian, konfigurasikan opsi konversi, seperti menentukan opsi konversi PDF. Terakhir, panggil `Convert` metode, meneruskan jalur file keluaran dan opsi konversi.

## Langkah 3: Menampilkan Pesan Penyelesaian Konversi

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Setelah konversi selesai, tampilkan pesan yang menunjukkan konversi berhasil dan lokasi berkas PDF yang dikonversi.

## Kesimpulan

Mengonversi file JPG ke PDF menggunakan GroupDocs.Conversion for .NET mudah dilakukan hanya dengan beberapa baris kode. Dengan mengikuti tutorial ini, Anda dapat mengintegrasikan kemampuan konversi dokumen ke aplikasi .NET Anda dengan mudah.

## Pertanyaan yang Sering Diajukan

### T: Dapatkah saya mengonversi beberapa berkas JPG ke PDF secara bersamaan?

A: Ya, Anda dapat mengonversi beberapa file JPG ke PDF dengan mengulangi setiap file dan melakukan proses konversi yang dijelaskan dalam tutorial.

### T: Apakah GroupDocs.Conversion mendukung format gambar lain selain JPG?

A: Ya, GroupDocs.Conversion mendukung berbagai format gambar seperti PNG, TIFF, BMP, dan GIF, antara lain.

### T: Dapatkah saya menyesuaikan keluaran berkas PDF menggunakan opsi konversi?

A: Tentu saja! GroupDocs.Conversion menyediakan berbagai pilihan konversi yang memungkinkan Anda menyesuaikan hasil PDF sesuai dengan kebutuhan Anda.

### T: Apakah ada versi uji coba yang tersedia untuk GroupDocs.Conversion untuk .NET?

A: Ya, Anda dapat mengakses versi uji coba gratis GroupDocs.Conversion untuk .NET dari [Di Sini](https://releases.groupdocs.com/).

### T: Di mana saya dapat mencari bantuan jika saya menemui masalah selama proses konversi?

A: Jika Anda mengalami masalah atau memiliki pertanyaan mengenai GroupDocs.Conversion untuk .NET, jangan ragu untuk mengunjungi [Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) untuk bantuan.