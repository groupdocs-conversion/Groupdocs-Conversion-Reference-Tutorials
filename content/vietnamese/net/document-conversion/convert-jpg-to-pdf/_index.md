---
title: Chuyển đổi JPG sang PDF
linktitle: Chuyển đổi JPG sang PDF
second_title: API GroupDocs.Conversion .NET
description: Chuyển đổi JPG sang PDF dễ dàng bằng GroupDocs.Conversion cho .NET. Hãy làm theo hướng dẫn từng bước này để chuyển đổi tài liệu liền mạch.
weight: 14
url: /vi/net/document-conversion/convert-jpg-to-pdf/
---

# Chuyển đổi JPG sang PDF

## Giới thiệu

Bạn đang muốn chuyển đổi tệp JPG sang PDF dễ dàng bằng GroupDocs.Conversion cho .NET? Hướng dẫn này sẽ hướng dẫn bạn từng bước thực hiện quy trình. GroupDocs.Conversion for .NET là một API mạnh mẽ cho phép bạn chuyển đổi liền mạch các định dạng tài liệu khác nhau, bao gồm cả hình ảnh, sang PDF một cách dễ dàng. Hãy đi sâu vào!

## Điều kiện tiên quyết

Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:

1.  GroupDocs.Conversion cho .NET: Đảm bảo bạn đã cài đặt GroupDocs.Conversion cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/conversion/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển, chẳng hạn như Visual Studio, cùng với .NET Framework hoặc .NET Core.
3. Tệp JPG mẫu: Chuẩn bị tệp JPG mẫu mà bạn muốn chuyển đổi sang PDF.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Bây giờ, hãy chia quá trình chuyển đổi thành các bước đơn giản:

## Bước 1: Xác định thư mục đầu ra và tên tệp

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Đảm bảo chỉ định thư mục nơi bạn muốn lưu tệp PDF đã chuyển đổi và tên tệp đầu ra mong muốn.

## Bước 2: Tải tệp JPG nguồn và chuyển đổi sang PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Khởi tạo`Converter` object bằng đường dẫn đến tệp JPG mẫu của bạn. Sau đó, định cấu hình các tùy chọn chuyển đổi, chẳng hạn như chỉ định các tùy chọn chuyển đổi PDF. Cuối cùng, hãy gọi`Convert` phương thức, chuyển đường dẫn tệp đầu ra và các tùy chọn chuyển đổi.

## Bước 3: Hiển thị thông báo hoàn thành chuyển đổi

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Sau khi quá trình chuyển đổi hoàn tất, hiển thị thông báo cho biết quá trình chuyển đổi thành công và vị trí của tệp PDF được chuyển đổi.

## Phần kết luận

Chuyển đổi tệp JPG sang PDF bằng GroupDocs.Conversion cho .NET thật đơn giản chỉ với một vài dòng mã. Bằng cách làm theo hướng dẫn này, bạn có thể tích hợp liền mạch khả năng chuyển đổi tài liệu vào các ứng dụng .NET của mình.

## Câu hỏi thường gặp

### H: Tôi có thể chuyển đổi nhiều tệp JPG sang PDF cùng một lúc không?

Đáp: Có, bạn có thể chuyển đổi nhiều tệp JPG thành PDF bằng cách lặp lại từng tệp và thực hiện quy trình chuyển đổi được mô tả trong hướng dẫn.

### Câu hỏi: GroupDocs.Conversion có hỗ trợ các định dạng hình ảnh khác ngoài JPG không?

Trả lời: Có, GroupDocs.Conversion hỗ trợ nhiều định dạng hình ảnh khác nhau như PNG, TIFF, BMP và GIF, cùng nhiều định dạng khác.

### H: Tôi có thể tùy chỉnh tệp PDF đầu ra bằng các tùy chọn chuyển đổi không?

Đ: Chắc chắn rồi! GroupDocs.Conversion cung cấp nhiều tùy chọn chuyển đổi cho phép bạn tùy chỉnh tệp PDF đầu ra theo yêu cầu của mình.

### Câu hỏi: Có phiên bản dùng thử của GroupDocs.Conversion dành cho .NET không?

Đáp: Có, bạn có thể truy cập phiên bản dùng thử miễn phí của GroupDocs.Conversion dành cho .NET từ[đây](https://releases.groupdocs.com/).

### Hỏi: Tôi có thể tìm kiếm trợ giúp ở đâu nếu gặp bất kỳ vấn đề nào trong quá trình chuyển đổi?

 Đáp: Nếu bạn gặp phải bất kỳ vấn đề nào hoặc có thắc mắc liên quan đến GroupDocs.Conversion cho .NET, vui lòng truy cập vào[Diễn đàn GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) để được hỗ trợ.