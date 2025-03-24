---
title: DNG Görüntülerini PDF'ye Dönüştür
linktitle: DNG Görüntülerini PDF'ye Dönüştür
second_title: GroupDocs.Conversion .NET API'si
description: GroupDocs.Conversion for .NET'i kullanarak DNG görüntülerini zahmetsizce PDF'ye nasıl dönüştüreceğinizi öğrenin. Sorunsuz dönüşüm için adım adım kılavuzumuzu izleyin.
weight: 21
url: /tr/net/file-conversion-to-pdf/convert-dng-to-pdf/
---
## giriiş
Bu öğreticide, GroupDocs.Conversion for .NET'i kullanarak DNG görüntülerini PDF'ye dönüştürme sürecinde size rehberlik edeceğiz. DNG (Dijital Negatif), dijital fotoğrafçılıkta kullanılan bir dosya formatıdır. DNG görüntülerini PDF'ye dönüştürerek bunları kolayca paylaşabilir veya evrensel olarak kabul edilen bir formatta saklayabilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  .NET için GroupDocs.Conversion: .NET için GroupDocs.Conversion kitaplığını şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/conversion/net/).
2. Kaynak DNG Dosyası: PDF'ye dönüştürmek istediğiniz bir DNG resim dosyasına ihtiyacınız var.
3. Geliştirme Ortamı: Bir .NET geliştirme ortamı kurduğunuzdan emin olun.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını projenize aktarmanız gerekir. Kod dosyanıza aşağıdaki kullanma yönergelerini ekleyin:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Adım 1: Kaynak DNG Dosyasını Yükleyin
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Kaynak DNG dosyasını yükleyin
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Dönüştürme işlemine devam edin
}
```
 Bu adımda, dönüştürülen PDF dosyasının kaydedileceği çıktı klasörünü tanımlarsınız. Değiştirildiğinden emin olun`"Your Document Directory"` İstediğiniz dizinin yolu ile birlikte. Daha sonra çıktı PDF dosyasının adını ve yolunu belirtirsiniz.
## Adım 2: DNG'yi PDF'ye dönüştürün
```csharp
var options = new PdfConvertOptions();
// Dönüştürülen PDF dosyasını kaydet
converter.Convert(outputFile, options);
```
 Burada şunun bir örneğini yaratırsınız:`PdfConvertOptions` Gerekirse PDF dönüştürmeye yönelik belirli seçenekleri ayarlamak için. Daha sonra, şu numarayı ararsınız:`Convert` yöntemi`converter`nesne, çıktı dosyası yolunu ve dönüştürme seçeneklerini ileterek.
## 3. Adım: Dönüşümün Tamamlanmasını İşleyin
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Dönüştürme işlemi tamamlandıktan sonra, dönüştürülen PDF dosyasının bulunduğu dizinle birlikte bir başarı mesajı görüntülersiniz.

## Çözüm
Sonuç olarak, DNG görüntülerini PDF'ye dönüştürmek GroupDocs.Conversion for .NET kullanılarak kolayca gerçekleştirilebilir. Bu eğitimde özetlenen basit adımları izleyerek DNG dosyalarınızı verimli bir şekilde PDF formatına dönüştürebilir, böylece onları daha erişilebilir ve paylaşılabilir hale getirebilirsiniz.
## SSS'ler
### GroupDocs.Conversion for .NET, .NET'in tüm sürümleriyle uyumlu mu?
Evet, GroupDocs.Conversion for .NET, .NET Framework 4.6.1 ve üzerinin yanı sıra .NET Core 2.0 ve üzeri ile uyumludur.
### Birden fazla DNG dosyasını aynı anda PDF'ye dönüştürebilir miyim?
Evet, her bir dosyayı yineleyerek ve her biri için dönüştürme işlemini gerçekleştirerek birden fazla DNG dosyasını PDF'ye dönüştürebilirsiniz.
### Dönüştürülebilecek DNG dosyalarının boyutunda herhangi bir sınırlama var mı?
GroupDocs.Conversion for .NET'in dönüştürülebilecek DNG dosyalarının boyutu konusunda belirli bir sınırlaması yoktur. Ancak performans, giriş dosyalarının boyutuna ve karmaşıklığına bağlı olarak değişebilir.
### PDF çıktısı için dönüştürme seçeneklerini özelleştirebilir miyim?
 Evet, sayfa boyutu, yönlendirme, sıkıştırma ve daha fazlası gibi çeşitli seçenekleri özelleştirebilirsiniz.`PdfConvertOptions`.NET için GroupDocs.Conversion tarafından sağlanan sınıf.
### GroupDocs.Conversion for .NET için teknik destek mevcut mu?
 Evet, teknik desteğe GroupDocs forumu aracılığıyla ulaşılabilir[Burada](https://forum.groupdocs.com/c/conversion/11)Soru sorabileceğiniz ve uzmanlardan yardım alabileceğiniz yer.