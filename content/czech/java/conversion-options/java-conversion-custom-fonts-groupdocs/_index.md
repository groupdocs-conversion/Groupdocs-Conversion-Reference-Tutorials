---
date: '2026-01-28'
description: Naučte se, jak převést prezentaci do PDF s vlastní náhradou fontů pomocí
  GroupDocs.Conversion pro Javu. Zachovejte písma a zajistěte konzistentní vzhled
  dokumentu.
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: Jak převést prezentaci do PDF s vlastními fonty pomocí GroupDocs.Conversion
  pro Javu
type: docs
url: /cs/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# Jak převést prezentaci do PDF s vlastními fonty pomocí GroupDocs.Conversion pro Java

V moderních obchodních pracovních postupech často potřebujete **převést prezentaci do pdf**, přičemž zachováte původní vzhled a pocit. Ať už sdílíte prezentaci pro klienta, archivujete výukový materiál nebo automatizujete generování zpráv, chybějící fonty mohou zničit vizuální kvalitu. Tento tutoriál vám přesně ukáže, jak zachovat fonty během konverze Java pptx do pdf pomocí **GroupDocs.Conversion pro Java**.

## Rychlé odpovědi
- **Jaký je hlavní přínos vlastní substituce fontů?** Zaručuje, že PDF vypadá přesně jako zdrojová prezentace, i když originální fonty nejsou nainstalovány na cílovém počítači.  
- **Která knihovna provádí konverzi?** `GroupDocs.Conversion` pro Java.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována komerční licence.  
- **Mohu to použít v Maven projektu?** Ano – stačí přidat úložiště a závislost uvedenou níže.  
- **Je proces thread‑safe?** Instance `Converter` je lehká; můžete vytvořit jednu pro každý konverzní vlákno.

## Co je **convert presentation to pdf**?
Tento výraz jednoduše popisuje akci převodu souboru PowerPoint (.pptx) na PDF dokument. Konverze do PDF umožňuje soubor zobrazit univerzálně, vytisknout a snadněji archivovat, přičemž zachovává rozvržení, obrázky a text.

## Proč použít **custom font substitution**?
- **Konzistence značky:** Zajistěte, aby firemní fonty se zobrazovaly správně i na počítačích, kde nejsou nainstalovány.  
- **Spolehlivost napříč platformami:** PDF se vykreslují stejně na Windows, macOS, Linuxu i mobilních zařízeních.  
- **Snížení počtu podporných tiketů:** Už žádné „mé PDF vypadá divně, protože chybí font.“

## Předpoklady
1. **Java Development Kit (JDK)** – verze 8 nebo vyšší.  
2. **Maven** – pro správu závislostí.  
3. **IDE** – IntelliJ IDEA, Eclipse nebo jakýkoli editor kompatibilní s Javou.  
4. **Základní znalost Javy** – měli byste být obeznámeni s třídami a metodami.  

## Nastavení GroupDocs.Conversion pro Java

Integrovat knihovnu GroupDocs.Conversion do vašeho Maven projektu. Níže uvedený XML úryvek přidává oficiální úložiště a požadovanou závislost.

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
- **Bezplatná zkušební verze:** Stáhněte si trial z webu GroupDocs.  
- **Dočasná licence:** Požádejte o dočasný klíč pro prodloužené testování.  
- **Zakoupení:** Přejděte na plnou licenci, jakmile budete spokojeni.

Po vyřešení závislosti Mavenem můžete začít psát kód pro konverzi.

## Průvodce implementací

### Krok 1: Definujte možnosti načtení prezentace s substitucí fontů
Následující metoda vytváří objekt `PresentationLoadOptions` a říká GroupDocs, jak nahradit chybějící fonty. Toto je jádro **jak zachovat fonty** během konverze.

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

**Vysvětlení**  
- **Substituce fontů:** Mapuje „Tahoma“ a „Times New Roman“ na „Arial“.  
- **Výchozí font:** Poskytuje záložní (`Helvetica.ttf`) pokud žádná mapa neodpovídá.  

### Krok 2: Převést dokument prezentace do PDF s pokročilými možnostmi
Nyní použijeme možnosti načtení z Kroku 1 k provedení operace **convert presentation to pdf**.

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

**Vysvětlení**  
- **Inicializace Converteru:** Předává cestu k PPTX spolu s vlastním `loadOptions`.  
- **Možnosti konverze PDF:** Můžete dále upravit nastavení (např. kvalitu obrázku), pokud je potřeba.  

## Praktické aplikace
1. **Obchodní prezentace:** Zachovat firemní branding při sdílení PDF s externími partnery.  
2. **Vzdělávací materiály:** Převést přednáškové sady do PDF pro offline studium bez obav o chybějící fonty.  
3. **Právní dokumenty:** Zachovat přesné rozvržení důkazních snímků pro soudní podání.  

## Úvahy o výkonu
- **Správa paměti:** Přidělte dostatečný heap pro velké prezentace (`-Xmx2g` je dobrý výchozí bod).  
- **Omezte substituce fontů:** Mapujte jen fonty, které skutečně potřebujete; nadměrné mapování může zpomalit zpracování.  
- **Garbage Collection:** Zavolejte `System.gc()` po velkých dávkových konverzích, pokud zaznamenáte špičky v paměti.  

## Časté problémy a řešení

| Problém | Řešení |
|-------|----------|
| **Chybějící výchozí soubor fontu** | Ověřte, že cesta v `setDefaultFont` ukazuje na platný soubor `.ttf` a že je soubor čitelný. |
| **Konverze se zasekne u velkého PPTX** | Zvyšte velikost JVM heap a zvažte konverzi snímků po dávkách. |
| **Font nebyl nahrazen podle očekávání** | Ujistěte se, že název zdrojového fontu přesně (rozlišuje velká a malá písmena) odpovídá názvu použitému v `FontSubstitute.create`. |
| **Výstupní PDF je prázdný** | Potvrďte, že zdrojový PPTX není poškozený a že `Converter` ukazuje na správnou cestu k souboru. |

## Často kladené otázky

**Q: Jaký je hlavní přínos používání vlastních substitucí fontů při konverzích?**  
A: Vlastní substituce fontů zaručuje, že PDF zachová zamýšlený vzhled, i když originální fonty nejsou na cílovém systému dostupné.

**Q: Jak mohu během konverze zacházet s nepodporovanými fonty?**  
A: Použijte funkci `FontSubstitute` k mapování nedostupných fontů na alternativy, čímž zajistíte konzistentní estetiku dokumentu.

**Q: Mohu použít GroupDocs.Conversion s řešeními cloudového úložiště?**  
A: Ano, GroupDocs nabízí integrace, které umožňují konverze přímo z cloudových úložišť jako AWS S3 a Azure Blob Storage.

**Q: Co mám dělat, pokud je můj konverzní proces pomalý?**  
A: Optimalizujte systémové zdroje, omezte mapování substitucí fontů a zvyšte velikost JVM heap pro zlepšení výkonu.

**Q: Je tento tutoriál součástí větší série **document conversion tutorial java**?**  
A: Rozhodně — tento průvodce se zaměřuje na vlastní fonty, ale série také pokrývá extrakci obrázků, vodoznaky a dávkové zpracování pomocí GroupDocs.Conversion pro Java.

## Závěr
Nyní máte kompletní, připravený přístup pro **convert presentation to pdf** při zachování fontů pomocí **GroupDocs.Conversion pro Java**. Definováním možností načtení s náhradními fonty a využitím výkonného API `Converter` můžete garantovat vizuální věrnost na jakékoli platformě.

**Další kroky**  
- Experimentujte s dalšími `PdfConvertOptions` (např. nastavení souladu PDF/A).  
- Integrovat logiku konverze do REST služby pro generování PDF na vyžádání.  
- Prozkoumat další moduly GroupDocs, jako je `GroupDocs.Annotation`, pro přidávání komentářů k vygenerovaným PDF.

---

**Poslední aktualizace:** 2026-01-28  
**Testováno s:** GroupDocs.Conversion 25.2 pro Java  
**Autor:** GroupDocs