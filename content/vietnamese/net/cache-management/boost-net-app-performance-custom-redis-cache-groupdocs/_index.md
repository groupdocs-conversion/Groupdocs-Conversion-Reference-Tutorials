---
"date": "2025-04-28"
"description": "Tìm hiểu cách nâng cao hiệu suất ứng dụng .NET của bạn bằng cách triển khai bộ đệm Redis tùy chỉnh để chuyển đổi tài liệu bằng GroupDocs.Conversion. Cải thiện hiệu quả và tốc độ ngay hôm nay!"
"title": "Tăng hiệu suất ứng dụng .NET&#58; Triển khai bộ đệm Redis tùy chỉnh với GroupDocs.Conversion"
"url": "/vi/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
type: docs
---
# Tăng hiệu suất ứng dụng .NET của bạn với bộ nhớ đệm Redis tùy chỉnh bằng GroupDocs.Conversion

## Giới thiệu

Bạn có đang gặp phải quá trình chuyển đổi tài liệu chậm trong các ứng dụng .NET của mình không? Nâng cao hiệu suất và hiệu quả bằng cách tận dụng bộ đệm Redis tùy chỉnh cùng với GroupDocs.Conversion cho .NET. Hướng dẫn này hướng dẫn bạn thực hiện các thao tác lưu trữ đệm để tăng tốc độ hiển thị tài liệu.

**Những gì bạn sẽ học được:**
- Thiết lập GroupDocs.Conversion cho .NET
- Triển khai bộ nhớ đệm Redis tùy chỉnh để chuyển đổi tài liệu
- Tối ưu hóa hiệu suất với các chiến lược lưu trữ đệm hiệu quả

Chúng tôi sẽ hướng dẫn bạn cách nâng cao hiệu quả ứng dụng của mình bằng các công cụ mạnh mẽ này. Trước khi bắt đầu, hãy đảm bảo bạn hiểu các điều kiện tiên quyết.

## Điều kiện tiên quyết

Để làm theo hướng dẫn này, hãy đảm bảo bạn có:

### Thư viện và phiên bản cần thiết:
- **GroupDocs.Conversion cho .NET** (Phiên bản 25.3.0)
- **StackExchange.Redis** thư viện cho các hoạt động Redis
- Một phiên bản đang chạy của máy chủ Redis (ví dụ: `192.168.222.4:6379`)

### Yêu cầu thiết lập môi trường:
- Visual Studio hoặc một IDE tương thích khác hỗ trợ C#
- Đã cài đặt .NET Framework hoặc .NET Core

### Điều kiện tiên quyết về kiến thức:
- Hiểu biết cơ bản về lập trình C# và .NET
- Làm quen với Redis như một giải pháp lưu trữ đệm
- Kinh nghiệm với các quy trình chuyển đổi tài liệu trong các ứng dụng phần mềm

## Thiết lập GroupDocs.Conversion cho .NET

Để bắt đầu sử dụng GroupDocs.Conversion, hãy cài đặt nó thông qua NuGet Package Manager Console hoặc .NET CLI.

**Bảng điều khiển quản lý gói NuGet:**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**.NETCLI:**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### Các bước xin cấp phép:
- **Dùng thử miễn phí:** Kiểm tra các tính năng và chức năng với giấy phép tạm thời.
- **Giấy phép tạm thời:** Có thể được đánh giá mở rộng mà không có giới hạn.
- **Mua:** Để sử dụng lâu dài, hãy cân nhắc mua giấy phép đầy đủ.

Sau khi cài đặt, hãy khởi tạo GroupDocs.Conversion trong ứng dụng C# của bạn:

```csharp
using GroupDocs.Conversion;
```

## Hướng dẫn thực hiện

### Triển khai bộ nhớ đệm tùy chỉnh bằng Redis

Phần này trình bày cách tạo bộ nhớ đệm tùy chỉnh bằng Redis cho các hoạt động kết xuất tài liệu nhằm tăng tốc độ và hiệu quả chuyển đổi.

#### Tổng quan
Chúng tôi sẽ triển khai cơ chế lưu trữ đệm dựa trên Redis để lưu trữ các tài liệu đã kết xuất, tránh xử lý trùng lặp và tăng tốc đáng kể thời gian chuyển đổi.

##### Bước 1: Xác định lớp RedisCache

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using StackExchange.Redis;

public class RedisCache : IDisposable
{
    private readonly string _cacheKeyPrefix;
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _db;
    private readonly string _host = "192.168.222.4:6379";

    public RedisCache(string cacheKeyPrefix)
    {
        _cacheKeyPrefix = cacheKeyPrefix;
        _redis = ConnectionMultiplexer.Connect(_host);
        _db = _redis.GetDatabase();
    }

    // Đặt dữ liệu trong bộ nhớ đệm bằng một khóa cụ thể
    public void Set(string key, object data)
    {
        if (data == null) return;

        string prefixedKey = GetPrefixedKey(key);
        using (MemoryStream stream = new MemoryStream())
        {
            ((Stream)data).CopyTo(stream);
            _db.StringSet(prefixedKey, RedisValue.CreateFrom(stream));
        }
    }

    // Cố gắng lấy dữ liệu từ bộ nhớ đệm bằng cách sử dụng khóa
    public bool TryGetValue(string key, out object value)
    {
        var prefixedKey = GetPrefixedKey(key);
        var redisValue = _db.StringGet(prefixedKey);

        if (redisValue.HasValue)
        {
            value = new MemoryStream(redisValue);
            return true;
        }

        value = default;
        return false;
    }

    // Truy xuất tất cả các khóa khớp với mẫu bộ lọc từ bộ nhớ đệm
    public IEnumerable<string> GetKeys(string filter)
    {
        return _redis.GetServer(_host).Keys(pattern: $"*{filter}*")
            .Select(x => x.ToString().Replace(_cacheKeyPrefix, string.Empty))
            .Where(x => x.StartsWith(filter, StringComparison.InvariantCultureIgnoreCase))
            .ToList();
    }

    private string GetPrefixedKey(string key) => $"{_cacheKeyPrefix}{key}";

    public void Dispose()
    {
        _redis.Dispose();
    }
}
```

**Giải thích:**
- **Thiết lập phương pháp:** Lưu dữ liệu trong Redis bằng khóa bộ nhớ đệm cụ thể.
- **Phương thức TryGetValue:** Truy xuất dữ liệu được lưu trong bộ nhớ đệm, nếu có.
- **Phương thức GetKeys:** Lấy các khóa khớp với một mẫu đã chỉ định.

##### Bước 2: Triển khai chuyển đổi tài liệu với Custom Cache

```csharp
using System;
using System.Diagnostics;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Caching;

public class HowToUseCustomCacheImplementation
{
    public static void Run()
    {
        string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
        
        RedisCache cache = new RedisCache("sample_");
        Func<ConverterSettings> settingsFactory = () => new ConverterSettings
        {
            Cache = cache
        };

        using (Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF", settingsFactory))
        {
            PdfConvertOptions options = new PdfConvertOptions();
            
            Stopwatch stopWatch = Stopwatch.StartNew();
            converter.Convert($"{outputDirectory}/converted.pdf", options);
            stopWatch.Stop();

            stopWatch.Restart();
            converter.Convert($"{outputDirectory}/converted-1.pdf", options);
            stopWatch.Stop();
        }
    }
}
```

**Giải thích:**
- **Khởi tạo RedisCache:** Thiết lập bộ nhớ đệm với tiền tố khóa.
- **Cài đặt bộ chuyển đổi:** Tích hợp bộ nhớ đệm tùy chỉnh vào cài đặt GroupDocs.Conversion.
- **Quá trình chuyển đổi:** Đo lường và chứng minh cải thiện hiệu suất bằng cách lưu trữ kết quả chuyển đổi.

## Ứng dụng thực tế

### Các trường hợp sử dụng:
1. **Hệ thống quản lý tài liệu doanh nghiệp:** Cải thiện tốc độ kết xuất tài liệu cho các ứng dụng quy mô lớn.
2. **Dịch vụ web:** Cải thiện thời gian phản hồi cho các API xử lý các chuyển đổi PDF thường xuyên.
3. **Mạng phân phối nội dung (CDN):** Lưu trữ và chuyển giao các tài liệu đã chuyển đổi trước một cách nhanh chóng.
4. **Nền tảng phân tích dữ liệu:** Tăng tốc quá trình tạo báo cáo liên quan đến việc chuyển đổi dữ liệu sang định dạng trực quan.
5. **Các trang web thương mại điện tử:** Tối ưu hóa quá trình xử lý danh mục sản phẩm bằng cách lưu trữ hình ảnh đã chuyển đổi hoặc bản xem trước tài liệu.

### Khả năng tích hợp:
- Kết hợp với các nền tảng .NET khác như ASP.NET Core cho các ứng dụng web.
- Tích hợp vào kiến trúc dịch vụ vi mô bằng Docker và Kubernetes.

## Cân nhắc về hiệu suất

Để tối ưu hóa hiệu suất, hãy cân nhắc những điều sau:

- **Quản lý kích thước bộ nhớ đệm:** Xóa các mục cũ thường xuyên để tránh tràn bộ nhớ.
- **Kết nối gộp:** Sử dụng kết nối nhóm trong Redis để quản lý tài nguyên hiệu quả.
- **Tuần tự hóa dữ liệu:** Lựa chọn định dạng tuần tự hóa hiệu quả (ví dụ: Bộ đệm giao thức) để lưu trữ dữ liệu trong Redis.

## Phần kết luận

Việc triển khai bộ đệm Redis tùy chỉnh với GroupDocs.Conversion cho .NET có thể tăng đáng kể hiệu suất chuyển đổi tài liệu của ứng dụng. Hướng dẫn này cung cấp hướng dẫn từng bước về cách thiết lập và sử dụng các công cụ mạnh mẽ này để tối ưu hóa hoạt động.

**Các bước tiếp theo:**
- Thử nghiệm với các cấu hình bộ nhớ đệm khác nhau.
- Khám phá các tính năng nâng cao của GroupDocs.Conversion cho các trường hợp sử dụng phức tạp hơn.

Bạn đã sẵn sàng nâng cao hiệu quả ứng dụng của mình chưa? Hãy bắt đầu triển khai giải pháp này ngay hôm nay!

## Phần Câu hỏi thường gặp

1. **Làm thế nào để cài đặt Redis trên máy cục bộ của tôi?**
   - Làm theo hướng dẫn cài đặt Redis chính thức cho hệ điều hành của bạn: [Tải xuống Redis](https://redis.io/download).
2. **Lợi ích của việc sử dụng bộ nhớ đệm tùy chỉnh với GroupDocs.Conversion là gì?**
   - Giảm xử lý dư thừa, tăng tốc thời gian chuyển đổi và giảm mức sử dụng tài nguyên.
3. **Tôi có thể sử dụng thiết lập này trong môi trường đám mây không?**
   - Chắc chắn rồi! Đảm bảo rằng phiên bản Redis của bạn có thể truy cập được từ môi trường ứng dụng của bạn.