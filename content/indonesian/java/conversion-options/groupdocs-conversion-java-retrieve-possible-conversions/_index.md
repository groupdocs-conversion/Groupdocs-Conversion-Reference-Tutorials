---
date: '2026-07-29'
description: Temukan cara menampilkan daftar format dan mengambil semua konversi yang
  memungkinkan menggunakan GroupDocs.Conversion for Java, ideal untuk alur kerja konversi
  file penyimpanan awan.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Pelajari cara menampilkan daftar format dan mengambil semua konversi
  yang memungkinkan menggunakan GroupDocs.Conversion for Java. Ideal untuk pipeline
  konversi file penyimpanan awan.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Cara Menampilkan Daftar Format dengan GroupDocs.Conversion for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: Cara Menampilkan Daftar Format dengan GroupDocs.Conversion for Java
type: docs
url: /id/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Cara Menampilkan Format dan Mengambil Semua Konversi yang Mungkin dengan GroupDocs.Conversion untuk Java

Dalam banyak proyek pemrosesan dokumen, langkah pertama adalah mengetahui **how to list formats** yang didukung oleh mesin konversi. Tutorial ini menunjukkan, langkah demi langkah, cara menanyakan GroupDocs.Conversion untuk Java, mengambil setiap pasangan sumber‑ke‑target, dan menerapkan pengetahuan tersebut dalam pipeline konversi file penyimpanan cloud. Pada akhir tutorial, Anda akan memiliki metode yang dapat digunakan kembali yang mengembalikan matriks konversi lengkap, serta tips praktis untuk kinerja dan penanganan kesalahan.

## Jawaban Cepat
- **What does “list formats” mean?** Ini mengembalikan setiap pasangan konversi sumber‑ke‑target yang dapat ditangani oleh pustaka.  
- **Do I need a license?** Uji coba gratis dapat digunakan untuk pengujian; lisensi berbayar diperlukan untuk produksi.  
- **Can this help cloud storage file conversion?** Ya—mengetahui format yang didukung memungkinkan Anda mengotomatisasi konversi dalam pipeline penyimpanan cloud.  
- **Which Java version is required?** JDK 8 atau lebih baru.  
- **Is the feature thread‑safe?** Instance `Converter` dapat digunakan kembali di seluruh thread, tetapi harus membuang sumber daya setelah penggunaan.

## Apa itu “how to list formats” dalam GroupDocs.Conversion?
Operasi **list formats** mengembalikan koleksi yang menjelaskan setiap format sumber bersama dengan format target yang dapat diubah menjadi. Matriks ini dihasilkan dari aturan konversi internal pustaka dan penting untuk membangun alur kerja dinamis yang menyesuaikan dengan kemampuan sebenarnya dari GroupDocs.Conversion pada waktu berjalan.

## Mengapa Menggunakan GroupDocs.Conversion untuk Java?
GroupDocs.Conversion untuk Java mendukung **200+ format input** dan **200+ format output**, mencakup semua mulai dari DOCX dan PPTX hingga PDF/A dan tipe gambar. Ia berjalan sepenuhnya di server, sehingga tidak memerlukan Microsoft Office atau produk Adobe. API bersifat thread‑safe, dapat memproses dokumen ratusan halaman tanpa memuat seluruh file ke dalam memori, dan terintegrasi mulus dengan layanan penyimpanan cloud seperti AWS S3, Azure Blob, dan Google Cloud Storage.

## Prasyarat
- **Java Development Kit (JDK):** Versi 8 atau lebih baru.  
- **Maven:** Dikonfigurasi dengan benar di IDE Anda (IntelliJ IDEA, Eclipse, NetBeans, dll.).  
- **GroupDocs.Conversion for Java:** Ditambahkan sebagai dependensi Maven (lihat di bawah).  

## Menyiapkan GroupDocs.Conversion untuk Java

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Pengadaan Lisensi
Mulailah dengan uji coba gratis untuk menjelajahi API. Untuk beban kerja produksi, beli lisensi atau minta lisensi evaluasi sementara.

### Inisialisasi Dasar dan Penyiapan

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## Cara Menampilkan Format Menggunakan GroupDocs.Conversion untuk Java
`Converter` adalah kelas inti yang melakukan konversi dan menyediakan informasi format. `getAllPossibleConversions()` mengembalikan daftar semua pasangan konversi sumber‑ke‑target yang didukung. `ConversionInfo` mewakili satu pemetaan konversi antara format sumber dan target.

Muat mesin `Converter`, panggil `getAllPossibleConversions()`, dan Anda akan menerima daftar objek `ConversionInfo` yang menggambarkan setiap pasangan sumber‑ke‑target yang diizinkan. Panggilan tunggal ini sudah cukup untuk membuat dropdown opsi ekspor, memvalidasi file masuk, atau merancang skrip migrasi batch.

### Inisialisasi dan Mengambil Konversi
Kelas `Converter` adalah mesin inti yang menyediakan kemampuan konversi dan mengekspos metode `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterasi atas Konversi yang Mungkin

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Menentukan Jenis Konversi

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Fungsi Lengkap

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## Kasus Penggunaan Konversi File Penyimpanan Cloud
Mengetahui matriks konversi lengkap sangat berharga saat membangun layanan **cloud storage file conversion**:

1. **Dynamic Format Detection:** Saat file masuk ke penyimpanan cloud, Anda dapat langsung menanyakan apakah format target yang diinginkan didukung.  
2. **Batch Migration:** Pindahkan perpustakaan dokumen besar ke format terpadu (mis., PDF/A) dengan mengiterasi tipe sumber yang didukung.  
3. **User‑Driven Export:** Tawarkan kepada pengguna akhir dropdown hanya format yang dapat diekspor dari dokumen mereka saat ini, mengurangi kesalahan dan meningkatkan UX.

## Pertimbangan Kinerja
- **Resource Management:** Buang instance `Converter` atau gunakan try‑with‑resources jika Anda membuat banyak konverter berumur pendek.  
- **Batch Processing:** Kelompokkan beberapa file menjadi satu pekerjaan untuk mengurangi beban.  
- **Caching:** Cache hasil `getAllPossibleConversions()` jika Anda sering menanyakannya; matriks konversi jarang berubah pada waktu berjalan.  

## Masalah Umum dan Solusinya
| Gejala | Penyebab Kemungkinan | Solusi |
|---------|--------------|-----|
| Tidak ada output yang muncul | `Converter` tidak diinisialisasi dengan benar | Pastikan JAR pustaka berada di classpath dan lisensi dimuat. |
| Daftar `TargetConversion` kosong | Menggunakan versi pustaka yang usang | Upgrade ke rilis GroupDocs.Conversion terbaru. |
| Lonjakan memori pada dokumen besar | Tidak membuang sumber daya konverter | Panggil `converter.close()` atau gunakan try‑with‑resources. |

## Pertanyaan yang Sering Diajukan

**Q: Apa itu GroupDocs.Conversion untuk Java?**  
A: Ini adalah pustaka sisi server yang mendukung 200+ format input dan 200+ format output, memungkinkan konversi dokumen cepat tanpa lisensi tanpa perangkat lunak eksternal.

**Q: Bagaimana cara memulai dengan GroupDocs.Conversion?**  
A: Siapkan proyek Maven Anda, tambahkan dependensi yang ditunjukkan sebelumnya, muat file lisensi, dan buat instance kelas `Converter` seperti yang ditunjukkan pada bagian inisialisasi.

**Q: Apakah saya dapat mengonversi tipe file khusus menggunakan GroupDocs.Conversion?**  
A: Ya—melalui titik ekstensi API Anda dapat mendaftarkan konverter khusus atau plug‑in penangan pihak ketiga untuk format proprietari.

**Q: Apa jebakan umum saat mengimplementasikan konversi?**  
A: Lupa menutup `Converter`, menggunakan versi JAR lama, atau mengabaikan penggunaan memori untuk PDF yang sangat besar. Ikuti tips manajemen sumber daya di atas.

**Q: Di mana saya dapat mendapatkan bantuan lebih lanjut?**  
A: Kunjungi [dokumentasi](https://docs.groupdocs.com/conversion/java/) resmi atau ajukan pertanyaan di forum komunitas GroupDocs.

---

**Terakhir Diperbarui:** 2026-07-29  
**Diuji Dengan:** GroupDocs.Conversion 25.2 for Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Konversi Word ke PDF dan Format File Lain dengan GroupDocs.Conversion untuk Java](/conversion/java/)
- [Word ke PDF Java – Sembunyikan Perubahan yang Dilacak & Opsi Konversi](/conversion/java/conversion-options/)
- [Cara Melacak Progres Konversi di Java dengan GroupDocs - Panduan Lengkap](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)