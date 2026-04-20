---
date: '2026-01-26'
description: GroupDocs.Conversion for Java kullanarak dwg'yi pdf'ye nasıl dönüştüreceğinizi
  öğrenin. Maven kurulumu, seçici düzen dönüşümü ve performans ipuçları içerir.
keywords:
- convert dwg to pdf
- selective layout conversion
- GroupDocs.Conversion for Java
title: 'dwg''yi pdf''ye dönüştür: Java''da GroupDocs ile Seçmeli Düzen Dönüştürme'
type: docs
url: /tr/java/cad-formats/groupdocs-java-cad-to-pdf-selective-layouts/
weight: 1
---

# dwg'yi pdf'ye dönüştürme GroupDocs.Conversion for Java ile
## Java'da Seçici CAD'den PDF'ye Dönüşümde Uzmanlaşma
### Giriş
Bir CAD belgesinden yalnızca belirli düzenleri PDF'ye dönüştürmekte zorlanıyor musunuz nasıl yapacağınızı gösterir. Mimari planlar ya da mühendislik tasarımlarıyla çalışıyor olun, yalnızca gereken bölümleri filtre ve iş akışlarını basitleştirir.

Bu öğreticide şunları öğreneceksiniz:
- **GroupDocs.Conversion için Maven kurulumu**
- **CAD belgelerinin PDF'ye seçici düzen dönüşümü**
 deposunuim?** Evet – `CadLoadOptions.setLayoutNames` kullanın  
- **Gerekli Java sürümü nedir?** JDK 8 veya daha yeni  
- **Lisans gerekir mi?** Tam özellikler için deneme veya satın alınmış bir lisans gereklidir  

## **convert dwg to pdf** nedir?
DWG'yi PDF'ye dönüştürmek, vektör tabanlı CAD çizimlerini evrensel olarak görüntülenebilir bir belge formatına çevirir. Bu süreç, geometrileri, katmanları ve düzen doğruluğunu korurken dosyaların paylaşımını, yazdırılmasını veya arşivlenmesini kolaylaştırır.

## Neden seçici düzen dönüşümü kullanılmalı?
Seçici dönüşüm, büyük bir CAD dosyasının yalnızca ilgili bölümlerini—örneğin belirli kat planları veya kesitler—çıkararak dosya boyutunu küçültmenizi, işlem süresini azaltmanızı ve paydaşların gerçekten önemli olan bölümlere odaklanmasını sağlar.

## Önkoşullar
- **Java Development Kit (JDK):** Versiyon 8 veya üzeri  
- **Maven:** Bağımlılık yönetimi ve proje derleme otomasyonu için  
- **IDE:** IntelliJ IDEA, Eclipse veya herhangi bir Java uyumlu editör  
- Java ve Maven projelerine temel aşinalık  

## GroupDocs.Conversion for Java Kurulumu
GroupDocs.Conversion'ı kullanmak için, kütüphaneyi Maven aracılığıyla Java uygulamanıza entegre edin.

### Maven Yapılandırması (Maven ile cad nasıl dönüştürülür)
`pom.xml` dosyanıza bu yapılandırmayı ekleyin:

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

### Lisans Alımı
Tam özellikleri açmak için bir deneme lisansı alın veya uzun vadeli kullanım için satın alın:

- **Ücretsiz Deneme:** [Buradan İndir](https://releases.groupdocs.com/conversion/java/)
- **Geçici Lisans:** [Buradan Talep Et](https://purchase.groupdocs.com/temporary-license/)
- **Satın Al:** [Şimdi Satın Al](https://purchase.groupdocs.com/buy)

Lisans dosyanızla GroupDocs.Conversion'ı başlatın:

```java
// Load the license to unlock full features
License license = new License();
license.setLicense("path/to/license.lic");
```

## Uygulama Rehberi
### Adım 1: Dosya Yollarını ve Düzenleri Belirtin (java cad to pdf)
Girdi CAD dosyanız ve çıktı PDF için yolları ayarlayın, hangi düzenleri dönüştürmek istediğinizi tanımlayın:

```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.dwg";
String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyLayouts.pdf";

// Specify desired layout names
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setLayoutNames(new String[] { "Layout1", "Layout3" });
```

### Adım 2: Dönüştürücüyü Başlatın
`Converter` örneğini kaynak yol ve düzenleri filtreleyen yük seçenekleriyle oluşturun:

```java
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
```

### Adım 3: Dönüşüm Seçeneklerini Ayarlayın
`PdfConvertOptions` kullanarak PDF dönüşüm ayarlarını yapılandırın. Gerektiğinde DPI, sayfa boyutu veya gömülü fontları ayarlayabilirsiniz:

```java
PdfConvertOptions convertOptions = new PdfConvertOptions();
```

### Adım 4: Dönüşümü Gerçekleştirin
Dönüşüm sürecini yürütün. Oluşan PDF, **yalnızca** belirtilen düzenleri içerecek:

```java
converter.convert(convertedFile, convertOptions);
```

## Pratik Uygulamalar
Seçici düzen dönüşümü aşağıdaki senaryolarda faydalı olabilir:
- **Mimari Tasarım İncelemeleri:** Toplantılar sırasında belirli kat planlarına veya kesitlere odaklanın.  
- **Mühendislik Analizi:** Ayrıntılı inceleme için yalnızca ilgili tasarım bölümlerini dönüştürün.  
- **Dokümantasyon ve Arşivleme:** Kayıtlar için özlü PDF'ler oluşturun, depolama alanından tasarruf edin.

## Performans Düşünceleri
Büyük CAD dosyalarıyla çalışırken:
- **Bellek Yönetimi:** `-Xmx2g` gibi JVM seçenekleriyle yeterli yığın boyutu ayırın.  
- **Toplu İşleme:** Kaynak kullanımını öngörülebilir tutmak için birden fazla dosyayı toplu olarak işleyin.  

## Yaygın Sorunlar ve Çözümler
- **Eksik Düzenler:** `setLayoutNames`'e verilen düzen adlarının DWG dosyasındaki adlarla tam olarak eşleştiğinden (büyük/küçük harf duyarlı) emin olun.  
- **Bellek Yetersizliği Hataları:** JVM yığın boyutunu artırın veya dosyaları daha küçük partilerde işleyin.  
- **Lisans Hataları:** Lisans dosyası yolunun doğru olduğundan ve lisansın kütüphane sürümü için geçerli olduğundan emin olun.

## SSS Bölümü
1. **GroupDocs.Conversion for Java kullanmak için sistem gereksinimleri nelerdir?**  
   - JDK 8+, Maven ve IntelliJ IDEA veya Eclipse gibi bir IDE'ye ihtiyacınız var.  
2. **GroupDocs.Conversion ile büyük dosyaları nasıl yönetirim?**  
   - JVM ayarlarınızı (ör. `-Xmx`) ayarlayın ve toplu işleme düşünün.  
3. **Bu yöntemle diğer CAD formatlarını dönüştürebilir miyim?**  
   - Evet, GroupDocs.Conversion DXF, DGN ve diğer CAD formatlarını destekler.  
4. **Dönüşüm sonrası bazı düzenler eksikse ne yapmalıyım?**  
   - `setLayoutNames`'e verilen düzen adlarını tekrar kontrol edin.  
5. **GroupDocs.Conversion'ı bir web uygulamasına nasıl entegre edebilirim?**  
   - Kütüphaneyi içeren Java backend'i dağıtın ve dosya dönüşümü için REST uç noktaları sunun.

## Kaynaklar
- **Documentation:** [GroupDocs Conversion Documentation](https://docs.groupdocs.com/conversion/java/)
- **API Referansı:** [GroupDocs API Reference](https://reference.groupdocs.com/conversion/java/)
- **İndirme:** [Kütüphaneyi Edinin](https://releases.groupdocs.com/conversion/java/)
- **Satın Al:** [Şimdi Satın Al](https://purchase.groupdocs.com/buy)
- **Ücretsiz Deneme:** [Buradan Başlayın](https://releases.groupdocs.com/conversion/java/)
- **Geçici Lisans:** [Geçici Lisans Talep Et](https://purchase.groupdocs.com/temporary-license/)
- **Destek:** [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)

---

**Son Güncelleme:** 2026-01-26  
**Test Edilen Versiyon:** GroupDocs.Conversion 25.2 for Java  
**Yazar:** GroupDocs