---
date: '2026-07-24'
description: 'A Java képkonvertálás egyszerű: ismerje meg, hogyan konvertálhat CAD
  fájlokat TIFF-re egyedi méretekkel a GroupDocs Conversion Java segítségével. Lépésről‑lépésre
  útmutató fejlesztőknek.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: A Java képkonvertálás egyszerű. Konvertáljon CAD fájlokat magas minőségű
  TIFF képekké egyedi szélességgel és magassággal a GroupDocs Conversion Java segítségével.
  Kövesse részletes útmutatónkat.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Java képkonvertálás: CAD-t TIFF-re egyedi méretekkel'
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
title: 'Java képkonvertálás: CAD-t TIFF-re egyedi méretekkel'
type: docs
url: /hu/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java képkonvertálás: CAD TIFF-re egyedi méretekkel

Ha CAD rajzokat kell magas felbontású TIFF képekké alakítania, miközben a pontos pixel szélességet és magasságot szabályozza, a **java image conversion** a kulcs. A GroupDocs Conversion Java segítségével rasterizálhat bármely támogatott CAD formátumot (DWG, DGN, DXF stb.) egy olyan TIFF fájlba, amely tökéletesen illeszkedik jelentésekbe, webportálokba vagy nyomtatási elrendezésekbe. Ez az útmutató minden lépésen végigvezet – a projekt beállításától a végső konvertálásig –, hogy a folyamatot bármely Java‑alapú munkafolyamatba integrálhassa.

## Gyors válaszok
- **Melyik könyvtárat kell használnom Java képkonvertáláshoz?** GroupDocs Conversion Java, egy robusztus Java képkonvertálási könyvtár.  
- **Hogyan állíthatom be az egyedi méreteket egy CAD fájlhoz?** Használja a `CadLoadOptions`-t, és adja meg a `setWidth()` és `setHeight()` metódusokat.  
- **Átalakíthatom a DWG-t TIFF-re egy lépésben?** Igen—töltse be a CAD-et, állítsa be a méreteket, majd konvertáljon az `ImageConvertOptions` segítségével.  
- **Szükségem van licencre?** Az ingyenes próbaalkalmazás értékelésre használható; egy teljes licenc feloldja az összes funkciót.  
- **Melyik Java verzió szükséges?** Bármely Java 8+ futtatókörnyezet támogatott.

## Mi az a GroupDocs Conversion Java?
A `GroupDocs Conversion Java` könyvtár egy **java image conversion** megoldás, amely több mint 110 bemeneti és kimeneti formátumot támogat, beleértve az összes fő CAD és raszteres kép típust.  
A `Converter` osztály a központi komponens, amely elindítja a fájlkonvertálási műveleteket.  
Szerver‑oldali renderelést, méretezést és formátum‑specifikus beállításokat biztosít, lehetővé téve a fejlesztők számára, hogy fájlokat konvertáljanak anélkül, hogy harmadik fél nézőprogramjait telepítenék.

## Miért konvertáljuk a CAD-et TIFF-re egyedi méretekkel?
Az explicit szélesség és magasság beállítása garantálja, hogy a kapott TIFF pontosan megfeleljen a downstream rendszerek elrendezési követelményeinek. A pixelméretek rasterizálás előtti meghatározásával elkerülhetők a downstream skálázási hibák, megőrizhető a vonalvastagság egységessége, és biztosítható, hogy a kép zökkenőmentesen integrálódjon PDF-ekbe, weboldalakba vagy nyomtatott anyagokba további feldolgozás nélkül. Ez a megközelítés egyszerűsíti az automatizált csővezetékeket is, ahol minden képet előre meghatározott méret specifikációnak kell megfelelnie.  

- **Megőrzi a vizuális hűséget:** A 1920 × 1080 px (vagy bármilyen általad választott méret) rasterizálása éles vonalakat és kitöltéseket biztosít.  
- **Biztosítja az egységes elrendezéseket:** A képek tisztán beágyazódnak PDF-ekbe, HTML oldalakba vagy nyomtatási sablonokba további átméretezés nélkül.  
- **Növeli a kompatibilitást:** A TIFF univerzálisan elfogadott Windows, macOS, Linux és a legtöbb tervezőeszköz között, csökkentve a formátum‑konvertálási fejfájást.

## Előfeltételek
Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

1. **GroupDocs Conversion Java** verzió 25.2 vagy újabb (az legújabb kiadás ajánlott).  
2. Java IDE, például IntelliJ IDEA vagy Eclipse.  
3. Maven telepítve a függőségkezeléshez.  
4. Alapvető Java programozási ismeretek és a Maven `pom.xml`-jének ismerete.  

## A GroupDocs Conversion Java beállítása

Adja hozzá a GroupDocs Maven függőséget a `pom.xml`-jéhez:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Licenc beszerzése:** Ingyenes próba verziót szerezhet, kérhet ideiglenes licencet a teljes funkcionalitáshoz, vagy megvásárolhat egy állandó licencet, amely teljes mértékben feloldja a GroupDocs Conversion funkciókat.

Miután a Java projektje helyesen kapcsolódik ezekhez a függőségekhez, készen áll a CAD fájlok konvertálására!

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

## Hogyan konvertáljuk a CAD-et TIFF-re egyedi méretekkel?

A CAD fájlok TIFF-re konvertálása pontos méretekkel magában foglalja a forrásrajz betöltését, a renderelési beállítások konfigurálását és a konvertálási API meghívását. Egy lineáris sorrend követésével – a szélesség és magasság beállítása, a TIFF kiválasztása kimeneti formátumként, és a konvertálás végrehajtása – biztosítható, hogy a létrehozott kép pontosan megfeleljen a downstream alkalmazások méretkövetelményeinek, miközben megőrzi az eredeti rajz részleteit és minőségét.  

1. **Importálja a szükséges osztályokat** (lásd az alábbi lépés‑ről‑lépésre útmutatót).  
2. **Hozzon létre egy `CadLoadOptions` példányt**, és állítsa be a `width` és `height` értékeket a kívánt méretekre.  
3. **Példányosítsa az `ImageConvertOptions`-t**, megadva az `ImageFileType.Tiff` értéket.  
4. **Hívja meg a `convert` metódust** egy `Converter` objektumon, átadva a forrás útvonalát, a betöltési beállításokat és a konvertálási beállításokat.  

### CAD dokumentumok betöltése egyedi méretekkel (Hogyan állítsuk be a méreteket)

A `CadLoadOptions` osztály megmondja a GroupDocs-nak, hogyan rasterizálja a rajzot a konvertálás előtt.

A `CadLoadOptions` egy konfigurációs objektum, amely meghatározza a renderelési paramétereket, például a szélességet, magasságot és DPI-t CAD fájlok esetén.

#### 1. lépés: Szükséges könyvtárak importálása
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### 2. lépés: Betöltési beállítások konfigurálása egyedi méretekkel
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Magyarázat:* A `CadLoadOptions` konfigurálásával azt mondja a **GroupDocs Conversion Java**-nak, hogy a CAD rajzot 1920 × 1080 pixelben rasterizálja minden további feldolgozás előtt.

### CAD konvertálása TIFF képpé (CAD TIFF-re konvertálása)

Az `ImageConvertOptions` irányítja a könyvtárat, hogy a megadott beállításokkal TIFF fájlt állítson elő.

Az `ImageConvertOptions` tartalmazza az összes képspecifikus konvertálási paramétert, beleértve a kimeneti formátumot, felbontást és tömörítési szintet.

#### 3. lépés: Konvertálási beállítások konfigurálása
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### 4. lépés: A konvertálás végrehajtása
```java
converter.convert(convertedFilePath, options);
```
*Magyarázat:* Az `ImageFileType.Tiff` beállítása azt irányítja a **GroupDocs Conversion Java**-t, hogy magas minőségű TIFF fájlt állítson elő, amely figyelembe veszi a korábban meghatározott szélességet és magasságot.

## Hibaelhárítási tippek és gyakori buktatók
- **Fájlútvonal problémák:** Ellenőrizze, hogy a forrás- és célútvonalak helyesek-e, és hogy az alkalmazásnak van‑e olvasási/írási jogosultsága.  
- **Nem támogatott formátumok:** Győződjön meg arról, hogy a CAD fájl a támogatott formátumok (DWG, DGN, DXF stb.) egyike.  
- **Memória korlátok:** Nagy rajzok esetén szükség lehet a JVM heap méretének növelésére (`-Xmx2g` vagy nagyobb).  
- **Minőségi aggályok:** Állítsa be az `ImageConvertOptions` felbontási beállításait, ha az alap DPI nem felel meg a minőségi követelményeknek.  

## Gyakorlati alkalmazások
1. **Építészeti vizualizáció:** Exportálja az alaprajzokat TIFF formátumban magas felbontású prezentációkhoz.  
2. **Mérnöki dokumentáció:** Készítsen szabványosított képeket a műszaki kézikönyvekbe való beillesztéshez.  
3. **Automatizált jelentéskészítés:** Ágyazzon be CAD‑alapú TIFF fájlokat PDF vagy HTML jelentésekbe CI csővezeték segítségével.  

## Teljesítmény szempontok
- **Memóriahasználat optimalizálása:** Szabadítsa fel a `Converter` példányt a konvertálás után (`converter.close()`, ha alkalmazható).  
- **Kötegelt feldolgozás:** Iteráljon egy CAD fájlok listáján, és használja újra egyetlen `Converter` konfigurációt a terhelés csökkentése érdekében.  
- **Maradjon naprakész:** Rendszeresen frissítse a legújabb GroupDocs Conversion Java kiadásra, hogy élvezze a teljesítményjavulásokat és a hibajavításokat.  

## Gyakran feltett kérdések

**Q:** Milyen fájlformátumokat támogat a GroupDocs Conversion?  
**A:** Több mint 110 formátumot támogat, beleértve a CAD fájlokat, mint a DWG, DGN, DXF, valamint a gyakori kép, dokumentum és archívum típusokat.  

**Q:** Konvertálhatok több CAD fájlt egyszerre?  
**A:** Igen—valósítson meg egy egyszerű ciklust, amely minden fájlhoz új `Converter`-t hoz létre, vagy használja újra ugyanazt a példányt különböző forrás útvonalakkal.  

**Q:** Hogyan kezeljem a nagy fájlméreteket a konvertálás során?  
**A:** Növelje a JVM heap méretét, dolgozza fel a fájlokat kisebb kötegekben, vagy használja a könyvtár által biztosított streaming opciókat.  

**Q:** Mi a teendő, ha a kimeneti képminőség nem kielégítő?  
**A:** Állítsa be a DPI vagy a méretezési beállításokat az `ImageConvertOptions`-ban a felbontás növeléséhez.  

**Q:** Elérhető támogatás, ha problémáim vannak?  
**A:** A GroupDocs kiterjedt dokumentációt, közösségi fórumokat és közvetlen támogatást kínál a licencelt ügyfelek számára.  

## Források
- [GroupDocs dokumentáció](https://docs.groupdocs.com/conversion/java/)
- [API referencia](https://reference.groupdocs.com/conversion/java/)
- [Legújabb kiadás letöltése](https://releases.groupdocs.com/conversion/java/)
- [Licenc vásárlása](https://purchase.groupdocs.com/buy)
- [Ingyenes próba hozzáférés](https://releases.groupdocs.com/conversion/java/)
- [Ideiglenes licenc kérése](https://purchase.groupdocs.com/temporary-license/)
- [Támogatási fórum](https://forum.groupdocs.com/c/conversion/10)

---

**Utolsó frissítés:** 2026-07-24  
**Tesztelve ezzel:** GroupDocs Conversion Java 25.2  
**Szerző:** GroupDocs  

## Kapcsolódó oktatóanyagok

- [convert cad pdf java – CAD formátum konvertálási oktatóanyagok a GroupDocs.Conversion Java-hoz](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Útmutató](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Hogyan állítsuk be a licencet a GroupDocs.Conversion Java-hoz – Lépés‑ről‑lépésre útmutató](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)