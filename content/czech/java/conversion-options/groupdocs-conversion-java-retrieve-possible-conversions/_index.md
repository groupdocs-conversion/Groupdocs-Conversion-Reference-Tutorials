---
date: '2026-01-28'
description: Naučte se, jak vypsat formáty a získat všechny možné konverze pomocí
  GroupDocs.Conversion pro Javu, včetně scénářů konverze souborů v cloudovém úložišti.
keywords:
- GroupDocs.Conversion for Java
- retrieve all possible conversions
- Java document conversion
title: 'GroupDocs.Conversion pro Java: Jak vypsat formáty a získat všechny možné konverze'
type: docs
url: /cs/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Komplexní průvodce získáním všech možných konverzí pomocí GroupDocs.Conversion pro Java

Projekty převodu dokumentů často začínají jednoduchou otázkou: **jak vypsat formáty**, které knihovna podporuje, než se rozhodnete, které převádět. V tomto tutoriálu se přesně to dozvíte — jak vypsat formáty a získat každou možnou konverzní cestu nabízenou GroupDocs.Conversion pro Java. Provedeme vás nastavením, spuštěním kódu, reálnými scénáři a tipy na výkon, abyste mohli integraci zjišťování formátů do svých aplikací provést s jistotou.

## Rychlé odpovědi
- **Co znamená “list formats”?** Vrací každý pár zdroj‑cíl konverze, který knihovna dokáže zpracovat.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; placená licence je vyžadována pro produkci.  
- **Může to pomoci při konverzi souborů v cloud storage?** Ano — znalost podporovaných formátů vám umožní automatizovat konverze v cloudových pipelinech.  
- **Jaká verze Javy je vyžadována?** JDK 8 nebo novější.  
- **Je funkce thread‑safe?** Instance `Converter` může být znovu použita napříč vlákny, ale po použití uvolněte prostředky.

## Co je “how to list formats” v GroupDocs.Conversion?
Operace **list formats** dotazuje interní konverzní matici a vrací kolekci popisující každý zdrojový formát a cílové formáty, do kterých může být převeden. Tento přehled je nezbytný pro tvorbu dynamických pracovních postupů zpracování dokumentů.

## Proč používat GroupDocs.Conversion pro Java?
- **Široké pokrytí formátů:** Stovky zdrojových a cílových typů jsou podporovány ihned po instalaci.  
- **Cloud‑ready:** Ideální pro pipeline konverzí souborů v cloud storage, kde potřebujete vědět, které soubory lze převést za běhu.  
- **Optimalizováno pro výkon:** Optimalizováno pro rozsáhlé dávkové operace.

## Předpoklady
- **Java Development Kit (JDK):** Verze 8 nebo novější.  
- **Maven:** Správně nakonfigurovaný ve vašem IDE (IntelliJ IDEA, Eclipse, NetBeans, atd.).  
- **GroupDocs.Conversion pro Java:** Přidán jako Maven závislost (viz níže).

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
Začněte s bezplatnou zkušební verzí pro prozkoumání API. Pro produkční zatížení zakupte licenci nebo požádejte o dočasnou evaluační licenci.

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
Následující sekce ukazují, jak získat kompletní konverzní matici. Ukázky kódu jsou nezměněny oproti originálnímu tutoriálu; pouze přidáváme kontext a vysvětlení.

### Inicializace a získání konverzí

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

## Případy použití konverze souborů v cloud storage
Znalost kompletní konverzní matice je zvláště cenná při tvorbě služeb **cloud storage file conversion**:

1. **Dynamické rozpoznání formátu:** Když soubor přistane v cloud storage, můžete okamžitě zjistit, zda je požadovaný cílový formát podporován.  
2. **Dávková migrace:** Přesuňte velké knihovny dokumentů do jednotného formátu (např. PDF/A) procházením podporovaných zdrojových typů.  
3. **Export řízený uživatelem:** Nabídněte koncovým uživatelům rozbalovací seznam pouze formátů, do kterých může být jejich aktuální dokument exportován, čímž snížíte chyby.

## Úvahy o výkonu
- **Správa zdrojů:** Uvolněte instanci `Converter` nebo použijte try‑with‑resources, pokud vytváříte mnoho krátkodobých konvertorů.  
- **Dávkové zpracování:** Seskupte více souborů do jedné úlohy, abyste snížili režii.  
- **Cache:** Uložte výsledek `getAllPossibleConversions()` do cache, pokud jej často dotazujete; konverzní matice se za běhu zřídka mění.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Oprava |
|---------|-----------------------|--------|
| Žádný výstup se neobjeví | `Converter` není správně inicializován | Ujistěte se, že JAR knihovny je na classpath a licence je načtena. |
| Seznam `TargetConversion` je prázdný | Používáte zastaralou verzi knihovny | Aktualizujte na nejnovější vydání GroupDocs.Conversion. |
| Špičky paměti u velkých dokumentů | Není uvolňováno zdroje konvertoru | Zavolejte `converter.close()` nebo použijte try‑with‑resources. |

## Často kladené otázky

**Q: Co je GroupDocs.Conversion pro Java?**  
A: Výkonná knihovna pro konverzi dokumentů podporující širokou škálu formátů, umožňující bezproblémovou integraci a automatizaci v Java aplikacích.

**Q: Jak začít s GroupDocs.Conversion?**  
A: Začněte nastavením prostředí podle popisu v předpokladech a přidáním knihovny pomocí Maven.

**Q: Mohu pomocí GroupDocs.Conversion převádět vlastní typy souborů?**  
A: Ano, prostřednictvím možností přizpůsobení dostupných v API můžete rozšířit podporu o další formáty souborů.

**Q: Jaké jsou některé běžné problémy při implementaci konverzí?**  
A: Ujistěte se, že všechny závislosti jsou správně nakonfigurovány a ověřte, že vaše Java prostředí splňuje požadavky knihovny.

**Q: Kde mohu získat další pomoc, pokud potřebuji?**  
A: Navštivte fórum GroupDocs nebo si prostudujte jejich rozsáhlou [dokumentaci](https://docs.groupdocs.com/conversion/java/).

---

**Poslední aktualizace:** 2026-01-28  
**Testováno s:** GroupDocs.Conversion 25.2 for Java  
**Autor:** GroupDocs