---
title: PPTX'yi PDF'ye dönüştür
linktitle: PPTX'yi PDF'ye dönüştür
second_title: GroupDocs.Conversion .NET API'si
description: GroupDocs.Conversion for .NET'i kullanarak PowerPoint sunumlarını (PPTX) PDF formatına nasıl dönüştüreceğinizi öğrenin. Kolay ve verimli dönüştürme işlemi.
weight: 29
url: /tr/net/pdf-conversion/convert-pptx-to-pdf/
---
## giriiş
Bu öğreticide, .NET için GroupDocs.Conversion kitaplığını kullanarak bir PowerPoint sunumu (PPTX) dosyasını Taşınabilir Belge Formatına (PDF) dönüştürme sürecini anlatacağız. Bu dönüşümü gerçekleştirmek için aşağıdaki adımları izleyin.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  GroupDocs.Conversion for .NET Kitaplığı: GroupDocs.Conversion for .NET kitaplığını yüklediğinizden emin olun. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/conversion/net/).
2. Geliştirme Ortamı: Visual Studio veya başka herhangi bir .NET IDE gibi gerekli araçları içeren bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktar
GroupDocs.Conversion işlevlerine erişmek için projenize gerekli ad alanlarını ekleyin.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Adım 1: Çıktı Klasörünü ve Dosya Adını Ayarlayın
İlk olarak, dönüştürülen PDF dosyasının kaydedileceği çıktı klasörünü tanımlayın ve çıktı PDF dosyasının adını belirtin.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Adım 2: Kaynak PPTX Dosyasını Yükleyin
GroupDocs.Conversion kitaplığını kullanarak kaynak PowerPoint sunumu (PPTX) dosyasını yükleyin.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Dönüşüm mantığı buraya yerleştirilecek
}
```
## 3. Adım: Dönüşüm Seçeneklerini Belirleyin
Dönüştürme seçeneklerini tanımlayın. Bu durumda, PDF formatına dönüştürüyoruz, dolayısıyla bir örneğini oluşturun.`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Adım 4: Dönüşümü Gerçekleştirin
 Dönüştürme işlemini kullanarak yürütün.`Convert` yöntemini kullanın ve çıktı dosyası yolunu dönüştürme seçenekleriyle birlikte iletin.
```csharp
converter.Convert(outputFile, options);
```
## Adım 5: Çıktıyı Kontrol Edin
Dönüştürme başarıyla tamamlandıktan sonra, tamamlandığını ve çıktı dosyasının konumunu belirten bir mesaj görüntüleyin.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Çözüm
Bu eğitimde, .NET için GroupDocs.Conversion kitaplığını kullanarak bir PowerPoint sunumu (PPTX) dosyasını Taşınabilir Belge Formatına (PDF) nasıl dönüştüreceğimizi öğrendik. Yukarıda özetlenen adımları takip ederek .NET uygulamalarınızda bu dönüşümü kolaylıkla gerçekleştirebilirsiniz.
## SSS'ler
### S: GroupDocs.Conversion tüm .NET sürümleriyle uyumlu mudur?
C: Evet, GroupDocs.Conversion, .NET Core ve .NET Standard dahil olmak üzere .NET Framework 2.0 ve üstünü destekler.
### S: Dosyaları PDF dışındaki formatlara dönüştürebilir miyim?
C: Evet, GroupDocs.Conversion, dönüştürme için aralarında Word, Excel, HTML ve daha fazlasının da bulunduğu çok çeşitli belge formatlarını destekler.
### S: GroupDocs.Conversion herhangi bir ücretsiz deneme sunuyor mu?
 C: Evet, GroupDocs.Conversion'ın ücretsiz deneme sürümüne şu adresten erişebilirsiniz:[Burada](https://releases.groupdocs.com/).
### S: GroupDocs.Conversion için nasıl destek alabilirim?
 C: GroupDocs topluluk forumundan destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/conversion/11).
### S: GroupDocs.Conversion için geçici bir lisans mevcut mu?
 C: Evet, GroupDocs.Conversion için geçici bir lisansı şuradan alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/).