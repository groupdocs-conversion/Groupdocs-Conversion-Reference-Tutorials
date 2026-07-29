---
date: '2026-07-29'
description: Zjistěte, jak vypsat formáty a získat všechny možné konverze pomocí GroupDocs.Conversion
  for Java, ideální pro workflow konverze souborů v cloud storage.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Naučte se, jak vypsat formáty a získat všechny možné konverze pomocí
  GroupDocs.Conversion for Java. Ideální pro pipeline konverze souborů v cloud storage.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Jak vypsat formáty pomocí GroupDocs.Conversion for Java
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
title: Jak vypsat formáty pomocí GroupDocs.Conversion for Java
type: docs
url: /cs/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Jak vypsat formáty a získat všechny možné konverze pomocí GroupDocs.Conversion pro Java

V mnoha projektech zpracování dokumentů je prvním krokem vědět **jak vypsat formáty**, které konverzní engine podporuje. Tento tutoriál vám krok za krokem ukáže, jak dotazovat GroupDocs.Conversion pro Java, získat každý pár zdroj‑cíl a tuto znalost využít v pipeline konverzí souborů v cloudovém úložišti. Na konci budete mít znovupoužitelnou metodu, která vrací úplnou konverzní matici, plus praktické tipy pro výkon a zpracování chyb.

## Rychlé odpovědi
- **Co znamená „list formats“?** Vrací každý pár konverze ze zdroje do cíle, který knihovna dokáže zpracovat.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; placená licence je vyžadována pro produkci.  
- **Může to pomoci při konverzi souborů v cloudovém úložišti?** Ano — znalost podporovaných formátů vám umožní automatizovat konverze v cloudových pipelinech.  
- **Jaká verze Javy je požadována?** JDK 8 nebo novější.  
- **Je funkce thread‑safe?** Instance `Converter` může být znovu použita napříč vlákny, ale po použití uvolněte prostředky.

## Co je „how to list formats“ v GroupDocs.Conversion?
Operace **list formats** vrací kolekci, která popisuje každý vstupní formát spolu s cílovými formáty, do kterých může být převeden. Tato matice je generována z interních konverzních pravidel knihovny a je nezbytná pro tvorbu dynamických workflow, které se přizpůsobují skutečným schopnostem GroupDocs.Conversion za běhu.

## Proč používat GroupDocs.Conversion pro Java?
GroupDocs.Conversion pro Java podporuje **více než 200 vstupních formátů** a **více než 200 výstupních formátů**, zahrnujících vše od DOCX a PPTX po PDF/A a typy obrázků. Běží kompletně na serveru, takže nejsou vyžadovány produkty Microsoft Office ani Adobe. API je thread‑safe, dokáže zpracovat dokumenty s několika stovkami stránek bez načítání celého souboru do paměti a integruje se hladce s cloudovými úložišti jako AWS S3, Azure Blob a Google Cloud Storage.

## Požadavky
- **Java Development Kit (JDK):** Verze 8 nebo novější.  
- **Maven:** Správně nakonfigurovaný ve vašem IDE (IntelliJ IDEA, Eclipse, NetBeans atd.).  
- **GroupDocs.Conversion pro Java:** Přidáno jako Maven závislost (viz níže).  

## Nastavení GroupDocs.Conversion pro Java

Přidejte repozitář GroupDocs a závislost do vašeho `pom.xml`:

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
Začněte s bezplatnou zkušební verzí a prozkoumejte API. Pro produkční zatížení zakupte licenci nebo požádejte o dočasnou evaluační licenci.

### Základní inicializace a nastavení

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

## Jak vypsat formáty pomocí GroupDocs.Conversion pro Java
`Converter` je hlavní třída, která provádí konverze a poskytuje informace o formátech. `getAllPossibleConversions()` vrací seznam všech podporovaných párů zdroj‑cíl. `ConversionInfo` představuje jediné mapování konverze mezi zdrojovým a cílovým formátem.  

Načtěte engine `Converter`, zavolejte `getAllPossibleConversions()` a získáte seznam objektů `ConversionInfo`, které popisují každý povolený pár zdroj‑cíl. Tento jediný volání stačí k vytvoření rozbalovacího seznamu exportních možností, validaci příchozích souborů nebo návrhu skriptů pro hromadnou migraci.

### Inicializace a získání konverzí

Třída `Converter` je jádro, které poskytuje konverzní schopnosti a vystavuje metodu `getAllPossibleConversions()`.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Procházení možných konverzí

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Určení typů konverzí

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Kompletní funkce

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

## Případy použití konverze souborů v cloudovém úložišti
Znalost úplné konverzní matice je zvláště cenná při budování **služeb konverze souborů v cloudovém úložišti**:

1. **Dynamická detekce formátu:** Když soubor dorazí do cloudového úložiště, můžete okamžitě zjistit, zda je požadovaný cílový formát podporován.  
2. **Hromadná migrace:** Přesuňte velké knihovny dokumentů do jednotného formátu (např. PDF/A) tím, že projdete podporované typy zdrojů.  
3. **Export řízený uživatelem:** Nabídněte koncovým uživatelům rozbalovací seznam pouze těch formátů, do kterých může být jejich aktuální dokument exportován, čímž snížíte chyby a zlepšíte UX.

## Úvahy o výkonu
- **Správa prostředků:** Uvolněte instanci `Converter` nebo použijte try‑with‑resources, pokud vytváříte mnoho krátkodobých konvertorů.  
- **Hromadné zpracování:** Skupinujte více souborů do jedné úlohy, abyste snížili režii.  
- **Cache:** Uložte výsledek `getAllPossibleConversions()` do cache, pokud jej často dotazujete; konverzní matice se za běhu zřídka mění.  

## Časté problémy a řešení
| Projev | Předpokládaná příčina | Řešení |
|---------|--------------|-----|
| Žádný výstup se neobjeví | `Converter` není správně inicializován | Ujistěte se, že je JAR knihovny na classpath a licence je načtena. |
| Seznam `TargetConversion` je prázdný | Používáte zastaralou verzi knihovny | Aktualizujte na nejnovější vydání GroupDocs.Conversion. |
| Špičky paměti u velkých dokumentů | Nepoužíváte uvolnění prostředků konvertoru | Zavolejte `converter.close()` nebo použijte try‑with‑resources. |

## Často kladené otázky

**Q: Co je GroupDocs.Conversion pro Java?**  
A: Jedná se o server‑side knihovnu, která podporuje více než 200 vstupních i výstupních formátů, umožňuje rychlou konverzi dokumentů bez licence a bez externího softwaru.

**Q: Jak začít s GroupDocs.Conversion?**  
A: Nastavte svůj Maven projekt, přidejte závislost uvedenou výše, načtěte licenční soubor a vytvořte instanci třídy `Converter`, jak je ukázáno v sekci inicializace.

**Q: Mohu pomocí GroupDocs.Conversion převádět vlastní typy souborů?**  
A: Ano — prostřednictvím rozšiřovacích bodů API můžete registrovat vlastní konvertory nebo připojit třetí strany pro proprietární formáty.

**Q: Jaké jsou běžné úskalí při implementaci konverzí?**  
A: Zapomenutí uzavřít `Converter`, používání staré verze JAR nebo přehlížení spotřeby paměti u velmi velkých PDF. Dodržujte výše uvedené tipy pro správu prostředků.

**Q: Kde mohu získat další pomoc?**  
A: Navštivte oficiální [dokumentaci](https://docs.groupdocs.com/conversion/java/) nebo položte otázky ve fóru komunity GroupDocs.

---

**Poslední aktualizace:** 2026-07-29  
**Testováno s:** GroupDocs.Conversion 25.2 for Java  
**Autor:** GroupDocs

## Související tutoriály

- [Převod Wordu do PDF a dalších formátů souborů pomocí GroupDocs.Conversion pro Java](/conversion/java/)
- [Word do PDF Java – Skrytí sledovaných změn a možnosti konverze](/conversion/java/conversion-options/)
- [Jak sledovat průběh konverze v Java s GroupDocs – Kompletní průvodce](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)