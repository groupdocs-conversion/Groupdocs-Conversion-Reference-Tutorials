---
date: '2026-07-24'
description: 'Konversi gambar Java menjadi mudah: pelajari cara mengonversi file CAD
  ke TIFF dengan dimensi kustom menggunakan GroupDocs Conversion Java. Panduan langkah
  demi langkah untuk pengembang.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Konversi gambar Java menjadi mudah. Konversi file CAD ke gambar TIFF
  berkualitas tinggi dengan lebar dan tinggi kustom menggunakan GroupDocs Conversion
  Java. Ikuti panduan detail kami.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Konversi Gambar Java: CAD ke TIFF dengan Dimensi Kustom'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'Konversi Gambar Java: CAD ke TIFF dengan Dimensi Kustom'
type: docs
url: /id/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Konversi Gambar Java: CAD ke TIFF dengan Dimensi Kustom

Jika Anda perlu mengubah gambar CAD menjadi gambar TIFF resolusi tinggi sambil mengontrol lebar dan tinggi piksel yang tepat, **java image conversion** adalah kuncinya. Dengan menggunakan GroupDocs Conversion Java, Anda dapat merasterisasi format CAD yang didukung (DWG, DGN, DXF, dll.) menjadi file TIFF yang pas sempurna dalam laporan, portal web, atau tata letak cetak. Panduan ini memandu Anda melalui setiap langkah—dari penyiapan proyek hingga konversi akhir—sehingga Anda dapat mengintegrasikan proses ini ke dalam alur kerja berbasis Java apa pun.

## Jawaban Cepat
- **Library apa yang harus saya gunakan untuk Java image conversion?** GroupDocs Conversion Java, sebuah pustaka konversi gambar Java yang kuat.  
- **Bagaimana cara mengatur dimensi kustom untuk file CAD?** Gunakan `CadLoadOptions` dan tentukan `setWidth()` serta `setHeight()`.  
- **Bisakah saya mengonversi DWG ke TIFF dalam satu langkah?** Ya—muat CAD, atur dimensi, lalu konversi dengan `ImageConvertOptions`.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk evaluasi; lisensi penuh membuka semua fitur.  
- **Versi Java apa yang diperlukan?** Setiap runtime Java 8+ didukung.

## Apa itu GroupDocs Conversion Java?
Pustaka `GroupDocs Conversion Java` adalah solusi **java image conversion** yang mendukung lebih dari 110 format input dan output, termasuk semua jenis CAD utama serta tipe gambar raster.  
Kelas `Converter` adalah komponen inti yang memulai operasi konversi file.  
Ia menyediakan rendering sisi server, penskalaan, dan opsi khusus format, memungkinkan pengembang mengonversi file tanpa menginstal penampil pihak ketiga.

## Mengapa Mengonversi CAD ke TIFF dengan Dimensi Kustom?
Menetapkan lebar dan tinggi secara eksplisit menjamin bahwa TIFF yang dihasilkan sesuai dengan batas tata letak yang tepat dari sistem downstream. Dengan mendefinisikan dimensi piksel sebelum rasterisasi, Anda menghindari artefak penskalaan downstream, mempertahankan konsistensi ketebalan garis, dan memastikan gambar terintegrasi mulus ke dalam PDF, halaman web, atau materi cetak tanpa proses tambahan. Pendekatan ini juga menyederhanakan pipeline otomatis di mana setiap gambar harus mematuhi spesifikasi ukuran yang telah ditentukan.  

- **Mempertahankan Kesetiaan Visual:** Merasterisasi pada 1920 × 1080 px (atau ukuran apa pun yang Anda pilih) menjaga garis dan hatching tetap tajam.  
- **Menjamin Tata Letak Konsisten:** Gambar tersemat bersih ke dalam PDF, halaman HTML, atau templat cetak tanpa perlu mengubah ukuran tambahan.  
- **Meningkatkan Kompatibilitas:** TIFF diterima secara universal di Windows, macOS, Linux, dan sebagian besar alat desain, mengurangi masalah konversi format.  

## Prasyarat
1. **GroupDocs Conversion Java** versi 25.2 atau lebih baru (rilis terbaru disarankan).  
2. IDE Java seperti IntelliJ IDEA atau Eclipse.  
3. Maven terpasang untuk manajemen dependensi.  
4. Pengetahuan dasar pemrograman Java dan familiaritas dengan `pom.xml` Maven.  

## Menyiapkan GroupDocs Conversion Java

Tambahkan dependensi Maven GroupDocs ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Perolehan Lisensi:** Anda dapat memperoleh percobaan gratis, meminta lisensi sementara untuk fungsionalitas penuh, atau membeli lisensi permanen untuk membuka semua fitur GroupDocs Conversion.

Setelah proyek Java Anda terhubung dengan dependensi ini dengan benar, Anda siap mulai mengonversi file CAD!

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/conversion/java/</url>
    </repository>
</repositories>
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

## Cara Mengonversi CAD ke TIFF dengan Dimensi Kustom?

Mengonversi file CAD ke TIFF dengan dimensi yang tepat melibatkan memuat gambar sumber, mengonfigurasi opsi rendering, dan memanggil API konversi. Dengan mengikuti urutan linier—menetapkan lebar dan tinggi, memilih TIFF sebagai format output, dan mengeksekusi konversi—Anda memastikan gambar yang dihasilkan sesuai dengan persyaratan ukuran tepat aplikasi downstream Anda, sambil mempertahankan detail dan kualitas gambar asli.  

1. **Impor kelas yang diperlukan** (lihat langkah demi langkah di bawah).  
2. **Buat instance `CadLoadOptions`** dan atur `width` serta `height` ke dimensi target Anda.  
3. **Instansiasi `ImageConvertOptions`**, dengan menentukan `ImageFileType.Tiff`.  
4. **Panggil metode `convert`** pada objek `Converter`, dengan memberikan jalur sumber, opsi muat, dan opsi konversi.

### Memuat Dokumen CAD dengan Dimensi Kustom (Cara Menetapkan Dimensi)

Kelas `CadLoadOptions` memberi tahu GroupDocs cara merasterisasi gambar sebelum konversi.

`CadLoadOptions` adalah objek konfigurasi yang mendefinisikan parameter rendering seperti lebar, tinggi, dan DPI untuk file CAD.

#### Langkah 1: Impor Pustaka yang Diperlukan
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Langkah 2: Siapkan Opsi Muat dengan Dimensi Kustom
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Penjelasan:* Dengan mengkonfigurasi `CadLoadOptions`, Anda memberi tahu **GroupDocs Conversion Java** untuk merasterisasi gambar CAD pada 1920 × 1080 piksel sebelum pemrosesan lebih lanjut.

### Mengonversi Gambar CAD ke TIFF (Convert CAD to TIFF)

`ImageConvertOptions` mengarahkan pustaka untuk menghasilkan file TIFF dengan pengaturan yang Anda tentukan.

`ImageConvertOptions` mengenkapsulasi semua parameter konversi khusus gambar, termasuk format output, resolusi, dan tingkat kompresi.

#### Langkah 3: Konfigurasikan Opsi Konversi
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Langkah 4: Lakukan Konversi
```java
converter.convert(convertedFilePath, options);
```
*Penjelasan:* Menetapkan `ImageFileType.Tiff` mengarahkan **GroupDocs Conversion Java** untuk menghasilkan file TIFF berkualitas tinggi yang menghormati lebar dan tinggi yang Anda definisikan sebelumnya.

## Tips Pemecahan Masalah & Kesalahan Umum
- **Masalah Jalur File:** Verifikasi bahwa jalur sumber dan tujuan keduanya benar serta aplikasi memiliki izin baca/tulis.  
- **Format Tidak Didukung:** Pastikan file CAD merupakan salah satu format yang didukung (DWG, DGN, DXF, dll.).  
- **Keterbatasan Memori:** Gambar besar mungkin memerlukan peningkatan ukuran heap JVM (`-Xmx2g` atau lebih tinggi).  
- **Kekhawatiran Kualitas:** Sesuaikan pengaturan resolusi `ImageConvertOptions` jika DPI default tidak memenuhi standar kualitas Anda.  

## Aplikasi Praktis
1. **Visualisasi Arsitektur:** Ekspor denah sebagai TIFF untuk presentasi resolusi tinggi.  
2. **Dokumentasi Teknik:** Hasilkan gambar standar untuk dimasukkan ke dalam manual teknis.  
3. **Pelaporan Otomatis:** Sematkan TIFF hasil CAD ke dalam laporan PDF atau HTML melalui pipeline CI.  

## Pertimbangan Kinerja
- **Optimalkan Penggunaan Memori:** Lepaskan instance `Converter` setelah konversi (`converter.close()` jika berlaku).  
- **Pemrosesan Batch:** Loop melalui daftar file CAD dan gunakan kembali satu konfigurasi `Converter` untuk mengurangi beban.  
- **Tetap Terbaru:** Secara rutin tingkatkan ke rilis GroupDocs Conversion Java terbaru untuk mendapatkan peningkatan kinerja dan perbaikan bug.  

## Pertanyaan yang Sering Diajukan

**Q:** Format file apa yang didukung oleh GroupDocs Conversion?  
**A:** Mendukung lebih dari 110 format, termasuk file CAD seperti DWG, DGN, DXF, serta tipe gambar, dokumen, dan arsip umum.  

**Q:** Bisakah saya mengonversi beberapa file CAD sekaligus?  
**A:** Ya—implementasikan loop sederhana yang membuat `Converter` baru untuk setiap file atau gunakan kembali instance yang sama dengan jalur sumber yang berbeda.  

**Q:** Bagaimana cara menangani ukuran file besar selama konversi?  
**A:** Tingkatkan ukuran heap JVM, proses file dalam batch lebih kecil, atau gunakan opsi streaming yang disediakan pustaka.  

**Q:** Bagaimana jika kualitas gambar output tidak memuaskan?  
**A:** Sesuaikan DPI atau pengaturan skala di `ImageConvertOptions` untuk meningkatkan resolusi.  

**Q:** Apakah dukungan tersedia jika saya mengalami masalah?  
**A:** GroupDocs menyediakan dokumentasi lengkap, forum komunitas, dan dukungan langsung untuk pelanggan berlisensi.  

## Sumber Daya
- [Dokumentasi GroupDocs](https://docs.groupdocs.com/conversion/java/)
- [Referensi API](https://reference.groupdocs.com/conversion/java/)
- [Unduh Rilis Terbaru](https://releases.groupdocs.com/conversion/java/)
- [Beli Lisensi](https://purchase.groupdocs.com/buy)
- [Akses Percobaan Gratis](https://releases.groupdocs.com/conversion/java/)
- [Permintaan Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)
- [Forum Dukungan](https://forum.groupdocs.com/c/conversion/10)

---

**Terakhir Diperbarui:** 2026-07-24  
**Diuji Dengan:** GroupDocs Conversion Java 25.2  
**Penulis:** GroupDocs  

---

## Tutorial Terkait

- [convert cad pdf java – Tutorial Konversi Format CAD untuk GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java menggunakan GroupDocs.Conversion – Panduan](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Cara Mengatur Lisensi untuk GroupDocs.Conversion Java - Panduan Langkah‑ demi‑Langkah](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)