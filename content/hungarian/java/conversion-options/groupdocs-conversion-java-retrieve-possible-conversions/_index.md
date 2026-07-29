---
date: '2026-07-29'
description: Fedezze fel, hogyan listázhatja a formátumokat és szerezheti be az összes
  lehetséges konverziót a GroupDocs.Conversion for Java használatával, ideális felhőalapú
  tárolási fájlkonvertálási munkafolyamatokhoz.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Tanulja meg, hogyan listázhatja a formátumokat és szerezheti be az
  összes lehetséges konverziót a GroupDocs.Conversion for Java segítségével. Ideális
  felhőalapú tárolási fájlkonvertálási csővezetékekhez.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Formátumok listázása a GroupDocs.Conversion for Java segítségével
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
title: Formátumok listázása a GroupDocs.Conversion for Java segítségével
type: docs
url: /hu/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Hogyan listázzuk a formátumokat és szerezzük meg az összes lehetséges konverziót a GroupDocs.Conversion for Java használatával

Sok dokumentumfeldolgozó projektben az első lépés annak tudása, hogy **hogyan listázzuk a formátumokat**, amelyeket a konverziós motor támogat. Ez az útmutató lépésről lépésre megmutatja, hogyan kérdezzük le a GroupDocs.Conversion for Java‑t, hogyan szerezzük meg minden forrás‑cél párt, és hogyan alkalmazzuk ezt a tudást felhőalapú tároló fájlkörnyezetekben. A végére egy újrahasználható metódust kapunk, amely visszaadja a teljes konverziós mátrixot, valamint gyakorlati tippeket a teljesítményhez és a hibakezeléshez.

## Gyors válaszok
- **Mi jelent a „list formats” kifejezés?** A könyvtár minden forrás‑cél konverziós párját adja vissza.  
- **Szükségem van licencre?** Egy ingyenes próba a teszteléshez működik; a termeléshez fizetett licenc szükséges.  
- **Segíthet ez a felhőalapú tároló fájlkörnyezet konverziójában?** Igen – a támogatott formátumok ismerete lehetővé teszi a konverziók automatizálását a felhőalapú tároló csővezetékekben.  
- **Melyik Java verzió szükséges?** JDK 8 vagy újabb.  
- **A funkció szálbiztos?** A `Converter` példány több szál között újrahasználható, de a használat után szabadítsa fel az erőforrásokat.

## Mi a „hogyan listázzuk a formátumokat” a GroupDocs.Conversion‑ben?
A **list formats** művelet egy gyűjteményt ad vissza, amely leírja minden forrásformátumot a hozzájuk alakítható célformátumokkal együtt. Ez a mátrix a könyvtár belső konverziós szabályaiból származik, és elengedhetetlen a dinamikus munkafolyamatok felépítéséhez, amelyek a futásidőben a GroupDocs.Conversion tényleges képességeihez igazodnak.

## Miért használjuk a GroupDocs.Conversion for Java‑t?
A GroupDocs.Conversion for Java **200+ bemeneti formátumot** és **200+ kimeneti formátumot** támogat, lefedve mindent a DOCX‑től és PPTX‑től a PDF/A‑ig és a képformátumokig. Teljesen a szerveren fut, így nincs szükség Microsoft Office vagy Adobe termékekre. Az API szálbiztos, képes több száz oldalas dokumentumok feldolgozására anélkül, hogy az egész fájlt a memóriába töltené, és zökkenőmentesen integrálódik a felhőalapú tárolási szolgáltatásokkal, mint az AWS S3, Azure Blob és a Google Cloud Storage.

## Előfeltételek
- **Java Development Kit (JDK):** 8-as vagy újabb verzió.  
- **Maven:** Az IDE‑ben megfelelően konfigurálva (IntelliJ IDEA, Eclipse, NetBeans stb.).  
- **GroupDocs.Conversion for Java:** Maven függőségként hozzáadva (lásd alább).

## A GroupDocs.Conversion for Java beállítása

Adja hozzá a GroupDocs tárolót és a függőséget a `pom.xml`‑hez:

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

### Licenc beszerzése
Kezdje egy ingyenes próbaidőszakkal az API felfedezéséhez. Termelési feladatokhoz vásároljon licencet vagy kérjen ideiglenes értékelő licencet.

### Alapvető inicializálás és beállítás

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

## Hogyan listázzuk a formátumokat a GroupDocs.Conversion for Java használatával
`Converter` az a központi osztály, amely a konverziókat végzi és formátuminformációkat biztosít. A `getAllPossibleConversions()` visszaadja az összes támogatott forrás‑cél konverziós pár listáját. A `ConversionInfo` egyetlen konverziós leképezést képvisel egy forrás és egy cél formátum között.  

Töltse be a `Converter` motorját, hívja meg a `getAllPossibleConversions()`‑t, és egy `ConversionInfo` objektumok listáját kapja, amelyek leírják minden megengedett forrás‑cél párt. Ez az egyetlen hívás elegendő egy export opciókat tartalmazó legördülő lista, a bejövő fájlok validálása vagy kötegelt migrációs szkriptek megtervezéséhez.

### Inicializálás és konverziók lekérése
A `Converter` osztály a központi motor, amely konverziós képességeket biztosít és kiépíti a `getAllPossibleConversions()` metódust.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Lehetséges konverziók iterálása

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Konverziós típusok meghatározása

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Teljes függvény

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

## Felhőalapú tároló fájl konverzió felhasználási esetek
A teljes konverziós mátrix ismerete különösen értékes, amikor **felhőalapú tároló fájl konverzió** szolgáltatásokat építünk:

1. **Dinamikus formátumdetektálás:** Amikor egy fájl megérkezik a felhőalapú tárolóba, azonnal lekérdezhető, hogy a kívánt célformátum támogatott‑e.  
2. **Kötegelt migráció:** Nagy dokumentumtárakat egy egységes formátumba (pl. PDF/A) mozgatni a támogatott forrástípusok iterálásával.  
3. **Felhasználó‑vezérelt export:** A végfelhasználóknak csak azokat a formátumokat kínálja legördülőben, amelyekre a jelenlegi dokumentum exportálható, ezáltal csökkentve a hibákat és javítva a felhasználói élményt.

## Teljesítmény szempontok
- **Erőforrás-kezelés:** Szabadítsa fel a `Converter` példányt, vagy használjon try‑with‑resources‑t, ha sok rövid életű konvertert hoz létre.  
- **Kötegelt feldolgozás:** Több fájlt csoportosítson egyetlen feladatba a terhelés csökkentése érdekében.  
- **Gyorsítótárazás:** Cache‑elje a `getAllPossibleConversions()` eredményét, ha gyakran lekérdezi; a konverziós mátrix ritkán változik futásidőben.  

## Gyakori problémák és megoldások

| Tünet | Valószínű ok | Megoldás |
|---------|--------------|-----|
| Nincs kimenet | `Converter` nincs megfelelően inicializálva | Győződjön meg róla, hogy a könyvtár JAR a classpath‑on van, és a licenc betöltve. |
| `TargetConversion` lista üres | Elavult könyvtárverzió használata | Frissítsen a legújabb GroupDocs.Conversion kiadásra. |
| Memória csúcsok nagy dokumentumoknál | A konverter erőforrásainak nem felszabadítása | Hívja a `converter.close()`‑t vagy használjon try‑with‑resources‑t. |

## Gyakran ismételt kérdések

**Q: Mi a GroupDocs.Conversion for Java?**  
A: Ez egy szerver‑oldali könyvtár, amely 200+ bemeneti és 200+ kimeneti formátumot támogat, lehetővé téve a gyors, licenc‑ingyenes dokumentumkonverziót külső szoftverek nélkül.

**Q: Hogyan kezdjek hozzá a GroupDocs.Conversion-hoz?**  
A: Állítsa be Maven projektjét, adja hozzá a korábban bemutatott függőséget, töltse be a licencfájlt, és hozza létre a `Converter` osztály példányát, ahogyan az inicializálási részben bemutattuk.

**Q: Konvertálhatok egyedi fájltípusokat a GroupDocs.Conversion segítségével?**  
A: Igen – az API kiterjeszthető pontjain keresztül regisztrálhat egyedi konvertereket vagy beépíthet harmadik fél kezelőket a saját formátumokhoz.

**Q: Milyen gyakori buktatók vannak a konverziók megvalósításakor?**  
A: A `Converter` bezárásának elfelejtése, régi JAR verzió használata, vagy a memóriahasználat figyelmen kívül hagyása nagyon nagy PDF‑eknél. Kövesse a fentebb leírt erőforrás‑kezelési tippeket.

**Q: Hol kaphatok további segítséget?**  
A: Látogassa meg a hivatalos [dokumentációt](https://docs.groupdocs.com/conversion/java/) vagy tegyen fel kérdéseket a GroupDocs közösségi fórumon.

---

**Legutóbb frissítve:** 2026-07-29  
**Tesztelve a következővel:** GroupDocs.Conversion 25.2 for Java  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [Word átalakítása PDF‑re és más fájlformátumokra a GroupDocs.Conversion for Java‑val](/conversion/java/)
- [Word PDF‑re Java – Követett változások elrejtése és konverziós beállítások](/conversion/java/conversion-options/)
- [Hogyan követhetjük a konverzió előrehaladását Java‑ban a GroupDocs‑szal – Teljes útmutató](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)