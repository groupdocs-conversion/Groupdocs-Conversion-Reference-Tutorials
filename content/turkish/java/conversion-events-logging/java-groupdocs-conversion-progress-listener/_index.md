---
date: '2025-12-19'
description: Java'da dönüşümü nasıl izleyebileceğinizi öğrenin, GroupDocs.Conversion
  kullanarak docx ve pdf'yi Java'da nasıl dönüştüreceğinizi dahil edin. Sorunsuz izleme
  için sağlam dinleyiciler uygulayın.
keywords:
- track document conversion progress Java
- GroupDocs.Conversion for Java
- conversion state and progress listener
title: 'Java''da GroupDocs ile Dönüşüm İlerlemesini Nasıl İzlersiniz: Tam Bir Rehber'
type: docs
url: /tr/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/
weight: 1
---

# Java ile GroupDocs'ta Dönüşüm İlerlemesini Nasıl İzlersiniz

Uygulamalarınızda **dönüşümün nasıl izleneceğini** bilmeniz gerekiyorsa—özellikle **docx pdf java** dönüştürmek istediğinizde—GroupDocs.Conversion temiz, olay‑tabanlı bir yaklaşım sunar. Dinleyicileri ekleyerek dönüşüm hattının her aşamasında gerçek‑zamanlı geri bildirim alabilir, toplu işler, UI ilerleme çubukları ve günlük kaydı (logging) çok daha şeffaf hale gelir.

## Hızlı Yanıtlar
- **Dinleyici ne işe yarar?** Başlangıç, ilerleme (yüzde) ve tamamlanma olaylarını raporlar.  
- **Hangi formatları izleyebilirim?** GroupDocs.Conversion tarafından desteklenen herhangi bir format, ör. DOCX → PDF.  
- **Lisans gerekli mi?** Geliştirme için ücretsiz deneme çalışır; üretim için ücretli lisans gerekir.  
- **Maven gerekli mi?** Maven bağımlılık yönetimini kolaylaştırır, ancak Gradle ya da manuel JAR'lar da kullanılabilir.  
- **Bunu bir web servisinde kullanabilir miyim?** Evet—dönüşüm çağrısını bir REST uç noktasına sarın ve ilerlemeyi istemciye geri akıtın.

## GroupDocs'ta “dönüşümün nasıl izleneceği” nedir?
GroupDocs.Conversion `IConverterListener` arayüzünü sağlar. Bu arayüzü uygulayarak dönüşüm motoru durum değiştiğinde kodunuzun tepki vermesini sağlayabilir, günlük kaydı yapabilir, UI bileşenlerini güncelleyebilir ya da sonraki süreçleri tetikleyebilirsiniz.

## Dönüşüm ilerlemesi neden izlenir?
- **Kullanıcı Deneyimi:** UI panolarında ya da CLI araçlarında canlı yüzde göstergeleri sunun.  
- **Hata Yönetimi:** Duraklamaları erken tespit edin ve nazikçe yeniden deneyin ya da iptal edin.  
- **Kaynak Planlaması:** Büyük toplular için işleme süresini tahmin edin ve kaynakları buna göre tahsis edin.  

## Önkoşullar
- **Java Development Kit (JDK 8+).**  
- **Maven** (veya Maven depolarını çözebilen herhangi bir yapı aracı).  
- **GroupDocs.Conversion for Java** kütüphanesi.  
- **Geçerli bir GroupDocs lisansı** (test için ücretsiz deneme yeterli).

## GroupDocs.Conversion for Java Kurulumu
### Maven ile GroupDocs.Conversion Yükleme
`pom.xml` dosyanıza depo ve bağımlılığı ekleyin:

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
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

### Lisans Edinme
GroupDocs ücretsiz deneme, değerlendirme için geçici lisanslar ve ticari kullanım için satın alma seçenekleri sunar. Lisansınızı edinmek için [satın alma sayfasını](https://purchase.groupdocs.com/buy) ziyaret edin.

### Temel Başlatma
Kütüphane sınıf yolunuza (classpath) eklendikten sonra bir `ConverterSettings` örneği oluşturabilirsiniz:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.ConverterSettings;

public class InitializeGroupDocs {
    public static void main(String[] args) {
        ConverterSettings settings = new ConverterSettings();
        // Additional configurations can be set here.
    }
}
```

## Uygulama Kılavuzu
Her özelliği adım adım inceleyecek, kod parçacıklarından önce bağlam ekleyeceğiz.

### Özellik 1: Dönüşüm Durumu ve İlerleme Dinleyicisi
#### Genel Bakış
Bu dinleyici bir dönüşümün ne zaman başladığını, ne kadar ilerlediğini ve ne zaman bittiğini size bildirir.

#### Dinleyiciyi Uygulama
`IConverterListener` arayüzünü uygulayan bir sınıf oluşturun:

```java
import com.groupdocs.conversion.IConverterListener;

class ListenConversionStateAndProgress implements IConverterListener {
    public void started() {
        System.out.println("Conversion has begun.");
    }

    public void progress(byte current) {
        System.out.printf("Conversion Progress: %d%%\n", current);
    }

    public void completed() {
        System.out.println("Conversion has finished.");
    }
}
```

**Açıklama**  
- **started()** – motor işlemeye başlamadan hemen önce çağrılır. Zamanlayıcıları ya da UI öğelerini sıfırlamak için kullanın.  
- **progress(byte current)** – tamamlanma yüzdesini 0‑100 arasında bir değer olarak alır. İlerleme çubukları için idealdir.  
- **completed()** – çıktı dosyası tamamen yazıldıktan sonra tetiklenir. Kaynakları burada temizleyin.

### Özellik 2: Dinleyicili Dönüştürücü Ayarları
#### Genel Bakış
Dinleyicinizi `ConverterSettings`e ekleyerek motorun olayları nereye göndereceğini belirtirsiniz.

#### Yapılandırma Adımları
1. **Dinleyicinizin bir örneğini oluşturun**:

   ```java
   IConverterListener listener = new ListenConversionStateAndProgress();
   ```

2. **`ConverterSettings` nesnesini yapılandırın**:

   ```java
   ConverterSettings settingsFactory = new ConverterSettings();
   settingsFactory.setListener(listener);
   ```

### Özellik 3: Belge Dönüştürme İşlemi
#### Genel Bakış
Şimdi DOCX dosyasını PDF’ye dönüştürürken dinleyicinin nasıl çalıştığını göreceksiniz.

#### Uygulama Adımları
1. **Girdi ve çıktı yollarını tanımlayın** (kendi dizinlerinizi buraya koyun):

   ```java
   String inputDocPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
   String outputPath = "YOUR_OUTPUT_DIRECTORY/converted.pdf";
   ```

2. **Dinleyicili ayarlarla dönüştürücüyü başlatın** ve dönüşümü çalıştırın:

   ```java
   try (Converter converter = new Converter(inputDocPath, settingsFactory)) {
       PdfConvertOptions options = new PdfConvertOptions();
       converter.convert(outputPath, options);
   }
   ```

**Açıklama**  
- **Converter** – dönüşümü yöneten çekirdek sınıf.  
- **PdfConvertOptions** – GroupDocs’a PDF çıktısı istediğinizi söyler. Bunu `PptxConvertOptions`, `HtmlConvertOptions` vb. ile değiştirebilir ve aynı dinleyici hâlâ ilerlemeyi rapor eder.  

## GroupDocs ile docx pdf java Nasıl Dönüştürülür
Yukarıdaki kod zaten **docx → pdf** akışını gösteriyor. Başka hedef formatlara ihtiyacınız varsa sadece `PdfConvertOptions` yerine ilgili seçenek sınıfını (ör. HTML için `HtmlConvertOptions`) değiştirin. Dinleyici aynı kalır, böylece çıktı tipine bakılmaksızın gerçek‑zamanlı ilerleme alırsınız.

## Pratik Uygulamalar
1. **Otomatik Belge Yönetim Sistemleri** – binlerce dosyayı toplu işleyip canlı bir ilerleme panosu gösterin.  
2. **Kurumsal Yazılım Çözümleri** – fatura hatlarını, yasal belge arşivlemeyi veya e‑öğrenme içerik üretimini dönüşümle bütünleştirin.  
3. **İçerik Göç Araçları** – eski formatlardan modern PDF’lere büyük ölçekli göçleri izleyin, duraklamaları erken yakalayın.

## Performans Düşünceleri
- **Bellek Yönetimi:** `Converter`ın hızlıca kapanmasını sağlamak için `try‑with‑resources` (gösterildiği gibi) kullanın.  
- **İş Parçacığı (Threading):** Çok büyük toplular için dönüşümleri paralel iş parçacıklarında çalıştırın, ancak her iş parçacığının kendi dinleyici örneğine sahip olduğundan emin olun, aksi takdirde karışık çıktılar oluşur.  
- **Günlük Kaydı (Logging):** Dinleyicinin `System.out` çağrılarını hafif tutun; üretimde bunları bir logging çerçevesine (SLF4J, Log4j) yönlendirin.

## Yaygın Sorunlar ve Çözümler
| Sorun | Çözüm |
|-------|----------|
| **İlerleme çıktısı yok** | `settingsFactory.setListener(listener);` çağrısının `Converter` oluşturulmadan önce yapıldığını doğrulayın. |
| **Büyük dosyalarda OutOfMemoryError** | JVM heap’ini artırın (`-Xmx2g` veya daha yüksek) ve mümkünse dosyaları daha küçük parçalar halinde işleyin. |
| **Hata durumunda dinleyici tetiklenmiyor** | `converter.convert` çağrısını try‑catch bloğuna alın ve dinleyicinizde özel bir `error(byte code)` metodunu çağırın. |

## Sık Sorulan Sorular

**S:** PDF dışındaki formatlar için de dönüşüm ilerlemesi izlenebilir mi?  
**C:** Evet. Aynı `IConverterListener` GroupDocs.Conversion tarafından desteklenen tüm hedef formatlarla çalışır; sadece seçenek sınıfını değiştirmeniz yeterlidir.

**S:** Büyük belgeleri verimli bir şekilde nasıl yönetirim?  
**C:** Java’nın streaming API’lerini kullanın, JVM heap boyutunu artırın ve dinleyicinin ilerlemesini izleyerek uzun süren adımları tespit edin.

**S:** Dönüşüm yarıda başarısız olursa ne olur?  
**C:** Dinleyicinizde ek metodlar (ör. `error(byte code)`) tanımlayın ve `convert` çağrısını istisna yönetimiyle sararak hataları yakalayıp kaydedin.

**S:** Dosya boyutu veya türü üzerinde sınırlamalar var mı?  
**C:** Çoğu yaygın format desteklenir, ancak çok büyük dosyalar daha fazla bellek gerektirebilir. Ayrıntılı sınırlamalar için resmi [GroupDocs belgelerine](https://docs.groupdocs.com/conversion/java/) bakın.

**S:** Bunu bir web uygulamasında nasıl sunarım?  
**C:** Dönüşüm mantığını bir REST uç noktasına (ör. Spring Boot) sarın ve Server‑Sent Events (SSE) ya da WebSocket üzerinden ilerleme güncellemelerini istemciye akıtın; dinleyicinin çıktısını bu kanala yönlendirin.

## Kaynaklar
- **Dokümantasyon:** [GroupDocs Conversion Documentation](https://docs.groupdocs.com/conversion/java/)
- **API Referansı:** [API Reference](https://reference.groupdocs.com/conversion/java/)
- **İndirme:** [Download GroupDocs.Conversion](https://releases.groupdocs.com/conversion/java/)
- **Satın Alma:** [Buy License](https://purchase.groupdocs.com/buy)
- **Ücretsiz Deneme:** [Try Free Trial](https://releases.groupdocs.com/conversion/java/)
- **Geçici Lisans:** [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Destek Forumu:** [GroupDocs Support](https://forum.groupdocs.com/c/conversion/10)

---

**Son Güncelleme:** 2025-12-19  
**Test Edilen Sürüm:** GroupDocs.Conversion 25.2  
**Yazar:** GroupDocs  

---