---
date: '2026-09-25'
description: Naučte se, jak převést eml na pdf java pomocí GroupDocs.Conversion, aplikací
  posunu časového pásma pro zachování správných časových razítek. Podrobný návod krok
  za krokem pro vývojáře Java.
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: Naučte se, jak převést eml na pdf java pomocí GroupDocs.Conversion,
  aplikací posunu časového pásma pro zachování správných časových razítek. Podrobný
  Java návod pro vývojáře.
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: Převod eml na pdf java s posunem časového pásma pomocí GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  headline: How to convert eml to pdf java with timezone offset
  type: TechArticle
- description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  name: How to convert eml to pdf java with timezone offset
  steps:
  - name: '**Libraries & dependencies**'
    text: '**Libraries & dependencies**'
  - name: '**Environment**'
    text: '**Environment**'
  - name: '**Knowledge**'
    text: '**Knowledge**'
  type: HowTo
- questions:
  - answer: It’s a powerful library that enables document conversion across dozens
      of formats, including email to PDF, with built‑in timezone handling.
    question: What is GroupDocs.Conversion for Java?
  - answer: Use `EmailLoadOptions.setTimeZoneOffset(milliseconds)` before initializing
      the `Converter`.
    question: How do I set the timezone offset for emails?
  - answer: Yes, the library supports `.eml`, `.msg`, and other common email file
      types.
    question: Can I convert multiple email formats with this setup?
  - answer: Missing dependencies, incorrect file paths, and providing the offset in
      the wrong unit (seconds vs. milliseconds).
    question: What are common pitfalls during conversion?
  - answer: Visit the [official documentation](https://docs.groupdocs.com/conversion/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Conversion?
  type: FAQPage
tags:
- convert eml
- GroupDocs.Conversion
- Java email conversion
- timezone offset
- PDF generation
title: Jak převést eml na pdf java s posunem časového pásma
type: docs
url: /cs/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# Jak převést eml na pdf java s posunem časového pásma

V tomto tutoriálu se dozvíte, jak **convert eml to pdf java** správně upravit časové razítko pro jakýkoli rozdíl časových pásem. Pomocí GroupDocs.Conversion for Java uvidíte kompletní end‑to‑end workflow — od nastavení Maven, přes načtení e‑mailu s vlastním posunem, až po streamování výsledných PDF souborů. Kroky jsou napsány pro vývojáře Java 8+, kteří potřebují spolehlivé, archivně připravené PDF, které zobrazují správný místní čas.

## Rychlé odpovědi
- **Která knihovna provádí konverzi?** GroupDocs.Conversion for Java.  
- **Která primární metoda nastavuje časové pásmo?** `EmailLoadOptions.setTimeZoneOffset`.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; plná licence je vyžadována pro produkci.  
- **Mohu dávkově zpracovávat mnoho e‑mailů?** Ano—zabalte smyčku konverze do dávkové rutiny.  
- **Jaká verze Javy je požadována?** JDK 8 nebo novější.  

## Co je convert eml to pdf java?
Fráze “convert eml to pdf java” popisuje proces převzetí souboru e‑mailu (obvykle `.eml` nebo `.msg`) a vytvoření PDF dokumentu pomocí Java kódu. Tato konverze je nezbytná pro archivaci, právní soulad a sdílení napříč platformami, protože PDF zachovává rozvržení a je univerzálně zobrazitelné.

## Proč používat GroupDocs.Conversion for Java?
GroupDocs.Conversion podporuje **70+** vstupních a výstupních formátů, včetně `.eml`, `.msg`, `.pdf`, `.docx` a typů obrázků. Jeho vestavěná třída `EmailLoadOptions` vám umožní zadat posun časového pásma v milisekundách, což zaručuje, že časová razítka PDF odpovídají zamýšlenému místnímu času. Knihovna zpracovává soubory ve streamovacím režimu, což snižuje využití paměti až o **80 %** ve srovnání s načítáním celého dokumentu do RAM.

## Předpoklady
1. **Knihovny a závislosti**  
   - GroupDocs.Conversion for Java verze **25.2** nebo novější.  

2. **Prostředí**  
   - JDK 8+ nainstalováno a nakonfigurováno na vašem počítači.  
   - Maven jako nástroj pro automatizaci sestavení.  

3. **Znalosti**  
   - Základní programování v Javě, zejména souborový I/O.  
   - Znalost struktury `pom.xml` v Maven.

## Nastavení GroupDocs.Conversion pro Java

### Informace o instalaci
Add the GroupDocs repository and the conversion dependency to your `pom.xml`:

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

### Získání licence
You can start with a free trial or request a temporary license for full functionality testing:

- **Free trial** – Stáhněte knihovnu a prozkoumejte základní funkce.  
- **Temporary license** – Požádejte o dočasnou licenci [stránka dočasné licence](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase** – Pro dlouhodobé používání zvažte zakoupení licence na [oficiální stránce](https://purchase.groupdocs.com/buy).

### Základní inicializace
Below is the minimal code you need to create a `Converter` instance and load an email with a timezone offset:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## Jak nastavit posun časového pásma?
`EmailLoadOptions` je konfigurační třída, která řídí, jak jsou e‑mailové soubory načítány pro konverzi. Načtěte svůj e‑mail s vlastním posunem před konverzí. Metoda `setTimeZoneOffset` přijímá posun v **milisekundách**, takže posun +2 hodiny odpovídá `7200000`. Toto nastavení přepíše zobrazené časové razítko v generovaném PDF. Poskytnutím posunu knihovna přepočítá zobrazené časy odeslání a přijetí, čímž zajistí, že generované PDF odráží místní časové pásmo příjemce. To je zvláště užitečné pro mezinárodní týmy, které přezkoumávají archivovanou korespondenci.

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## Jak inicializovat objekt Converter?
`Converter` je hlavní třída, která provádí konverzi dokumentů pomocí poskytnutých možností načtení. Vytvořte `Converter` předáním cesty ke zdrojovému souboru a lambda výrazu, který poskytuje dříve definované `loadOptions`. Tím se propojí nastavení časového pásma s procesem konverze. Načte zdrojový e‑mail, aplikuje nastavení `EmailLoadOptions` — včetně posunu časového pásma — a připraví výstupní stream pro generování PDF. Použití lambda výrazu zajišťuje, že možnosti jsou vyhodnoceny v čase konverze, což je užitečné při zpracování více souborů s různými nastaveními.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## Jak spustit konverzi a streamovat PDF stránky?
`PdfConvertOptions` určuje nastavení výstupu PDF, jako je velikost stránky, komprese a kvalita obrazu. Zavolejte metodu `convert` a poskytněte instanci `PdfConvertOptions` a výstupní stream pro každou stránku. Blok `try‑finally` zaručuje, že všechny streamy jsou uzavřeny, čímž se předchází únikům zdrojů. Po nastavení možností metoda `convert` iteruje přes každou stránku e‑mailu a zapisuje PDF data do samostatných výstupních streamů. Tento přístup vám umožní efektivně zpracovávat velké e‑maily, protože každá stránka je zpracována a vyprázdněna samostatně, což minimalizuje spotřebu paměti.

```java
try {
    converter.convert((SaveDocumentStreamForFileType) t -> {
        try {
            OutputStream outputStream = Files.newOutputStream(Paths.get(String.format(outputPattern, streamPool.size())));
            streamPool.add(outputStream);
            return outputStream;
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }, options);
} finally {
    for (OutputStream outputStream : streamPool) {
        if (outputStream != null) {
            outputStream.close();
        }
    }
}
```

## Praktické aplikace
- **Archiving emails** – Ukládejte PDF s přesnými časovými razítky pro právní nebo auditní účely.  
- **Cross‑timezone collaboration** – Týmy po celém světě vidí ve konvertovaných dokumentech stejný místní čas.  
- **Email reporting** – Generujte PDF zprávy, které zachovávají původní časy odeslání/přijetí pro soulad s předpisy.

Tento workflow můžete vložit do CRM systémů, platforem pro správu dokumentů nebo automatizovaných dávkových úloh, abyste zefektivnili svůj dokumentový kanál.

## Úvahy o výkonu
- **Resource management** – Uzavřete streamy okamžitě (jak je ukázáno), aby se uvolnila paměť.  
- **Batch processing** – Procházejte kolekci souborů `.eml` a pokud možno znovu použijte jedinou instanci `Converter`.  
- **JVM tuning** – Upravte velikost haldy (`-Xmx`) pro velké dávky, aby se předešlo `OutOfMemoryError`.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| `NullPointerException` at `loadOptions` | Možnosti načtení nebyly předány správně | Zajistěte, aby při vytváření `Converter` byla použita lambda `() -> loadOptions`. |
| PDF output is blank | Cesta k vstupnímu souboru je nesprávná nebo soubor chybí | Ověřte, že `sourceFilePath` ukazuje na existující soubor `.eml`. |
| Timezone not reflected | Špatná hodnota posunu (např. sekundy místo milisekund) | Poskytněte posun v **milisekundách** (např. `7200000` pro +2 h). |

## Často kladené otázky
**Q: Co je GroupDocs.Conversion for Java?**  
A: Jedná se o výkonnou knihovnu, která umožňuje konverzi dokumentů mezi desítkami formátů, včetně e‑mailu do PDF, s vestavěnou podporou časových pásem.

**Q: Jak nastavit posun časového pásma pro e‑maily?**  
A: Použijte `EmailLoadOptions.setTimeZoneOffset(milliseconds)` před inicializací `Converter`.

**Q: Mohu pomocí tohoto nastavení převádět více formátů e‑mailů?**  
A: Ano, knihovna podporuje `.eml`, `.msg` a další běžné typy e‑mailových souborů.

**Q: Jaké jsou běžné úskalí při konverzi?**  
A: Chybějící závislosti, nesprávné cesty k souborům a zadání posunu ve špatné jednotce (sekundy místo milisekund).

**Q: Kde mohu najít více zdrojů o GroupDocs.Conversion?**  
A: Navštivte [oficiální dokumentaci](https://docs.groupdocs.com/conversion/java/) pro podrobné návody a reference API.

## Další zdroje
- **Dokumentace**: Prozkoumejte dále na [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)  
- **Reference API**: Podrobná reference API je k dispozici na [API reference](https://reference.groupdocs.com/conversion/java/)  
- **Stáhnout GroupDocs.Conversion**: Začněte s knihovnou na [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/)  
- **Nákup**: Pro dlouhodobé používání zakupte licenci na [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)  
- **Bezplatná zkušební verze a licence**: Vyzkoušejte zdarma nebo požádejte o dočasnou licenci na [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) a [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Podpora**: Pro pomoc navštivte [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)

Využijte sílu GroupDocs.Conversion ve svých Java aplikacích a užijte si přesné, časově‑pásmově‑vědomé PDF konverze ještě dnes!

---

**Poslední aktualizace:** 2026-09-25  
**Testováno s:** GroupDocs.Conversion 25.2  
**Autor:** GroupDocs

## Související tutoriály

- [msg to pdf java – Konverze formátů e‑mailů s GroupDocs](/conversion/java/email-formats/)
- [eml to pdf java – Převod e‑mailu na PDF s GroupDocs](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [Převod více typů souborů pomocí GroupDocs.Conversion Java – Kompletní průvodce](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)