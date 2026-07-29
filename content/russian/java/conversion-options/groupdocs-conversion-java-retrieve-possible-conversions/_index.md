---
date: '2026-07-29'
description: Узнайте, как вывести список форматов и получить все возможные конверсии
  с помощью GroupDocs.Conversion for Java, идеально для рабочих процессов конвертации
  файлов в облачном хранилище.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Изучите, как вывести список форматов и получить все возможные конверсии
  с помощью GroupDocs.Conversion for Java. Идеально для конвейеров конвертации файлов
  в облачном хранилище.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Как вывести список форматов с помощью GroupDocs.Conversion for Java
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
title: Как вывести список форматов с помощью GroupDocs.Conversion for Java
type: docs
url: /ru/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Как вывести список форматов и получить все возможные конверсии с GroupDocs.Conversion для Java

В многих проектах обработки документов первым шагом является знание **как вывести список форматов**, поддерживаемых движком конверсии. Этот учебник показывает вам шаг за шагом, как запросить GroupDocs.Conversion для Java, получить каждую пару исходный‑целевой и применить эти знания в конвейерах конверсии файлов в облачном хранилище. К концу вы получите переиспользуемый метод, возвращающий полную матрицу конверсий, а также практические советы по производительности и обработке ошибок.

## Быстрые ответы
- **Что означает “list formats”?** Возвращает каждую пару исходный‑целевой конверсия, которую библиотека может обработать.  
- **Нужна ли лицензия?** Бесплатная пробная версия подходит для тестирования; платная лицензия требуется для продакшена.  
- **Поможет ли это при конвертации файлов в облачном хранилище?** Да — знание поддерживаемых форматов позволяет автоматизировать конвертации в облачных конвейерах.  
- **Какая версия Java требуется?** JDK 8 или новее.  
- **Потокобезопасна ли функция?** Экземпляр `Converter` можно переиспользовать в разных потоках, но после использования освобождайте ресурсы.

## Что такое “list formats” в GroupDocs.Conversion?
Операция **list formats** возвращает коллекцию, описывающую каждый исходный формат вместе с целевыми форматами, в которые его можно преобразовать. Эта матрица генерируется на основе внутренних правил конверсии библиотеки и необходима для построения динамических рабочих процессов, адаптирующихся к реальным возможностям GroupDocs.Conversion во время выполнения.

## Почему использовать GroupDocs.Conversion для Java?
GroupDocs.Conversion для Java поддерживает **более 200 входных форматов** и **более 200 выходных форматов**, охватывая всё от DOCX и PPTX до PDF/A и типов изображений. Он полностью работает на сервере, поэтому Microsoft Office или продукты Adobe не требуются. API потокобезопасен, может обрабатывать документы из сотен страниц без загрузки всего файла в память и бесшовно интегрируется с облачными сервисами хранения, такими как AWS S3, Azure Blob и Google Cloud Storage.

## Предварительные требования
- **Java Development Kit (JDK):** Версия 8 или новее.  
- **Maven:** Правильно настроен в вашей IDE (IntelliJ IDEA, Eclipse, NetBeans и т.д.).  
- **GroupDocs.Conversion для Java:** Добавлен как зависимость Maven (см. ниже).  

## Настройка GroupDocs.Conversion для Java

Добавьте репозиторий GroupDocs и зависимость в ваш `pom.xml`:

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

### Получение лицензии
Начните с бесплатной пробной версии, чтобы изучить API. Для производственных нагрузок необходимо приобрести лицензию или запросить временную оценочную лицензию.

### Базовая инициализация и настройка

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

## Как вывести список форматов с помощью GroupDocs.Conversion для Java
`Converter` — основной класс, выполняющий конвертации и предоставляющий информацию о форматах. `getAllPossibleConversions()` возвращает список всех поддерживаемых пар исходный‑целевой. `ConversionInfo` представляет отдельное сопоставление между исходным и целевым форматом.

Загрузите движок `Converter`, вызовите `getAllPossibleConversions()`, и вы получите список объектов `ConversionInfo`, описывающих каждую допустимую пару исходный‑целевой. Этот один вызов достаточно, чтобы построить выпадающий список вариантов экспорта, проверять входящие файлы или разрабатывать скрипты пакетной миграции.

### Инициализация и получение конверсий
Класс `Converter` — основной движок, предоставляющий возможности конверсии и раскрывающий метод `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Итерация по возможным конверсиям

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Определение типов конверсий

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Полная функция

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

## Сценарии конверсии файлов в облачном хранилище
Знание полной матрицы конверсий особенно ценно при построении сервисов **конверсии файлов в облачном хранилище**:

1. **Динамическое определение формата:** Когда файл появляется в облачном хранилище, вы можете мгновенно проверить, поддерживается ли желаемый целевой формат.  
2. **Пакетная миграция:** Перенесите большие библиотеки документов в единый формат (например, PDF/A), перебирая поддерживаемые типы исходных файлов.  
3. **Экспорт по запросу пользователя:** Предоставьте конечным пользователям выпадающий список только тех форматов, в которые их текущий документ может быть экспортирован, уменьшая количество ошибок и улучшая UX.

## Соображения по производительности
- **Управление ресурсами:** Освобождайте экземпляр `Converter` или используйте try‑with‑resources, если создаёте множество короткоживущих конвертеров.  
- **Пакетная обработка:** Объединяйте несколько файлов в одну задачу, чтобы уменьшить накладные расходы.  
- **Кеширование:** Кешируйте результат `getAllPossibleConversions()`, если часто делаете запрос; матрица конверсий редко меняется во время выполнения.  

## Распространённые проблемы и решения

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Нет вывода | `Converter` не инициализирован корректно | Убедитесь, что JAR библиотеки находится в classpath и лицензия загружена. |
| Список `TargetConversion` пуст | Используется устаревшая версия библиотеки | Обновите до последней версии GroupDocs.Conversion. |
| Пики памяти при больших документах | Не освобождаются ресурсы конвертера | Вызовите `converter.close()` или используйте try‑with‑resources. |

## Часто задаваемые вопросы

**В:** Что такое GroupDocs.Conversion для Java?  
**О:** Это серверная библиотека, поддерживающая более 200 входных и более 200 выходных форматов, обеспечивающая быструю конверсию документов без лицензий и без внешнего программного обеспечения.

**В:** Как начать работу с GroupDocs.Conversion?  
**О:** Настройте ваш Maven‑проект, добавьте зависимость, показанную выше, загрузите файл лицензии и создайте экземпляр класса `Converter`, как продемонстрировано в разделе инициализации.

**В:** Можно ли конвертировать пользовательские типы файлов с помощью GroupDocs.Conversion?  
**О:** Да — через точки расширения API вы можете регистрировать пользовательские конвертеры или подключать сторонние обработчики для проприетарных форматов.

**В:** Какие распространённые подводные камни при реализации конверсий?  
**О:** Забвение закрыть `Converter`, использование старой версии JAR или игнорирование потребления памяти при очень больших PDF. Следуйте советам по управлению ресурсами выше.

**В:** Где можно получить дополнительную помощь?  
**О:** Посетите официальную [документацию](https://docs.groupdocs.com/conversion/java/) или задавайте вопросы на форуме сообщества GroupDocs.

---

**Последнее обновление:** 2026-07-29  
**Тестировано с:** GroupDocs.Conversion 25.2 for Java  
**Автор:** GroupDocs

## Связанные руководства

- [Конвертировать Word в PDF и другие форматы с GroupDocs.Conversion для Java](/conversion/java/)
- [Word в PDF Java — скрыть отслеживаемые изменения и параметры конверсии](/conversion/java/conversion-options/)
- [Как отслеживать прогресс конверсии в Java с GroupDocs — Полное руководство](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)