---
"date": "2025-05-01"
"description": "Lär dig hur du konverterar gamla Macintosh-kalkylbladsfiler (.sxc) till mångsidiga CSV-format med GroupDocs.Conversion för .NET. Följ vår steg-för-steg-guide."
"title": "Konvertera SXC till CSV med GroupDocs.Conversion för .NET – en komplett guide"
"url": "/sv/net/spreadsheet-formats-features/convert-sxc-to-csv-groupdocs-conversion-dotnet/"
"weight": 1
---

# Konvertera SXC till CSV med GroupDocs.Conversion för .NET

## Introduktion

Har du svårt att konvertera äldre Macintosh-kalkylbladsfiler (.sxc) till mer lättillgängliga och mångsidiga CSV-format? Denna vanliga utmaning kan lösas smidigt med hjälp av det kraftfulla GroupDocs.Conversion för .NET-biblioteket. I den här handledningen guidar vi dig genom att effektivt konvertera dina SXC-filer till CSV-format.

- **Vad du kommer att lära dig:**
  - Hur man laddar och konverterar SXC-filer med GroupDocs.Conversion
  - Ställa in konverteringsalternativ för export som CSV
  - Spara den konverterade filen enkelt

Låt oss gå igenom vad du behöver innan vi börjar.

## Förkunskapskrav

Innan du börjar med kod, se till att din miljö är redo:

- **Obligatoriska bibliotek:**
  - GroupDocs.Conversion för .NET (version 25.3.0)

- **Krav för miljöinstallation:**
  - Visual Studio eller någon annan föredragen IDE som stöder C#
  

- **Kunskapsförkunskapskrav:**
  - Grundläggande förståelse för filhantering i C#

## Konfigurera GroupDocs.Conversion för .NET

Låt oss först installera det nödvändiga biblioteket:

**NuGet-pakethanterarkonsolen**

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**.NET CLI**

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### Licensförvärv

Du kan börja med en gratis provperiod för att utforska funktionerna i GroupDocs.Conversion:

- **Gratis provperiod:** Använda [den här länken](https://releases.groupdocs.com/conversion/net/) att ladda ner.
- **Tillfällig licens:** Skaffa en [här](https://purchase.groupdocs.com/temporary-license/).
- **Köpa:** För fullständig åtkomst, besök [GroupDocs köpsida](https://purchase.groupdocs.com/buy).

### Grundläggande initialisering och installation

För att initiera GroupDocs.Conversion i ditt C#-projekt:

```csharp
using GroupDocs.Conversion;
// Din kod för att ladda filer kommer att placeras här
```

## Implementeringsguide

Nu ska vi dela upp implementeringen i tydliga steg.

### Ladda källfilen SXC

#### Översikt

Att ladda en SXC-fil är det första steget i vår konverteringsprocess. Detta innebär att initiera en `Converter` objekt med källfilens sökväg.

**Steg-för-steg-guide**

##### Initiera konverterobjekt

```csharp
string sampleSxcPath = "YOUR_DOCUMENT_DIRECTORY/sample.sxc";
// Ladda källfilen för SXC
var converter = new Converter(sampleSxcPath);
```

- **Parametrar:**
  - `sampleSxcPath`Den fullständiga sökvägen till din SXC-fil.
  

Det här steget säkerställer att konverteringsprocessen kan komma åt och läsa din indatafil korrekt.

### Ställ in konverteringsalternativ till CSV

#### Översikt

Nästa steg är att definiera hur vår SXC-fil ska konverteras till CSV-format. Detta innebär att konfigurera `SpreadsheetConvertOptions`.

**Steg-för-steg-guide**

##### Konfigurera konverteringsalternativ

```csharp
using GroupDocs.Conversion.Options.Convert;
// Skapa en instans av SpreadsheetConvertOptions med önskade inställningar
var convertOptions = new SpreadsheetConvertOptions 
{
    Format = FileType.Csv // Ange målformatet som CSV
};
```

- **Nyckelkonfiguration:**
  - `Format`Anger att utdata ska vara i CSV-format.

Den här konfigurationen anger exakt hur GroupDocs.Conversion ska bearbeta och exportera din fil.

### Utför konvertering och spara utdatafilen

#### Översikt

Slutligen utför vi konverteringen och sparar resultatet. Detta steg är avgörande för att få önskad CSV-utdata.

**Steg-för-steg-guide**

##### Utför konvertering och spara

```csharp
string outputFile = Path.Combine("YOUR_OUTPUT_DIRECTORY\