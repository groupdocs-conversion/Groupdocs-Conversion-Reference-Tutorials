---
"date": "2025-04-28"
"description": "เรียนรู้วิธีการแปลงเอกสาร Word ที่ป้องกันด้วยรหัสผ่านเป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ Java เชี่ยวชาญในการระบุหน้า ปรับ DPI และหมุนเนื้อหา"
"title": "แปลง Word ที่มีการป้องกันด้วยรหัสผ่านเป็น PDF ใน Java โดยใช้ GroupDocs.Conversion"
"url": "/th/java/security-protection/convert-password-protected-word-pdf-java/"
"weight": 1
type: docs
---
# แปลง Word ที่มีการป้องกันด้วยรหัสผ่านเป็น PDF ใน Java โดยใช้ GroupDocs.Conversion

แปลงเอกสาร Word ที่ได้รับการป้องกันของคุณเป็นรูปแบบ PDF ได้อย่างง่ายดายด้วยคู่มือที่ครอบคลุมนี้เกี่ยวกับการใช้ไลบรารี GroupDocs.Conversion ใน Java ค้นพบวิธีการระบุหน้าเฉพาะ กำหนดขนาดที่กำหนดเอง ปรับความละเอียด และเพิ่มประสิทธิภาพการทำงานเพื่อการแปลงเอกสารที่ราบรื่น

## สิ่งที่คุณจะได้เรียนรู้:
- แปลงไฟล์ Word ที่มีการป้องกันด้วยรหัสผ่านโดยใช้ GroupDocs.Conversion สำหรับ Java
- ระบุหน้าหรือส่วนที่แน่นอนของเอกสารเพื่อการแปลงเป็น PDF
- หมุนเนื้อหาเอกสารก่อนที่จะแปลงเป็น PDF
- ปรับการตั้งค่า DPI ให้มีความละเอียดที่กำหนดเองในระหว่างการแปลง PDF
- ปรับปรุงประสิทธิภาพด้วยแนวทางปฏิบัติที่ดีที่สุดในการจัดการหน่วยความจำ Java

## ข้อกำหนดเบื้องต้น
ให้แน่ใจว่าคุณได้ครอบคลุมข้อกำหนดเบื้องต้นต่อไปนี้ก่อนดำเนินการต่อ:

### ไลบรารีและการอ้างอิงที่จำเป็น
ในการใช้ GroupDocs.Conversion ให้รวมไลบรารีที่จำเป็น หากใช้ Maven ให้เพิ่มที่เก็บข้อมูลและการอ้างอิงลงในของคุณ `pom.xml`-

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

### การตั้งค่าสภาพแวดล้อม
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งและกำหนดค่า Java Development Kit (JDK) บนเครื่องของคุณแล้ว ขอแนะนำให้มีความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java

### การขอใบอนุญาต
GroupDocs.Conversion นำเสนอเวอร์ชันทดลองใช้งานฟรีสำหรับการทดสอบฟีเจอร์ต่างๆ หากต้องการใช้งานแบบขยายเวลา โปรดพิจารณาซื้อใบอนุญาตชั่วคราวหรือฉบับเต็มจาก [การซื้อ GroupDocs](https://purchase-groupdocs.com/buy).

## การตั้งค่า GroupDocs.Conversion สำหรับ Java
ในการเริ่มต้นด้วย GroupDocs.Conversion ให้ทำการตั้งค่าเริ่มต้นบางอย่างในโครงการของคุณ

### การตั้งค่า Maven
รวมการอ้างอิง Maven ที่จำเป็นดังที่กล่าวไว้ก่อนหน้านี้เพื่อให้แน่ใจว่าไลบรารีที่จำเป็นทั้งหมดสามารถดาวน์โหลดได้และพร้อมใช้งาน

### การเริ่มต้นขั้นพื้นฐาน
เริ่มต้น GroupDocs.Conversion โดยการสร้างอินสแตนซ์ของ `Converter` ชั้นเรียน นี่คือการตั้งค่าพื้นฐาน:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.WordProcessingLoadOptions;

WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
// ตั้งรหัสผ่านสำหรับเอกสารที่ได้รับการป้องกันหากจำเป็น:
loadOptions.setPassword("your_password_here");

Converter converter = new Converter("path_to_your_document.docx", () -> loadOptions);
```

สไนปเป็ตนี้จะเริ่มต้นการแปลงเอกสาร `loadOptions` คลาสช่วยจัดการการป้องกันด้วยรหัสผ่านและการตั้งค่าอื่นๆ

## คู่มือการใช้งาน
มาสำรวจวิธีการนำฟีเจอร์หลักไปใช้โดยใช้ GroupDocs.Conversion ใน Java กัน

### แปลงเอกสารที่ป้องกันด้วยรหัสผ่านเป็น PDF
**ภาพรวม:**
แปลงเอกสาร Word ที่ป้องกันด้วยรหัสผ่านเป็นไฟล์ PDF ได้อย่างราบรื่น

#### การดำเนินการแบบทีละขั้นตอน
##### เริ่มต้นโหลดตัวเลือกด้วยรหัสผ่าน
ตั้งรหัสผ่านสำหรับการเข้าถึงเอกสารที่ได้รับการป้องกันของคุณ:

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("12345"); // แทนที่ด้วยรหัสผ่านจริงของคุณ
```

##### ตั้งค่าตัวแปลงและแปลง
เริ่มต้นการใช้งาน `Converter` คลาส กำหนดตัวเลือกการแปลง PDF และดำเนินการแปลง:

```java
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedDocument.pdf";
PdfConvertOptions options = new PdfConvertOptions();

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleProtectedDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**คำอธิบาย:**
การ `loadOptions` วัตถุเป็นสิ่งสำคัญสำหรับการจัดการเอกสารที่ป้องกันด้วยรหัสผ่าน การตั้งรหัสผ่านอย่างถูกต้องจะช่วยให้เข้าถึงและแปลงไฟล์ได้สำเร็จ

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบความถูกต้องของรหัสผ่านอีกครั้ง เนื่องจากการพิมพ์ผิดถือเป็นปัญหาทั่วไป
- ตรวจสอบเส้นทางไฟล์เพื่อป้องกัน `FileNotFoundException`-

### ระบุหน้าที่จะแปลงเป็น PDF
**ภาพรวม:**
เลือกหน้าเฉพาะของเอกสารของคุณเพื่อแปลง PDF

#### การดำเนินการแบบทีละขั้นตอน
##### ตั้งค่าช่วงหน้า
กำหนดหน้าที่คุณต้องการแปลง:

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2); // เริ่มตั้งแต่หน้า 2.
options.setPagesCount(1); // แปลงเพียงหน้าเดียว
```

##### กระบวนการแปลง
ใช้การตั้งค่าตามที่ระบุ `options` สำหรับการแปลง:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SelectedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**คำอธิบาย:**
การ `setPageNumber()` และ `setPagesCount()` วิธีการดังกล่าวช่วยให้สามารถควบคุมส่วนเอกสารใดที่จะถูกแปลงได้อย่างแม่นยำ

### หมุนหน้าในการแปลง PDF
**ภาพรวม:**
หมุนหน้าในระหว่างการแปลงเพื่อให้ได้ทิศทางที่ต้องการ

#### การดำเนินการแบบทีละขั้นตอน
##### ตั้งค่าตัวเลือกการหมุน
ระบุการตั้งค่าการหมุน:

```java
import com.groupdocs.conversion.options.convert.Rotation;

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On180); // หมุนหน้ากระดาษ 180 องศา
```

##### ดำเนินการแปลง
เริ่มต้นและแปลงด้วยตัวเลือกการหมุนที่ระบุ:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/RotatedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**คำอธิบาย:**
การหมุนหน้าอาจเป็นประโยชน์ในการแก้ไขการวางแนวหรือการตอบสนองความต้องการเค้าโครงเฉพาะ

### ตั้งค่า Dpi สำหรับการแปลง PDF
**ภาพรวม:**
ปรับความละเอียด (DPI) ของ PDF ที่คุณแปลงให้เหมาะกับความต้องการด้านคุณภาพ

#### การดำเนินการแบบทีละขั้นตอน
##### กำหนดค่าการตั้งค่า DPI
ตั้งค่า DPI ที่ต้องการ:

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(300); // ตั้งค่า DPI เป็น 300 เพื่อความละเอียดสูง
```

##### ดำเนินการแปลงด้วย DPI ที่กำหนดเอง
ดำเนินการแปลงโดยใช้การตั้งค่าเหล่านี้:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/HighResolutionPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**คำอธิบาย:**
ค่า DPI ที่สูงขึ้นจะช่วยเพิ่มคุณภาพของภาพแต่ขนาดไฟล์อาจเพิ่มขึ้น ปรับเปลี่ยนตามความต้องการของคุณ

### ตั้งค่าความกว้างและความสูงสำหรับการแปลง PDF
**ภาพรวม:**
ปรับแต่งขนาดของ PDF ที่ได้ในระหว่างการแปลง

#### การดำเนินการแบบทีละขั้นตอน
##### กำหนดมิติ
ตั้งค่าพารามิเตอร์ความกว้างและความสูง:

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setWidth(1024); // ตั้งค่าความกว้างเป็น 1,024 พิกเซล
options.setHeight(768); // ตั้งค่าความสูงเป็น 768 พิกเซล
```

##### แปลงด้วยขนาดที่กำหนดเอง
ดำเนินการแปลงโดยใช้มิติเหล่านี้:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SizedPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**คำอธิบาย:**
การกำหนดขนาดเองจะช่วยปรับแต่งผลลัพธ์ PDF ให้ตรงกับความต้องการในการแสดงผลหรือการพิมพ์ที่เฉพาะเจาะจง