---
"description": "Chuyển đổi JPG sang PDF dễ dàng bằng GroupDocs.Conversion cho .NET. Làm theo hướng dẫn từng bước này để chuyển đổi tài liệu liền mạch."
"linktitle": "Chuyển đổi JPG sang PDF"
"second_title": "API GroupDocs.Conversion .NET"
"title": "Chuyển đổi JPG sang PDF"
"url": "/vi/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
---

# Chuyển đổi JPG sang PDF

## Giới thiệu

Bạn có muốn chuyển đổi tệp JPG sang PDF dễ dàng bằng GroupDocs.Conversion cho .NET không? Hướng dẫn này sẽ hướng dẫn bạn từng bước trong quy trình. GroupDocs.Conversion cho .NET là một API mạnh mẽ cho phép bạn dễ dàng chuyển đổi liền mạch nhiều định dạng tài liệu, bao gồm cả hình ảnh, sang PDF. Hãy cùng tìm hiểu!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đáp ứng các điều kiện tiên quyết sau:

1. GroupDocs.Conversion cho .NET: Đảm bảo bạn đã cài đặt GroupDocs.Conversion cho .NET. Bạn có thể tải xuống từ [đây](https://releases.groupdocs.com/conversion/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển, chẳng hạn như Visual Studio, cùng với .NET Framework hoặc .NET Core.
3. Tệp JPG mẫu: Chuẩn bị tệp JPG mẫu mà bạn muốn chuyển đổi sang PDF.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Bây giờ, chúng ta hãy chia nhỏ quá trình chuyển đổi thành các bước đơn giản:

## Bước 1: Xác định thư mục đầu ra và tên tệp

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Đảm bảo chỉ định thư mục mà bạn muốn lưu tệp PDF đã chuyển đổi và tên tệp đầu ra mong muốn.

## Bước 2: Tải tệp JPG nguồn và chuyển đổi sang PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Khởi tạo `Converter` đối tượng với đường dẫn đến tệp JPG mẫu của bạn. Sau đó, cấu hình các tùy chọn chuyển đổi, chẳng hạn như chỉ định các tùy chọn chuyển đổi PDF. Cuối cùng, gọi `Convert` phương pháp, truyền đường dẫn tệp đầu ra và các tùy chọn chuyển đổi.

## Bước 3: Hiển thị thông báo hoàn tất chuyển đổi

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Sau khi quá trình chuyển đổi hoàn tất, sẽ hiển thị thông báo cho biết quá trình chuyển đổi thành công và vị trí của tệp PDF đã chuyển đổi.

## Phần kết luận

Chuyển đổi tệp JPG sang PDF bằng GroupDocs.Conversion cho .NET rất đơn giản chỉ với một vài dòng mã. Bằng cách làm theo hướng dẫn này, bạn có thể tích hợp liền mạch các khả năng chuyển đổi tài liệu vào các ứng dụng .NET của mình.

## Câu hỏi thường gặp

### H: Tôi có thể chuyển đổi nhiều tệp JPG sang PDF cùng lúc không?

A: Có, bạn có thể chuyển đổi nhiều tệp JPG sang PDF bằng cách lặp lại từng tệp và thực hiện quy trình chuyển đổi được mô tả trong hướng dẫn.

### H: GroupDocs.Conversion có hỗ trợ các định dạng hình ảnh khác ngoài JPG không?

A: Có, GroupDocs.Conversion hỗ trợ nhiều định dạng hình ảnh như PNG, TIFF, BMP và GIF, cùng nhiều định dạng khác.

### H: Tôi có thể tùy chỉnh tệp PDF đầu ra bằng các tùy chọn chuyển đổi không?

A: Hoàn toàn đúng! GroupDocs.Conversion cung cấp nhiều tùy chọn chuyển đổi cho phép bạn tùy chỉnh tệp PDF đầu ra theo yêu cầu của mình.

### H: Có phiên bản dùng thử của GroupDocs.Conversion dành cho .NET không?

A: Có, bạn có thể truy cập phiên bản dùng thử miễn phí của GroupDocs.Conversion cho .NET từ [đây](https://releases.groupdocs.com/).

### H: Tôi có thể tìm kiếm sự trợ giúp ở đâu nếu gặp bất kỳ vấn đề nào trong quá trình chuyển đổi?

A: Nếu bạn gặp bất kỳ vấn đề nào hoặc có câu hỏi liên quan đến GroupDocs.Conversion cho .NET, vui lòng truy cập [Diễn đàn GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) để được hỗ trợ.