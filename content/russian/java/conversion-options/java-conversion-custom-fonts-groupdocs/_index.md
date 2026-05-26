---
date: '2026-01-28'
description: Узнайте, как конвертировать презентацию в PDF с пользовательской заменой
  шрифтов, используя GroupDocs.Conversion для Java. Сохраните шрифты и обеспечьте
  единообразный вид документа.
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: Как конвертировать презентацию в PDF с пользовательскими шрифтами, используя
  GroupDocs.Conversion для Java
type: docs
url: /ru/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# Как конвертировать презентацию в PDF с пользовательскими шрифтами с помощью GroupDocs.Conversion для Java

В современных бизнес‑процессах часто требуется **конвертировать презентацию в pdf**, сохраняя оригинальный внешний вид. Будь то обмен клиентской презентацией, архивирование учебных материалов или автоматизация генерации отчетов, отсутствие шрифтов может испортить визуальное качество. В этом руководстве показано, как сохранить шрифты при конвертации Java pptx в pdf с использованием **GroupDocs.Conversion for Java**.

## Быстрые ответы
- **Какова основная выгода от пользовательской подстановки шрифтов?** Это гарантирует, что PDF выглядит точно так же, как исходная презентация, даже если оригинальные шрифты не установлены на целевой машине.  
- **Какая библиотека обрабатывает конвертацию?** `GroupDocs.Conversion` for Java.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для разработки; для продакшна требуется коммерческая лицензия.  
- **Можно ли использовать это в Maven‑проекте?** Да — просто добавьте репозиторий и зависимость, показанные ниже.  
- **Является ли процесс потокобезопасным?** `Converter`‑экземпляр лёгкий; вы можете создавать по одному на каждый поток конвертации.

## Что такое **конвертировать презентацию в pdf**?
Эта фраза просто описывает процесс преобразования файла PowerPoint (.pptx) в документ PDF. Конвертация в PDF делает файл универсально просматриваемым, печатаемым и более удобным для архивирования, при этом сохраняет макет, изображения и текст.

## Почему использовать **custom font substitution**?
- **Brand consistency:** Убедитесь, что корпоративные шрифты отображаются корректно даже на машинах, где их нет.  
- **Cross‑platform reliability:** PDF‑файлы отображаются одинаково в Windows, macOS, Linux и на мобильных устройствах.  
- **Reduced support tickets:** Больше нет запросов «мой PDF выглядит странно, потому что шрифт отсутствует».  

## Предварительные требования
1. **Java Development Kit (JDK)** – версия 8 или выше.  
2. **Maven** – для управления зависимостями.  
3. **IDE** – IntelliJ IDEA, Eclipse или любой совместимый с Java редактор.  
4. **Базовые знания Java** – вы должны быть уверены в работе с классами и методами.  

## Настройка GroupDocs.Conversion для Java

Интегрируйте библиотеку GroupDocs.Conversion в ваш Maven‑проект. Ниже приведён XML‑фрагмент, который добавляет официальный репозиторий и необходимую зависимость.

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

### Приобретение лицензии
- **Free Trial:** Скачайте пробную версию с сайта GroupDocs.  
- **Temporary License:** Запросите временный ключ для расширенного тестирования.  
- **Purchase:** Перейдите на полную лицензию, когда будете удовлетворены результатом.

После того как Maven разрешит зависимость, можно приступать к написанию кода конвертации.

## Руководство по реализации

### Шаг 1: Определите параметры загрузки презентации с подстановкой шрифтов
Следующий метод создаёт объект `PresentationLoadOptions` и указывает GroupDocs, как заменять отсутствующие шрифты. Это ядро **как сохранить шрифты** во время конвертации.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.PresentationLoadOptions;
import com.groupdocs.conversion.contracts.FontSubstitute;
import java.util.ArrayList;
import java.util.List;

public PresentationLoadOptions definePresentationLoadOptionsWithFontSubstitution() {
    // Initialize PresentationLoadOptions
    PresentationLoadOptions loadOptions = new PresentationLoadOptions();
    
    // Create a list to hold font substitutes
    List<FontSubstitute> fontSubstitutes = new ArrayList<>();
    
    // Add font substitution mappings
    fontSubstitutes.add(FontSubstitute.create("Tahoma", "Arial"));
    fontSubstitutes.add(FontSubstitute.create("Times New Roman", "Arial"));
    
    // Set default font to be used if a specific font is not found
    loadOptions.setDefaultFont("YOUR_DOCUMENT_DIRECTORY/resources/fonts/Helvetica.ttf");
    
    // Apply the font substitutes to the load options
    loadOptions.setFontSubstitutes(fontSubstitutes);
    
    return loadOptions;
}
```

**Пояснение**  
- **Font Substitution:** Сопоставляет «Tahoma» и «Times New Roman» со шрифтом «Arial».  
- **Default Font:** Предоставляет запасной вариант (`Helvetica.ttf`), если ни одно сопоставление не подходит.  

### Шаг 2: Конвертировать документ презентации в PDF с расширенными параметрами
Теперь используем параметры загрузки из Шага 1 для выполнения операции **конвертировать презентацию в pdf**.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public void defineConversionProcessWithAdvancedOptions(PresentationLoadOptions loadOptions) {
    // Specify the path for the converted PDF file
    String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedPresentation.pdf";
    
    // Initialize Converter with the presentation file and load options
    Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/Presentation.pptx", () -> loadOptions);
    
    // Set up PDF conversion options (empty for default configuration)
    PdfConvertOptions options = new PdfConvertOptions();
    
    // Perform the conversion from presentation to PDF
    converter.convert(convertedFile, options);
}
```

**Пояснение**  
- **Converter Initialization:** Передаёт путь к PPTX вместе с пользовательским `loadOptions`.  
- **PDF Conversion Options:** При необходимости можно дополнительно настроить параметры (например, качество изображений).  

## Практические применения
1. **Бизнес‑презентации:** Сохраняйте фирменный стиль при обмене PDF‑файлами с внешними партнёрами.  
2. **Учебные материалы:** Конвертируйте лекционные слайды в PDF для офлайн‑изучения без риска отсутствия шрифтов.  
3. **Юридические документы:** Сохраняйте точный макет доказательных слайдов для подачи в суд.  

## Соображения по производительности
- **Управление памятью:** Выделяйте достаточный объём heap‑памяти для больших презентаций (`-Xmx2g` — хорошая отправная точка).  
- **Ограничьте подстановки шрифтов:** Сопоставляйте только действительно нужные шрифты; избыточные сопоставления могут замедлить обработку.  
- **Сборка мусора:** Вызывайте `System.gc()` после больших пакетных конвертаций, если замечаете всплески использования памяти.  

## Распространённые проблемы и решения
| Проблема | Решение |
|-------|----------|
| **Missing default font file** | Убедитесь, что путь в `setDefaultFont` указывает на существующий файл `.ttf` и что файл доступен для чтения. |
| **Conversion hangs on large PPTX** | Увеличьте размер heap‑памяти JVM и рассмотрите возможность конвертации слайдов пакетами. |
| **Font not substituted as expected** | Проверьте, что имя исходного шрифта точно совпадает (с учётом регистра) с именем, использованным в `FontSubstitute.create`. |
| **Output PDF is blank** | Убедитесь, что исходный PPTX не повреждён и что `Converter` указывает на правильный путь к файлу. |

## Часто задаваемые вопросы

**Q: Какова основная выгода от использования пользовательских подстановок шрифтов при конвертации?**  
A: Пользовательская подстановка шрифтов гарантирует, что PDF сохраняет задуманное оформление, даже когда оригинальные шрифты недоступны на целевой системе.

**Q: Как обработать неподдерживаемые шрифты во время конвертации?**  
A: Используйте функцию `FontSubstitute`, чтобы сопоставить недоступные шрифты альтернативным, обеспечивая единообразную эстетику документа.

**Q: Можно ли использовать GroupDocs.Conversion с облачными хранилищами?**  
A: Да, GroupDocs предлагает интеграции, позволяющие выполнять конвертации напрямую из облачных хранилищ, таких как AWS S3 и Azure Blob Storage.

**Q: Что делать, если процесс конвертации работает медленно?**  
A: Оптимизируйте системные ресурсы, ограничьте количество сопоставлений шрифтов и увеличьте размер heap‑памяти JVM для повышения производительности.

**Q: Является ли это руководство частью более крупного **document conversion tutorial java** сериала?**  
A: Абсолютно — данный гайд фокусируется на пользовательских шрифтах, но серия также охватывает извлечение изображений, добавление водяных знаков и пакетную обработку с помощью GroupDocs.Conversion для Java.

## Заключение
Теперь у вас есть полностью готовый к продакшну подход к **конвертировать презентацию в pdf** с сохранением шрифтов с помощью **GroupDocs.Conversion for Java**. Определив параметры загрузки с подстановкой шрифтов и используя мощный API `Converter`, вы можете гарантировать визуальное соответствие на любой платформе.

**Следующие шаги**  
- Поэкспериментируйте с дополнительными `PdfConvertOptions` (например, настройкой соответствия PDF/A).  
- Интегрируйте логику конвертации в REST‑службу для генерации PDF‑файлов по запросу.  
- Изучите другие модули GroupDocs, такие как `GroupDocs.Annotation`, для добавления комментариев в сгенерированные PDF.

---

**Последнее обновление:** 2026-01-28  
**Тестировано с:** GroupDocs.Conversion 25.2 for Java  
**Автор:** GroupDocs  

---