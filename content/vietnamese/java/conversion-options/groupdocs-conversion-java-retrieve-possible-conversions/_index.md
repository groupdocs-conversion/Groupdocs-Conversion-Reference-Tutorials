---
date: '2026-07-29'
description: Khám phá cách liệt kê các định dạng và lấy tất cả các chuyển đổi có thể
  sử dụng GroupDocs.Conversion for Java, lý tưởng cho quy trình chuyển đổi tệp lưu
  trữ đám mây.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Tìm hiểu cách liệt kê các định dạng và lấy tất cả các chuyển đổi có
  thể sử dụng GroupDocs.Conversion for Java. Lý tưởng cho các đường ống chuyển đổi
  tệp lưu trữ đám mây.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Cách liệt kê các định dạng với GroupDocs.Conversion for Java
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
title: Cách liệt kê các định dạng với GroupDocs.Conversion for Java
type: docs
url: /vi/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Cách liệt kê các định dạng và truy xuất tất cả các chuyển đổi khả dụng với GroupDocs.Conversion cho Java

Trong nhiều dự án xử lý tài liệu, bước đầu tiên là biết **cách liệt kê các định dạng** mà engine chuyển đổi hỗ trợ. Hướng dẫn này sẽ chỉ cho bạn, từng bước, cách truy vấn GroupDocs.Conversion cho Java, lấy mọi cặp nguồn‑đến‑đích, và áp dụng kiến thức đó trong các pipeline chuyển đổi tệp trên lưu trữ đám mây. Khi hoàn thành, bạn sẽ có một phương thức tái sử dụng trả về ma trận chuyển đổi đầy đủ, cùng các mẹo thực tế về hiệu năng và xử lý lỗi.

## Câu trả lời nhanh
- **“list formats” có nghĩa là gì?** Nó trả về mọi cặp chuyển đổi nguồn‑đến‑đích mà thư viện có thể xử lý.  
- **Tôi có cần giấy phép không?** Một bản dùng thử miễn phí hoạt động cho việc thử nghiệm; giấy phép trả phí là bắt buộc cho môi trường sản xuất.  
- **Điều này có giúp chuyển đổi tệp lưu trữ đám mây không?** Có — việc biết các định dạng được hỗ trợ cho phép bạn tự động hóa các chuyển đổi trong pipeline lưu trữ đám mây.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc mới hơn.  
- **Tính năng này có an toàn với đa luồng không?** Đối tượng `Converter` có thể được tái sử dụng trên nhiều luồng, nhưng cần giải phóng tài nguyên sau khi sử dụng.

## “cách liệt kê các định dạng” trong GroupDocs.Conversion là gì?
Hoạt động **list formats** trả về một tập hợp mô tả mọi định dạng nguồn cùng với các định dạng đích mà nó có thể chuyển đổi sang. Ma trận này được tạo ra từ các quy tắc chuyển đổi nội bộ của thư viện và rất quan trọng để xây dựng các workflow động thích ứng với khả năng thực tế của GroupDocs.Conversion tại thời gian chạy.

## Tại sao nên sử dụng GroupDocs.Conversion cho Java?
GroupDocs.Conversion cho Java hỗ trợ **hơn 200 định dạng đầu vào** và **hơn 200 định dạng đầu ra**, bao gồm mọi thứ từ DOCX và PPTX đến PDF/A và các loại hình ảnh. Nó chạy hoàn toàn trên máy chủ, vì vậy không cần Microsoft Office hay sản phẩm Adobe. API an toàn với đa luồng, có thể xử lý tài liệu hàng trăm trang mà không cần tải toàn bộ tệp vào bộ nhớ, và tích hợp liền mạch với các dịch vụ lưu trữ đám mây như AWS S3, Azure Blob và Google Cloud Storage.

## Yêu cầu trước
- **Java Development Kit (JDK):** Phiên bản 8 hoặc mới hơn.  
- **Maven:** Được cấu hình đúng trong IDE của bạn (IntelliJ IDEA, Eclipse, NetBeans, v.v.).  
- **GroupDocs.Conversion cho Java:** Được thêm như một phụ thuộc Maven (xem bên dưới).  

## Cài đặt GroupDocs.Conversion cho Java

Thêm repository và phụ thuộc GroupDocs vào `pom.xml` của bạn:

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

### Nhận giấy phép
Bắt đầu với bản dùng thử miễn phí để khám phá API. Đối với các tải công việc sản xuất, mua giấy phép hoặc yêu cầu giấy phép đánh giá tạm thời.

### Khởi tạo và Cấu hình Cơ bản

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

## Cách liệt kê các định dạng bằng GroupDocs.Conversion cho Java
`Converter` là lớp cốt lõi thực hiện chuyển đổi và cung cấp thông tin định dạng. `getAllPossibleConversions()` trả về danh sách tất cả các cặp chuyển đổi nguồn‑đến‑đích được hỗ trợ. `ConversionInfo` đại diện cho một ánh xạ chuyển đổi duy nhất giữa định dạng nguồn và đích.  

Tải engine `Converter`, gọi `getAllPossibleConversions()`, và bạn sẽ nhận được danh sách các đối tượng `ConversionInfo` mô tả mọi cặp nguồn‑đến‑đích hợp lệ. Lệnh duy nhất này là tất cả những gì bạn cần để xây dựng dropdown các tùy chọn xuất, xác thực tệp đầu vào, hoặc thiết kế các script di chuyển hàng loạt.

### Khởi tạo và Lấy các chuyển đổi

Lớp `Converter` là engine cốt lõi cung cấp khả năng chuyển đổi và mở ra phương thức `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Duyệt qua các chuyển đổi khả dụng

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Xác định các loại chuyển đổi

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Hàm hoàn chỉnh

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

## Các trường hợp sử dụng chuyển đổi tệp lưu trữ đám mây
Biết ma trận chuyển đổi đầy đủ đặc biệt có giá trị khi xây dựng các dịch vụ **cloud storage file conversion**:

1. **Phát hiện định dạng động:** Khi một tệp được tải lên lưu trữ đám mây, bạn có thể ngay lập tức truy vấn xem định dạng đích mong muốn có được hỗ trợ hay không.  
2. **Di chuyển hàng loạt:** Di chuyển các thư viện tài liệu lớn sang một định dạng thống nhất (ví dụ, PDF/A) bằng cách duyệt qua các loại nguồn được hỗ trợ.  
3. **Xuất dựa trên người dùng:** Cung cấp cho người dùng cuối một dropdown chỉ chứa các định dạng mà tài liệu hiện tại của họ có thể xuất ra, giảm lỗi và cải thiện trải nghiệm người dùng.

## Các cân nhắc về hiệu năng
- **Quản lý tài nguyên:** Giải phóng đối tượng `Converter` hoặc sử dụng try‑with‑resources nếu bạn tạo nhiều converter ngắn hạn.  
- **Xử lý hàng loạt:** Gom nhiều tệp vào một công việc duy nhất để giảm chi phí phụ trợ.  
- **Caching:** Lưu vào bộ nhớ đệm kết quả của `getAllPossibleConversions()` nếu bạn truy vấn thường xuyên; ma trận chuyển đổi hiếm khi thay đổi trong thời gian chạy.  

## Các vấn đề thường gặp và giải pháp
| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|--------------------|----------------|
| Không có đầu ra nào xuất hiện | `Converter` không được khởi tạo đúng cách | Đảm bảo JAR thư viện có trong classpath và giấy phép đã được tải. |
| Danh sách `TargetConversion` rỗng | Sử dụng phiên bản thư viện lỗi thời | Nâng cấp lên phiên bản GroupDocs.Conversion mới nhất. |
| Tăng đột biến bộ nhớ khi xử lý tài liệu lớn | Không giải phóng tài nguyên của converter | Gọi `converter.close()` hoặc sử dụng try‑with‑resources. |

## Câu hỏi thường gặp

**Q: GroupDocs.Conversion cho Java là gì?**  
A: Đó là một thư viện phía máy chủ hỗ trợ hơn 200 định dạng đầu vào và hơn 200 định dạng đầu ra, cho phép chuyển đổi tài liệu nhanh chóng, không cần giấy phép và không phụ thuộc vào phần mềm bên ngoài.

**Q: Làm thế nào để bắt đầu với GroupDocs.Conversion?**  
A: Thiết lập dự án Maven của bạn, thêm phụ thuộc như đã chỉ ra ở trên, tải tệp giấy phép, và khởi tạo lớp `Converter` như đã trình bày trong phần khởi tạo.

**Q: Tôi có thể chuyển đổi các loại tệp tùy chỉnh bằng GroupDocs.Conversion không?**  
A: Có — thông qua các điểm mở rộng của API, bạn có thể đăng ký các converter tùy chỉnh hoặc tích hợp các trình xử lý của bên thứ ba cho các định dạng độc quyền.

**Q: Những khó khăn thường gặp khi triển khai chuyển đổi là gì?**  
A: Quên đóng `Converter`, sử dụng phiên bản JAR cũ, hoặc không chú ý tới việc sử dụng bộ nhớ cho các PDF rất lớn. Hãy tuân theo các mẹo quản lý tài nguyên ở trên.

**Q: Tôi có thể tìm thêm trợ giúp ở đâu?**  
A: Truy cập tài liệu chính thức [documentation](https://docs.groupdocs.com/conversion/java/) hoặc đặt câu hỏi trên diễn đàn cộng đồng GroupDocs.

---

**Cập nhật lần cuối:** 2026-07-29  
**Kiểm thử với:** GroupDocs.Conversion 25.2 cho Java  
**Tác giả:** GroupDocs

## Các hướng dẫn liên quan

- [Chuyển đổi Word sang PDF và các định dạng tệp khác với GroupDocs.Conversion cho Java](/conversion/java/)
- [Word sang PDF Java – Ẩn các thay đổi được theo dõi & tùy chọn chuyển đổi](/conversion/java/conversion-options/)
- [Cách theo dõi tiến trình chuyển đổi trong Java với GroupDocs - Hướng dẫn đầy đủ](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)