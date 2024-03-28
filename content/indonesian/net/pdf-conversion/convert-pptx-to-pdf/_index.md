---
title: Konversi PPTX ke PDF
linktitle: Konversi PPTX ke PDF
second_title: GroupDocs.Konversi .NET API
description: Pelajari cara mengonversi presentasi PowerPoint (PPTX) ke format PDF menggunakan GroupDocs.Conversion untuk .NET. Proses konversi yang mudah dan efisien.
type: docs
weight: 29
url: /id/net/pdf-conversion/convert-pptx-to-pdf/
---
## Perkenalan
Dalam tutorial ini, kita akan memandu proses mengonversi file presentasi PowerPoint (PPTX) ke Portable Document Format (PDF) menggunakan pustaka GroupDocs.Conversion untuk .NET. Ikuti langkah-langkah di bawah ini untuk mencapai konversi ini.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Conversion untuk .NET Library: Pastikan Anda telah menginstal GroupDocs.Conversion untuk perpustakaan .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/conversion/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan dengan alat yang diperlukan seperti Visual Studio atau .NET IDE lainnya.

## Impor Namespace
Sertakan namespace yang diperlukan dalam proyek Anda untuk mengakses fungsi GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Langkah 1: Tetapkan Folder Output dan Nama File
Pertama, tentukan folder keluaran tempat file PDF yang dikonversi akan disimpan, dan tentukan nama file PDF keluaran.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Langkah 2: Muat File PPTX Sumber
Muat file sumber presentasi PowerPoint (PPTX) menggunakan pustaka GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Logika konversi akan ditempatkan di sini
}
```
## Langkah 3: Tentukan Opsi Konversi
Tentukan opsi konversi. Dalam hal ini, kami mengonversi ke format PDF, jadi buatlah sebuah instance`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Langkah 4: Lakukan Konversi
 Jalankan proses konversi menggunakan`Convert` metode dan meneruskan jalur file keluaran bersama dengan opsi konversi.
```csharp
converter.Convert(outputFile, options);
```
## Langkah 5: Periksa Keluaran
Setelah konversi berhasil diselesaikan, tampilkan pesan yang menunjukkan penyelesaian dan lokasi file keluaran.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara mengonversi file presentasi PowerPoint (PPTX) ke Portable Document Format (PDF) menggunakan pustaka GroupDocs.Conversion untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat dengan mudah melakukan konversi ini di aplikasi .NET Anda.
## FAQ
### T: Apakah GroupDocs.Conversion kompatibel dengan semua versi .NET?
J: Ya, GroupDocs.Conversion mendukung .NET Framework 2.0 dan lebih tinggi, termasuk .NET Core dan .NET Standard.
### T: Dapatkah saya mengonversi file ke format selain PDF?
J: Ya, GroupDocs.Conversion mendukung berbagai format dokumen untuk konversi, termasuk Word, Excel, HTML, dan banyak lagi.
### T: Apakah GroupDocs.Conversion menawarkan uji coba gratis?
 J: Ya, Anda dapat mengakses uji coba gratis GroupDocs.Conversion dari[Di Sini](https://releases.groupdocs.com/).
### T: Bagaimana cara mendapatkan dukungan untuk GroupDocs.Conversion?
 J: Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs[Di Sini](https://forum.groupdocs.com/c/conversion/11).
### T: Apakah ada lisensi sementara yang tersedia untuk GroupDocs.Conversion?
 J: Ya, Anda bisa mendapatkan lisensi sementara untuk GroupDocs.Conversion dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).