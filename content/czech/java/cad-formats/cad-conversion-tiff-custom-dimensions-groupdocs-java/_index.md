---
date: '2026-07-24'
description: 'Jednoduchá konverze obrázků v Javě: naučte se, jak převést soubory CAD
  na TIFF s vlastními rozměry pomocí GroupDocs Conversion Java. Podrobný návod krok
  za krokem pro vývojáře.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Jednoduchá konverze obrázků v Javě. Převádějte soubory CAD na vysoce
  kvalitní TIFF obrázky s vlastní šířkou a výškou pomocí GroupDocs Conversion Java.
  Sledujte náš podrobný návod.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Java konverze obrázků: CAD na TIFF s vlastními rozměry'
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
title: 'Java konverze obrázků: CAD na TIFF s vlastními rozměry'
type: docs
url: /cs/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java konverze obrázků: CAD na TIFF s vlastními rozměry

Pokud potřebujete převést CAD výkresy na vysoce rozlišené TIFF obrázky a zároveň kontrolovat přesnou šířku a výšku v pixelech, **java image conversion** je klíč. Pomocí GroupDocs Conversion Java můžete rasterizovat libovolný podporovaný CAD formát (DWG, DGN, DXF atd.) do TIFF souboru, který se perfektně vejde do zpráv, webových portálů nebo tiskových rozvržení. Tento průvodce vás provede každým krokem – od nastavení projektu po finální konverzi – abyste mohli proces integrovat do jakéhokoli Java‑založeného pracovního postupu.

## Rychlé odpovědi
- **Jakou knihovnu bych měl použít pro Java image conversion?** GroupDocs Conversion Java, robustní knihovna pro Java image conversion.  
- **Jak nastavit vlastní rozměry pro CAD soubor?** Použijte `CadLoadOptions` a specifikujte `setWidth()` a `setHeight()`.  
- **Mohu převést DWG na TIFF v jednom kroku?** Ano—načtěte CAD, nastavte rozměry a poté konvertujte pomocí `ImageConvertOptions`.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro hodnocení; plná licence odemkne všechny funkce.  
- **Jaká verze Javy je vyžadována?** Jakýkoli runtime Java 8+ je podporován.

## Co je GroupDocs Conversion Java?
`GroupDocs Conversion Java` knihovna je řešení **java image conversion**, které podporuje více než 110 vstupních a výstupních formátů, včetně všech hlavních CAD a rastrových typů obrázků.  
Třída `Converter` je hlavní komponenta, která spouští operace konverze souborů.  
Poskytuje server‑side renderování, škálování a formát‑specifické možnosti, což vývojářům umožňuje konvertovat soubory bez instalace třetích stran prohlížečů.

## Proč převádět CAD na TIFF s vlastními rozměry?
Nastavení explicitní šířky a výšky zaručuje, že výsledný TIFF přesně odpovídá rozložení požadavkům downstream systémů. Definováním pixelových rozměrů před rasterizací se vyhnete artefaktům škálování, udržíte konzistenci tloušťky čar a zajistíte, že obrázek se bez problémů integruje do PDF, webových stránek nebo tištěného materiálu bez dalšího zpracování. Tento přístup také zjednodušuje automatizované pipeline, kde každý obrázek musí odpovídat předdefinované specifikaci velikosti.  

- **Zachovává vizuální věrnost:** Rasterizace při 1920 × 1080 px (nebo jakékoli jiné velikosti) zachovává čáry a šrafování ostré.  
- **Zajišťuje konzistentní rozvržení:** Obrázky se čistě vkládají do PDF, HTML stránek nebo tiskových šablon bez dalšího změny velikosti.  
- **Zvyšuje kompatibilitu:** TIFF je univerzálně akceptován na Windows, macOS, Linuxu a ve většině designových nástrojů, což snižuje problémy s konverzí formátů.

## Požadavky
Před začátkem se ujistěte, že máte:

1. **GroupDocs Conversion Java** verze 25.2 nebo novější (doporučuje se nejnovější verze).  
2. Java IDE, například IntelliJ IDEA nebo Eclipse.  
3. Maven nainstalovaný pro správu závislostí.  
4. Základní znalost programování v Javě a znalost `pom.xml` souboru Maven.  

## Nastavení GroupDocs Conversion Java

Přidejte Maven závislost GroupDocs do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Získání licence:** Můžete získat bezplatnou zkušební verzi, požádat o dočasnou licenci pro plnou funkčnost nebo zakoupit trvalou licenci, která plně odemkne funkce GroupDocs Conversion.

Jakmile je váš Java projekt správně propojen s těmito závislostmi, jste připraveni začít převádět CAD soubory!

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

## Jak převést CAD na TIFF s vlastními rozměry?

Převod CAD souborů na TIFF s přesnými rozměry zahrnuje načtení zdrojového výkresu, konfiguraci možností renderování a volání konverzního API. Dodržením lineární posloupnosti – nastavením šířky a výšky, výběrem TIFF jako výstupního formátu a provedením konverze – zajistíte, že vytvořený obrázek odpovídá přesným požadavkům na velikost vašich downstream aplikací, přičemž zachová detail a kvalitu původního výkresu.  

1. **Importujte požadované třídy** (viz krok po kroku níže).  
2. **Vytvořte instanci `CadLoadOptions`** a nastavte `width` a `height` na požadované rozměry.  
3. **Instanciujte `ImageConvertOptions`**, s určením `ImageFileType.Tiff`.  
4. **Zavolejte metodu `convert`** na objektu `Converter`, předáním cesty ke zdroji, možností načtení a konverzních možností.

### Načítání CAD dokumentů s vlastními rozměry (Jak nastavit rozměry)

Třída `CadLoadOptions` říká GroupDocs, jak rasterizovat výkres před konverzí.

`CadLoadOptions` je konfigurační objekt, který definuje parametry renderování jako šířka, výška a DPI pro CAD soubory.

#### Krok 1: Importujte potřebné knihovny
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Krok 2: Nastavte možnosti načtení s vlastními rozměry
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Vysvětlení:* Konfigurací `CadLoadOptions` říkáte **GroupDocs Conversion Java**, aby rasterizoval CAD výkres na 1920 × 1080 pixelů před jakýmkoli dalším zpracováním.

### Převod CAD na TIFF obrázek (Convert CAD to TIFF)

`ImageConvertOptions` řídí knihovnu, aby vytvořila TIFF soubor s nastaveními, které určíte.

`ImageConvertOptions` zapouzdřuje všechny specifické parametry konverze obrázku, včetně výstupního formátu, rozlišení a úrovně komprese.

#### Krok 3: Nakonfigurujte možnosti konverze
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Krok 4: Proveďte konverzi
```java
converter.convert(convertedFilePath, options);
```
*Vysvětlení:* Nastavením `ImageFileType.Tiff` řídíte **GroupDocs Conversion Java**, aby výstupem byl vysoce kvalitní TIFF soubor, který respektuje šířku a výšku definovanou dříve.

## Tipy pro řešení problémů a běžné úskalí
- **Problémy s cestou k souboru:** Ověřte, že cesty ke zdroji i cíli jsou správné a že aplikace má oprávnění pro čtení/zápis.  
- **Nepodporované formáty:** Ujistěte se, že CAD soubor je jedním z podporovaných formátů (DWG, DGN, DXF atd.).  
- **Paměťová omezení:** Velké výkresy mohou vyžadovat zvýšení velikosti haldy JVM (`-Xmx2g` nebo vyšší).  
- **Obavy o kvalitu:** Upravte nastavení rozlišení v `ImageConvertOptions`, pokud výchozí DPI nesplňuje vaše standardy kvality.  

## Praktické aplikace
1. **Architektonická vizualizace:** Exportujte půdorysy jako TIFF pro vysoce rozlišené prezentace.  
2. **Inženýrská dokumentace:** Vytvářejte standardizované obrázky pro zařazení do technických příruček.  
3. **Automatizované reportování:** Vkládejte TIFF obrázky odvozené z CAD do PDF nebo HTML reportů pomocí CI pipeline.  

## Úvahy o výkonu
- **Optimalizujte využití paměti:** Uvolněte instanci `Converter` po konverzi (`converter.close()` pokud je použitelné).  
- **Dávkové zpracování:** Procházejte seznam CAD souborů a znovu použijte jedinou konfiguraci `Converter` ke snížení režie.  
- **Zůstaňte aktuální:** Pravidelně aktualizujte na nejnovější verzi GroupDocs Conversion Java, abyste získali výhody vylepšení výkonu a oprav chyb.  

## Často kladené otázky

**Q:** Jaké souborové formáty GroupDocs Conversion podporuje?  
**A:** Podporuje více než 110 formátů, včetně CAD souborů jako DWG, DGN, DXF, stejně jako běžné typy obrázků, dokumentů a archivů.

**Q:** Mohu převést více CAD souborů najednou?  
**A:** Ano—implementujte jednoduchý cyklus, který vytvoří nový `Converter` pro každý soubor nebo znovu použije stejnou instanci s různými cestami ke zdrojům.

**Q:** Jak zacházet s velkými soubory během konverze?  
**A:** Zvyšte velikost haldy JVM, zpracovávejte soubory v menších dávkách nebo použijte streamovací možnosti poskytované knihovnou.

**Q:** Co když kvalita výstupního obrázku není uspokojivá?  
**A:** Upravte DPI nebo nastavení škálování v `ImageConvertOptions` pro zvýšení rozlišení.

**Q:** Je k dispozici podpora, pokud narazím na problémy?  
**A:** GroupDocs nabízí rozsáhlou dokumentaci, komunitní fóra a přímou podporu pro licencované zákazníky.

## Zdroje
- [GroupDocs dokumentace](https://docs.groupdocs.com/conversion/java/)
- [API reference](https://reference.groupdocs.com/conversion/java/)
- [Stáhnout nejnovější verzi](https://releases.groupdocs.com/conversion/java/)
- [Koupit licence](https://purchase.groupdocs.com/buy)
- [Přístup k bezplatné zkušební verzi](https://releases.groupdocs.com/conversion/java/)
- [Požadavek na dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)
- [Fórum podpory](https://forum.groupdocs.com/c/conversion/10)

---

**Poslední aktualizace:** 2026-07-24  
**Testováno s:** GroupDocs Conversion Java 25.2  
**Autor:** GroupDocs  

---

## Související tutoriály

- [převod cad pdf java – Tutoriály pro konverzi CAD formátů pro GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [převod pdf na jpg java pomocí GroupDocs.Conversion – Průvodce](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Jak nastavit licenci pro GroupDocs.Conversion Java – krok za krokem průvodce](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)