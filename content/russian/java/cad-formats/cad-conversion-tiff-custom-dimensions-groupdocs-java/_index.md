---
date: '2026-07-24'
description: 'Конвертация изображений Java стала простой: узнайте, как преобразовать
  файлы CAD в TIFF с пользовательскими размерами, используя GroupDocs Conversion Java.
  Пошаговое руководство для разработчиков.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Конвертация изображений Java стала простой. Преобразуйте файлы CAD
  в высококачественные изображения TIFF с пользовательской шириной и высотой, используя
  GroupDocs Conversion Java. Следуйте нашему подробному руководству.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Конвертация изображений Java: CAD в TIFF с пользовательскими размерами'
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
title: 'Конвертация изображений Java: CAD в TIFF с пользовательскими размерами'
type: docs
url: /ru/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Преобразование изображений Java: CAD в TIFF с пользовательскими размерами

Если вам нужно преобразовать чертежи CAD в изображения TIFF высокого разрешения, контролируя точную ширину и высоту в пикселях, **java image conversion** — это ключ. С помощью GroupDocs Conversion Java вы можете растеризовать любой поддерживаемый формат CAD (DWG, DGN, DXF и др.) в файл TIFF, который идеально впишется в отчёты, веб‑порталы или печатные макеты. Это руководство проведёт вас через каждый шаг — от настройки проекта до окончательного преобразования — чтобы вы могли интегрировать процесс в любой Java‑ориентированный рабочий процесс.

## Быстрые ответы
- **Какую библиотеку следует использовать для Java image conversion?** GroupDocs Conversion Java, надёжная библиотека Java image conversion.  
- **Как задать пользовательские размеры для файла CAD?** Используйте `CadLoadOptions` и укажите `setWidth()` и `setHeight()`.  
- **Можно ли преобразовать DWG в TIFF за один шаг?** Да — загрузите CAD, задайте размеры, затем выполните конвертацию с помощью `ImageConvertOptions`.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для оценки; полная лицензия открывает все функции.  
- **Какая версия Java требуется?** Поддерживается любой runtime Java 8+.

## Что такое GroupDocs Conversion Java?
Библиотека `GroupDocs Conversion Java` — это решение **java image conversion**, поддерживающее более 110 форматов ввода и вывода, включая все основные типы CAD и растровых изображений.  
Класс `Converter` является ядром, инициирующим операции конвертации файлов.  
Он предоставляет сервер‑сайд рендеринг, масштабирование и параметры, специфичные для форматов, позволяя разработчикам конвертировать файлы без установки сторонних просмотрщиков.

## Почему преобразовывать CAD в TIFF с пользовательскими размерами?
Задание явных ширины и высоты гарантирует, что полученный TIFF точно соответствует ограничениям макета downstream‑систем. Определяя пиксельные размеры до растеризации, вы избегаете артефактов масштабирования, сохраняете согласованность толщины линий и обеспечиваете бесшовную интеграцию изображения в PDF, веб‑страницы или печатные материалы без дополнительной обработки. Такой подход также упрощает автоматизированные конвейеры, где каждое изображение должно соответствовать предопределённой спецификации размера.  

- **Сохраняет визуальную точность:** Растеризация с разрешением 1920 × 1080 px (или любым другим выбранным размером) сохраняет чёткость линий и штриховки.  
- **Обеспечивает согласованные макеты:** Изображения без проблем встраиваются в PDF, HTML‑страницы или шаблоны печати без дополнительного изменения размеров.  
- **Повышает совместимость:** TIFF универсально поддерживается в Windows, macOS, Linux и большинстве дизайнерских инструментов, уменьшая проблемы с конвертацией форматов.

## Требования
1. **GroupDocs Conversion Java** версии 25.2 или новее (рекомендуется последняя версия).  
2. Java‑IDE, например IntelliJ IDEA или Eclipse.  
3. Maven, установленный для управления зависимостями.  
4. Базовые знания Java и знакомство с `pom.xml` Maven.

## Настройка GroupDocs Conversion Java

Добавьте зависимость GroupDocs Maven в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Получение лицензии:** Вы можете получить бесплатную пробную версию, запросить временную лицензию для полной функциональности или приобрести постоянную лицензию, чтобы полностью разблокировать возможности GroupDocs Conversion.

Как только ваш Java‑проект будет правильно связан с этими зависимостями, вы готовы начать конвертацию файлов CAD!

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

## Как преобразовать CAD в TIFF с пользовательскими размерами?

Преобразование файлов CAD в TIFF с точными размерами включает загрузку исходного чертежа, настройку параметров рендеринга и вызов API конвертации. Следуя линейной последовательности — задавая ширину и высоту, выбирая TIFF в качестве формата вывода и выполняя конвертацию — вы гарантируете, что полученное изображение соответствует точным требованиям ваших downstream‑приложений, сохраняя при этом детали и качество оригинального чертежа.  

1. **Импортировать необходимые классы** (см. пошаговое описание ниже).  
2. **Создать экземпляр `CadLoadOptions`** и задать `width` и `height` в требуемые размеры.  
3. **Создать `ImageConvertOptions`**, указав `ImageFileType.Tiff`.  
4. **Вызвать метод `convert`** у объекта `Converter`, передав путь к источнику, параметры загрузки и параметры конвертации.

### Загрузка CAD‑документов с пользовательскими размерами (Как задать размеры)

Класс `CadLoadOptions` сообщает GroupDocs, как растеризовать чертеж перед конвертацией.

`CadLoadOptions` — это объект конфигурации, определяющий параметры рендеринга, такие как ширина, высота и DPI для файлов CAD.

#### Шаг 1: Импортировать необходимые библиотеки
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Шаг 2: Настроить параметры загрузки с пользовательскими размерами
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Explanation:* By configuring `CadLoadOptions`, you tell **GroupDocs Conversion Java** to rasterize the CAD drawing at 1920 × 1080 pixels before any further processing.

### Преобразование CAD в TIFF‑изображение (Convert CAD to TIFF)

`ImageConvertOptions` указывает библиотеке создать файл TIFF с заданными параметрами.

`ImageConvertOptions` инкапсулирует все параметры конвертации, специфичные для изображений, включая формат вывода, разрешение и уровень сжатия.

#### Шаг 3: Настроить параметры конвертации
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Шаг 4: Выполнить конвертацию
```java
converter.convert(convertedFilePath, options);
```
*Explanation:* Setting `ImageFileType.Tiff` directs **GroupDocs Conversion Java** to output a high‑quality TIFF file that respects the width and height you defined earlier.

## Советы по устранению неполадок и распространённые ошибки
- **Проблемы с путями файлов:** Убедитесь, что пути к источнику и назначению указаны правильно и приложение имеет права чтения/записи.  
- **Неподдерживаемые форматы:** Убедитесь, что файл CAD относится к поддерживаемым форматам (DWG, DGN, DXF и др.).  
- **Ограничения памяти:** Большие чертежи могут потребовать увеличения размера кучи JVM (`-Xmx2g` или больше).  
- **Проблемы с качеством:** При необходимости отрегулируйте параметры разрешения в `ImageConvertOptions`, если DPI по умолчанию не удовлетворяет требованиям качества.  

## Практические применения
1. **Визуализация архитектуры:** Экспорт планов этажей в TIFF для презентаций высокого разрешения.  
2. **Инженерная документация:** Генерация стандартизированных изображений для включения в технические руководства.  
3. **Автоматизированные отчёты:** Встраивание TIFF‑изображений, полученных из CAD, в PDF или HTML‑отчёты через CI‑конвейер.  

## Соображения по производительности
- **Оптимизация использования памяти:** Освобождайте экземпляр `Converter` после конвертации (`converter.close()`, если применимо).  
- **Пакетная обработка:** Проходите по списку файлов CAD и переиспользуйте одну конфигурацию `Converter`, чтобы снизить накладные расходы.  
- **Поддерживайте актуальность:** Регулярно обновляйте до последней версии GroupDocs Conversion Java, чтобы воспользоваться улучшениями производительности и исправлениями ошибок.  

## Часто задаваемые вопросы

**Q:** Какие форматы файлов поддерживает GroupDocs Conversion?  
**A:** Поддерживается более 110 форматов, включая CAD‑файлы (DWG, DGN, DXF) и распространённые типы изображений, документов и архивов.

**Q:** Можно ли конвертировать несколько файлов CAD одновременно?  
**A:** Да — реализуйте простой цикл, создающий новый `Converter` для каждого файла, либо переиспользуйте один экземпляр с разными путями к источникам.

**Q:** Как работать с большими файлами во время конвертации?  
**A:** Увеличьте размер кучи JVM, обрабатывайте файлы небольшими партиями или используйте потоковые опции, предоставляемые библиотекой.

**Q:** Что делать, если качество выходного изображения неудовлетворительно?  
**A:** Отрегулируйте DPI или параметры масштабирования в `ImageConvertOptions`, чтобы повысить разрешение.

**Q:** Доступна ли поддержка в случае возникновения проблем?  
**A:** GroupDocs предоставляет обширную документацию, форумы сообщества и прямую поддержку для лицензированных клиентов.

## Ресурсы
- [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)
- [API Reference](https://reference.groupdocs.com/conversion/java/)
- [Download Latest Release](https://releases.groupdocs.com/conversion/java/)
- [Purchase Licenses](https://purchase.groupdocs.com/buy)
- [Free Trial Access](https://releases.groupdocs.com/conversion/java/)
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/conversion/10)

---

**Last Updated:** 2026-07-24  
**Tested With:** GroupDocs Conversion Java 25.2  
**Author:** GroupDocs  

---

## Связанные руководства

- [convert cad pdf java – CAD Formats Conversion Tutorials for GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Guide](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [How to Set License for GroupDocs.Conversion Java - Step‑By‑Step Guide](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)