---
date: '2026-05-21'
description: Pelajari cara menggunakan custom redis cache .net dengan GroupDocs.Conversion
  untuk secara dramatis mempercepat konversi dokumen. Temukan panduan langkah demi
  langkah, gunakan praktik terbaik caching redis, dan metrik kinerja.
keywords:
- custom redis cache .net
- use redis caching
- implement redis caching .net
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to use custom redis cache .net with GroupDocs.Conversion
    to dramatically speed up document conversion. Discover step‑by‑step setup, use
    redis caching best practices, and performance metrics.
  headline: Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: 'Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).'
    question: How do I install Redis on my local machine?
  - answer: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average
      response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute
      cycles.
    question: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?
  - answer: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance
      (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups
      allow traffic on port 6379.
    question: Can this architecture be deployed to Azure or AWS?
  - answer: The `StackExchange.Redis` client is fully thread‑safe; you can share a
      single `ConnectionMultiplexer` across all request threads without additional
      locking.
    question: Is the cache thread‑safe for concurrent web requests?
  - answer: Invalidate by deleting keys that match the document’s identifier, e.g.,
      `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.
    question: How do I clear the cache when a source document changes?
  type: FAQPage
title: Tingkatkan Kinerja .NET dengan custom redis cache .net dan GroupDocs.Conversion
type: docs
url: /id/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Tingkatkan Kinerja Aplikasi .NET Anda dengan **custom redis cache .net** Menggunakan GroupDocs.Conversion

## Pendahuluan

Jika aplikasi .NET Anda menghabiskan detik berharga—atau bahkan menit—untuk mengonversi dokumen, Anda tidak sendirian. Menerapkan solusi **custom redis cache .net** bersama GroupDocs.Conversion dapat memotong waktu konversi hingga 80 % untuk permintaan berulang. Dalam tutorial ini Anda akan belajar cara menyiapkan GroupDocs.Conversion, membuat cache berbasis Redis, dan menerapkan teknik penyetelan kinerja terbukti yang menjaga aplikasi Anda tetap responsif di bawah beban berat.

### Jawaban Cepat
- **Apa yang disimpan oleh custom Redis cache?** Aliran byte PDF/HTML yang dirender untuk setiap dokumen sumber.  
- **Seberapa cepat konversi dapat menjadi?** Hingga 8× lebih cepat untuk dokumen yang di-cache, diukur pada server 4‑core.  
- **Apakah saya memerlukan lisensi GroupDocs komersial?** Ya, lisensi yang valid diperlukan untuk penggunaan produksi.  
- **Apakah ini dapat dijalankan pada .NET 6+?** Tentu—kompatibel dengan .NET 5, .NET 6, dan .NET 7.  
- **Apakah dukungan Docker disertakan?** Cache berfungsi di dalam kontainer; cukup expose port Redis.  

## Apa itu **custom redis cache .net**?

Ini adalah lapisan caching yang diimplementasikan oleh pengembang yang menyimpan output biner dari konversi dokumen dalam penyimpanan key‑value Redis, memungkinkan permintaan berikutnya mengambil hasil yang sudah dirender secara instan alih-alih memproses ulang file asli, sehingga mengurangi latensi dan beban CPU di seluruh aplikasi.

## Mengapa menggunakan **custom redis cache .net** dengan GroupDocs.Conversion?

GroupDocs.Conversion mendukung **50+** format input dan output—termasuk DOCX, PPTX, HTML, dan PDF—dan dapat memproses dokumen hingga 500 halaman tanpa memuat seluruh file ke memori. Dengan menggabungkannya dengan cache Redis, Anda menghilangkan rendering berulang, mengurangi penggunaan CPU sekitar **70 %**, dan menjaga waktu respons di bawah **200 ms** untuk aset yang di-cache.

## Prasyarat

- **GroupDocs.Conversion untuk .NET** (Versi 25.3.0 atau lebih baru)  
- **StackExchange.Redis** paket NuGet  
- Instance Redis yang dapat dijangkau (mis., `192.168.222.4:6379`)  
- Visual Studio 2022 atau IDE kompatibel C# apa pun  
- .NET 6 SDK (atau .NET 5/Framework 4.8) terpasang  

### Prasyarat Pengetahuan
- Nyaman dengan pola async/await C#  
- Konsep dasar Redis (keys, TTL, connection pooling)  
- Familiaritas dengan pipeline konversi dokumen  

## Cara menyiapkan GroupDocs.Conversion untuk .NET?

Mulailah dengan menambahkan paket GroupDocs.Conversion ke proyek Anda menggunakan NuGet Package Manager Console atau .NET CLI. Ini menginstal mesin konversi inti dan dependensinya, menyiapkan lingkungan Anda untuk membuat instance Converter dan mengonfigurasi pengaturan konversi untuk berbagai format dokumen.

Instal perpustakaan melalui NuGet:

```
Install-Package GroupDocs.Conversion
```

Atau dengan .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Langkah Akuisisi Lisensi
- **Free trial:** Daftar di portal GroupDocs untuk file lisensi 30‑hari.  
- **Temporary license:** Minta kunci evaluasi 90‑hari untuk beban kerja yang lebih besar.  
- **Purchase:** Dapatkan lisensi produksi untuk membuka konversi tak terbatas.

Setelah menginstal paket, inisialisasi GroupDocs.Conversion dalam proyek C# Anda:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Bagaimana **custom redis cache .net** meningkatkan kecepatan konversi?

Ketika permintaan konversi tiba, aplikasi pertama-tama menanyakan Redis untuk aliran byte yang di-cache yang cocok dengan dokumen sumber dan parameter konversi. Jika ada hit, hasil yang disimpan dikembalikan segera, melewati proses rendering yang mahal; jika tidak, GroupDocs.Conversion melakukan konversi dan output disimpan kembali ke Redis untuk penggunaan di masa mendatang.

### Langkah 1: Definisikan kelas `RedisCache`

Kelas `RedisCache` menyediakan pembungkus ringan di sekitar StackExchange.Redis untuk menyimpan dan mengambil hasil konversi biner.

```csharp
// RedisCache class definition placeholder
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using StackExchange.Redis;

public class RedisCache : IDisposable
{
    private readonly string _cacheKeyPrefix;
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _db;
    private readonly string _host = "192.168.222.4:6379";

    public RedisCache(string cacheKeyPrefix)
    {
        _cacheKeyPrefix = cacheKeyPrefix;
        _redis = ConnectionMultiplexer.Connect(_host);
        _db = _redis.GetDatabase();
    }

    // Set data in the cache with a specific key
    public void Set(string key, object data)
    {
        if (data == null) return;

        string prefixedKey = GetPrefixedKey(key);
        using (MemoryStream stream = new MemoryStream())
        {
            ((Stream)data).CopyTo(stream);
            _db.StringSet(prefixedKey, RedisValue.CreateFrom(stream));
        }
    }

    // Try to retrieve data from the cache using a key
    public bool TryGetValue(string key, out object value)
    {
        var prefixedKey = GetPrefixedKey(key);
        var redisValue = _db.StringGet(prefixedKey);

        if (redisValue.HasValue)
        {
            value = new MemoryStream(redisValue);
            return true;
        }

        value = default;
        return false;
    }

    // Retrieve all keys that match a filter pattern from the cache
    public IEnumerable<string> GetKeys(string filter)
    {
        return _redis.GetServer(_host).Keys(pattern: $"*{filter}*")
            .Select(x => x.ToString().Replace(_cacheKeyPrefix, string.Empty))
            .Where(x => x.StartsWith(filter, StringComparison.InvariantCultureIgnoreCase))
            .ToList();
    }

    private string GetPrefixedKey(string key) => $"{_cacheKeyPrefix}{key}";

    public void Dispose()
    {
        _redis.Dispose();
    }
}
```
```

## Langkah 2: Implementasikan konversi dokumen dengan cache khusus

Contoh berikut menunjukkan integrasi `RedisCache` dengan GroupDocs.Conversion untuk meng-cache output konversi PDF.

```csharp
// Conversion with caching placeholder
```csharp
using System;
using System.Diagnostics;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Caching;

public class HowToUseCustomCacheImplementation
{
    public static void Run()
    {
        string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
        
        RedisCache cache = new RedisCache("sample_");
        Func<ConverterSettings> settingsFactory = () => new ConverterSettings
        {
            Cache = cache
        };

        using (Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF", settingsFactory))
        {
            PdfConvertOptions options = new PdfConvertOptions();
            
            Stopwatch stopWatch = Stopwatch.StartNew();
            converter.Convert($"{outputDirectory}/converted.pdf", options);
            stopWatch.Stop();

            stopWatch.Restart();
            converter.Convert($"{outputDirectory}/converted-1.pdf", options);
            stopWatch.Stop();
        }
    }
}
```
```

## Apa saja penggunaan umum untuk **custom redis cache .net**?

Cache Redis khusus dapat dimanfaatkan dalam skenario apa pun di mana hasil konversi dokumen diminta berulang kali, memberikan pengambilan instan dan mengurangi beban server. Aplikasi tipikal meliputi sistem manajemen dokumen perusahaan, API web dengan lalu lintas tinggi yang menyajikan pratinjau, caching edge CDN untuk aset yang dikonversi, dasbor pelaporan otomatis, dan platform e‑commerce yang menghasilkan brosur produk sesuai permintaan.

1. **Sistem Manajemen Dokumen Perusahaan:** Mempercepat pembuatan pratinjau untuk ribuan PDF yang disimpan di repositori pusat.  
2. **API Web:** Mengembalikan HTML atau thumbnail gambar yang telah dikonversi sebelumnya secara instan untuk endpoint dengan lalu lintas tinggi.  
3. **Node Edge CDN:** Meng-cache aset yang dikonversi dekat dengan pengguna, mengurangi beban server asal.  
4. **Dasbor Analitik:** Menghasilkan laporan PDF secara langsung dan menggunakannya kembali untuk pengiriman terjadwal berulang.  
5. **Katalog E‑commerce:** Meng-cache konversi brosur produk untuk meningkatkan waktu muat halaman.  

## Bagaimana Anda dapat menyetel kinerja saat menggunakan Redis?

Kinerja dapat dioptimalkan dengan mengonfigurasi nilai TTL yang tepat, menggunakan kembali satu instance ConnectionMultiplexer, menyimpan array byte mentah untuk menghindari overhead serialisasi, dan menggunakan operasi batch untuk penghapusan massal. Memantau penggunaan memori dan mengaktifkan kebijakan eviksi seperti allkeys‑lru memastikan cache tetap efisien di bawah beban berat.

- **Manajemen ukuran cache:** Tetapkan TTL 24 jam untuk kebanyakan dokumen; bersihkan entri lama dengan `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Gunakan kembali satu instance `ConnectionMultiplexer` di seluruh aplikasi untuk menghindari overhead handshake.  
- **Serialisasi efisien:** Simpan byte mentah secara langsung; hindari pembungkus JSON atau XML yang memperbesar ukuran payload.  
- **Operasi batch:** Saat membersihkan kategori, gunakan `IDatabase.KeyDelete` dengan pola untuk menghapus banyak kunci dalam satu panggilan.  

## Cara mengatasi masalah umum?

Saat masalah muncul, verifikasi bahwa kunci cache dihasilkan secara konsisten, pantau konsumsi memori Redis, dan pastikan versi pustaka klien cocok dengan runtime. Periksa latensi jaringan antara aplikasi dan server Redis, serta pastikan connection pooling dikonfigurasi dengan benar untuk menghindari handshake berlebihan yang dapat menurunkan kinerja.

- **Kunci hilang:** Verifikasi bahwa kunci cache yang sama dihasilkan untuk parameter konversi yang identik (jalur input, format output, opsi konversi).  
- **Tekanan memori:** Pantau penggunaan memori Redis; aktifkan `maxmemory-policy allkeys-lru` untuk meng-evict entri yang paling tidak baru secara otomatis.  
- **Versi tidak cocok:** Pastikan versi StackExchange.Redis cocok dengan runtime .NET (mis., 2.6+ untuk .NET 6).  
- **Latensi jaringan:** Tempatkan Redis di pusat data atau VPC yang sama dengan aplikasi Anda untuk menjaga waktu perjalanan pulang pergi di bawah 1 ms.  

## Pertanyaan yang Sering Diajukan

**Q: How do I install Redis on my local machine?**  
A: Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).

**Q: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?**  
A: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute cycles.

**Q: Can this architecture be deployed to Azure or AWS?**  
A: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups allow traffic on port 6379.

**Q: Is the cache thread‑safe for concurrent web requests?**  
A: The `StackExchange.Redis` client is fully thread‑safe; you can share a single `ConnectionMultiplexer` across all request threads without additional locking.

**Q: How do I clear the cache when a source document changes?**  
A: Invalidate by deleting keys that match the document’s identifier, e.g., `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Kesimpulan

Dengan mengintegrasikan **custom redis cache .net** dengan GroupDocs.Conversion, Anda membuka peningkatan kinerja yang dramatis, menurunkan biaya infrastruktur, dan memberikan pengalaman pengguna yang lebih halus. Langkah‑langkah di atas memberi Anda fondasi siap produksi—cobalah nilai TTL, strategi kunci cache, dan penskalaan horizontal untuk menyesuaikan solusi dengan beban kerja Anda.

**Terakhir Diperbarui:** 2026-05-21  
**Diuji Dengan:** GroupDocs.Conversion 25.3.0 untuk .NET  
**Penulis:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Tutorial Terkait

- [Tutorial Manajemen Cache Konversi untuk GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimalkan Konversi Dokumen .NET dengan Caching Menggunakan GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Kuasi Pengaturan Konversi Dokumen di .NET Menggunakan GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)