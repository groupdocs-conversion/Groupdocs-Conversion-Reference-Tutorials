---
title: Конвертировать PPTX в PDF
linktitle: Конвертировать PPTX в PDF
second_title: GroupDocs.Conversion .NET API
description: Узнайте, как конвертировать презентации PowerPoint (PPTX) в формат PDF с помощью GroupDocs.Conversion для .NET. Простой и эффективный процесс преобразования.
weight: 29
url: /ru/net/pdf-conversion/convert-pptx-to-pdf/
---

# Конвертировать PPTX в PDF

## Введение
В этом руководстве мы рассмотрим процесс преобразования файла презентации PowerPoint (PPTX) в формат переносимого документа (PDF) с использованием библиотеки GroupDocs.Conversion для .NET. Следуйте инструкциям ниже, чтобы добиться этого преобразования.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Conversion для библиотеки .NET. Убедитесь, что вы установили библиотеку GroupDocs.Conversion для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/conversion/net/).
2. Среда разработки: настройте среду разработки с необходимыми инструментами, такими как Visual Studio или любая другая .NET IDE.

## Импортировать пространства имен
Включите в свой проект необходимые пространства имен для доступа к функциям GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Шаг 1. Установите выходную папку и имя файла
Сначала определите выходную папку, в которой будет сохранен преобразованный PDF-файл, и укажите имя выходного PDF-файла.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Шаг 2. Загрузите исходный файл PPTX
Загрузите исходный файл презентации PowerPoint (PPTX) с помощью библиотеки GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Логика преобразования будет размещена здесь
}
```
## Шаг 3. Укажите параметры преобразования
Определите параметры преобразования. В данном случае мы конвертируем в формат PDF, поэтому создайте экземпляр`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Шаг 4. Выполните преобразование
 Выполните процесс преобразования, используя`Convert` метод и передайте путь к выходному файлу вместе с параметрами преобразования.
```csharp
converter.Convert(outputFile, options);
```
## Шаг 5: Проверьте вывод
После успешного завершения преобразования отобразится сообщение с указанием завершения и местоположения выходного файла.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Заключение
В этом руководстве мы узнали, как преобразовать файл презентации PowerPoint (PPTX) в формат переносимого документа (PDF) с помощью библиотеки GroupDocs.Conversion для .NET. Выполнив описанные выше шаги, вы сможете легко выполнить это преобразование в своих приложениях .NET.
## Часто задаваемые вопросы
### Вопрос. Совместим ли GroupDocs.Conversion со всеми версиями .NET?
О: Да, GroupDocs.Conversion поддерживает .NET Framework 2.0 и более поздние версии, включая .NET Core и .NET Standard.
### Вопрос: Могу ли я конвертировать файлы в форматы, отличные от PDF?
О: Да, GroupDocs.Conversion поддерживает преобразование широкого спектра форматов документов, включая Word, Excel, HTML и другие.
### Вопрос: Предлагает ли GroupDocs.Conversion бесплатную пробную версию?
 О: Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Conversion на сайте[здесь](https://releases.groupdocs.com/).
### Вопрос: Как я могу получить поддержку для GroupDocs.Conversion?
 О: Вы можете получить поддержку на форуме сообщества GroupDocs.[здесь](https://forum.groupdocs.com/c/conversion/11).
### Вопрос: Доступна ли временная лицензия для GroupDocs.Conversion?
 О: Да, вы можете получить временную лицензию для GroupDocs.Conversion на сайте[здесь](https://purchase.groupdocs.com/temporary-license/).