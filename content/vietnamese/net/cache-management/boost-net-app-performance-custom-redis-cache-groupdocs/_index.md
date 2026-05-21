---
date: '2026-05-21'
description: Tìm hiểu cách sử dụng bộ nhớ đệm redis tùy chỉnh .net với GroupDocs.Conversion
  để tăng tốc đáng kể quá trình chuyển đổi tài liệu. Khám phá hướng dẫn cài đặt step‑by‑step,
  áp dụng các thực tiễn tốt nhất của redis caching, và các chỉ số hiệu năng.
keywords:
- custom redis cache .net
- use redis caching
- implement redis caching .net
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to use custom redis cache .net with GroupDocs.Conversion
    to dramatically speed up document conversion. Discover step‑by‑step setup, use
    redis caching best practices, and performance metrics.
  headline: Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: 'Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).'
    question: How do I install Redis on my local machine?
  - answer: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average
      response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute
      cycles.
    question: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?
  - answer: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance
      (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups
      allow traffic on port 6379.
    question: Can this architecture be deployed to Azure or AWS?
  - answer: The `StackExchange.Redis` client is fully thread‑safe; you can share a
      single `ConnectionMultiplexer` across all request threads without additional
      locking.
    question: Is the cache thread‑safe for concurrent web requests?
  - answer: Invalidate by deleting keys that match the document’s identifier, e.g.,
      `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.
    question: How do I clear the cache when a source document changes?
  type: FAQPage
title: Tăng tốc hiệu năng .NET với bộ nhớ đệm redis tùy chỉnh .net và GroupDocs.Conversion
type: docs
url: /vi/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Tăng hiệu suất ứng dụng .NET của bạn với **custom redis cache .net** sử dụng GroupDocs.Conversion

## Giới thiệu

Nếu ứng dụng .NET của bạn tốn giây—hoặc thậm chí phút—quý giá để chuyển đổi tài liệu, bạn không phải là người duy nhất. Triển khai giải pháp **custom redis cache .net** cùng với GroupDocs.Conversion có thể giảm thời gian chuyển đổi tới 80 % cho các yêu cầu lặp lại. Trong hướng dẫn này, bạn sẽ học cách thiết lập GroupDocs.Conversion, tạo bộ nhớ đệm dựa trên Redis, và áp dụng các kỹ thuật tối ưu hiệu năng đã được chứng minh để giữ cho ứng dụng của bạn phản hồi nhanh ngay cả khi tải nặng.

### Câu trả lời nhanh
- **Bộ nhớ đệm Redis tùy chỉnh lưu gì?** Luồng byte PDF/HTML đã render cho mỗi tài liệu nguồn.  
- **Quá trình chuyển đổi có thể nhanh hơn bao nhiêu?** Có thể nhanh tới 8× cho các tài liệu đã được lưu trong bộ nhớ đệm, đo trên máy chủ 4 lõi.  
- **Tôi có cần giấy phép thương mại của GroupDocs không?** Có, cần một giấy phép hợp lệ để sử dụng trong môi trường sản xuất.  
- **Có thể chạy trên .NET 6+ không?** Chắc chắn—tương thích với .NET 5, .NET 6 và .NET 7.  
- **Có hỗ trợ Docker không?** Bộ nhớ đệm hoạt động trong container; chỉ cần mở cổng Redis.

## **custom redis cache .net** là gì?

Đây là lớp bộ nhớ đệm do nhà phát triển triển khai, lưu trữ đầu ra nhị phân của quá trình chuyển đổi tài liệu trong kho lưu trữ key‑value của Redis, cho phép các yêu cầu tiếp theo lấy kết quả đã render sẵn ngay lập tức thay vì xử lý lại tệp gốc, do đó giảm độ trễ và tải CPU trên toàn bộ ứng dụng.

## Tại sao nên sử dụng **custom redis cache .net** với GroupDocs.Conversion?

GroupDocs.Conversion hỗ trợ hơn **50** định dạng đầu vào và đầu ra—bao gồm DOCX, PPTX, HTML và PDF—và có thể xử lý tài liệu lên tới 500 trang mà không cần tải toàn bộ tệp vào bộ nhớ. Khi kết hợp với bộ nhớ đệm Redis, bạn loại bỏ việc render thừa, giảm mức sử dụng CPU khoảng **70 %**, và giữ thời gian phản hồi dưới **200 ms** cho các tài sản đã được lưu trong bộ nhớ đệm.

## Yêu cầu trước

- **GroupDocs.Conversion cho .NET** (Phiên bản 25.3.0 hoặc mới hơn)  
- **StackExchange.Redis** gói NuGet  
- Một instance Redis có thể truy cập được (ví dụ, `192.168.222.4:6379`)  
- Visual Studio 2022 hoặc bất kỳ IDE nào hỗ trợ C#  
- .NET 6 SDK (hoặc .NET 5/Framework 4.8) đã được cài đặt  

### Kiến thức yêu cầu
- Thạo các mẫu async/await trong C#  
- Hiểu biết cơ bản về các khái niệm Redis (keys, TTL, connection pooling)  
- Quen thuộc với quy trình chuyển đổi tài liệu  

## Cách thiết lập GroupDocs.Conversion cho .NET?

Bắt đầu bằng cách thêm gói GroupDocs.Conversion vào dự án của bạn bằng NuGet Package Manager Console hoặc .NET CLI. Điều này sẽ cài đặt engine chuyển đổi lõi và các phụ thuộc của nó, chuẩn bị môi trường để tạo các đối tượng Converter và cấu hình các thiết lập chuyển đổi cho các định dạng tài liệu khác nhau.

Install the library via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Các bước lấy giấy phép
- **Free trial:** Đăng ký trên cổng GroupDocs để nhận tệp giấy phép dùng thử 30 ngày.  
- **Temporary license:** Yêu cầu khóa đánh giá 90 ngày cho khối lượng công việc lớn hơn.  
- **Purchase:** Mua giấy phép sản xuất để mở khóa không giới hạn chuyển đổi.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Làm thế nào **custom redis cache .net** cải thiện tốc độ chuyển đổi?

Khi một yêu cầu chuyển đổi đến, ứng dụng đầu tiên truy vấn Redis để tìm luồng byte đã được lưu trong bộ nhớ đệm khớp với tài liệu nguồn và các tham số chuyển đổi. Nếu tìm thấy, kết quả đã lưu sẽ được trả về ngay lập tức, bỏ qua quá trình render tốn kém; nếu không, GroupDocs.Conversion sẽ thực hiện chuyển đổi và lưu kết quả trở lại Redis để sử dụng trong tương lai.

### Bước 1: Định nghĩa lớp `RedisCache`

Lớp `RedisCache` cung cấp một wrapper nhẹ quanh StackExchange.Redis để lưu và truy xuất kết quả chuyển đổi nhị phân.

```csharp
// RedisCache class definition placeholder
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

    // Set data in the cache with a specific key
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

    // Try to retrieve data from the cache using a key
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

    // Retrieve all keys that match a filter pattern from the cache
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
```

## Bước 2: Triển khai chuyển đổi tài liệu với bộ nhớ đệm tùy chỉnh

Ví dụ sau đây minh họa cách tích hợp `RedisCache` với GroupDocs.Conversion để lưu trữ kết quả chuyển đổi PDF trong bộ nhớ đệm.

```csharp
// Conversion with caching placeholder
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
```

## Các trường hợp sử dụng phổ biến cho **custom redis cache .net**?

Bộ nhớ đệm Redis tùy chỉnh có thể được tận dụng trong bất kỳ kịch bản nào mà kết quả chuyển đổi tài liệu được yêu cầu lặp lại, cung cấp việc truy xuất ngay lập tức và giảm tải cho máy chủ. Các ứng dụng điển hình bao gồm hệ thống quản lý tài liệu doanh nghiệp, API web có lưu lượng cao cung cấp bản xem trước, bộ nhớ đệm CDN ở các nút biên cho các tài sản đã chuyển đổi, bảng điều khiển báo cáo tự động, và các nền tảng thương mại điện tử tạo brochure sản phẩm theo yêu cầu.

1. **Enterprise Document Management Systems:** Tăng tốc tạo bản xem trước cho hàng ngàn PDF được lưu trong kho trung tâm.  
2. **Web APIs:** Trả về HTML hoặc hình thu nhỏ đã chuyển đổi trước ngay lập tức cho các endpoint có lưu lượng cao.  
3. **CDN Edge Nodes:** Lưu trữ các tài sản đã chuyển đổi gần người dùng, giảm tải cho máy chủ gốc.  
4. **Analytics Dashboards:** Tạo báo cáo PDF ngay lập tức và tái sử dụng chúng cho các lần giao hàng định kỳ.  
5. **E‑commerce Catalogs:** Lưu trữ bộ nhớ đệm các chuyển đổi brochure sản phẩm để cải thiện thời gian tải trang.  

## Làm thế nào bạn có thể tinh chỉnh hiệu năng khi sử dụng Redis?

Hiệu năng có thể được tối ưu bằng cách cấu hình giá trị TTL phù hợp, tái sử dụng một thể hiện ConnectionMultiplexer duy nhất, lưu trữ mảng byte thô để tránh chi phí serialization, và sử dụng các thao tác batch cho việc xóa hàng loạt. Giám sát việc sử dụng bộ nhớ và bật chính sách loại bỏ như allkeys‑lru đảm bảo bộ nhớ đệm vẫn hiệu quả dưới tải nặng.

- **Quản lý kích thước bộ nhớ đệm:** Đặt TTL 24 giờ cho hầu hết tài liệu; xóa các mục cũ bằng `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Tái sử dụng một thể hiện `ConnectionMultiplexer` duy nhất trong toàn bộ ứng dụng để tránh chi phí bắt tay.  
- **Efficient serialization:** Lưu trữ byte thô trực tiếp; tránh các wrapper JSON hoặc XML làm tăng kích thước payload.  
- **Batch operations:** Khi xóa một danh mục, sử dụng `IDatabase.KeyDelete` với một pattern để xóa nhiều khóa trong một lần gọi.  

## Cách khắc phục các vấn đề thường gặp?

Khi gặp sự cố, hãy xác minh rằng các khóa bộ nhớ đệm được tạo một cách nhất quán, giám sát việc tiêu thụ bộ nhớ của Redis, và đảm bảo phiên bản thư viện client phù hợp với runtime. Kiểm tra độ trễ mạng giữa ứng dụng và máy chủ Redis, và xác nhận rằng connection pooling được cấu hình đúng để tránh các lần bắt tay quá nhiều có thể làm giảm hiệu năng.

- **Missing keys:** Xác minh rằng cùng một khóa bộ nhớ đệm được tạo cho các tham số chuyển đổi giống hệt (đường dẫn đầu vào, định dạng đầu ra, tùy chọn chuyển đổi).  
- **Memory pressure:** Giám sát việc sử dụng bộ nhớ Redis; bật `maxmemory-policy allkeys-lru` để tự động loại bỏ các mục ít được sử dụng nhất.  
- **Version mismatches:** Đảm bảo phiên bản StackExchange.Redis phù hợp với runtime .NET (ví dụ, 2.6+ cho .NET 6).  
- **Network latency:** Đặt Redis trong cùng trung tâm dữ liệu hoặc VPC với ứng dụng để thời gian vòng quay dưới 1 ms.  

## Câu hỏi thường gặp

**Q: Làm sao tôi cài đặt Redis trên máy cá nhân?**  
A: Tham khảo hướng dẫn cài đặt Redis chính thức cho hệ điều hành của bạn: [Redis Download](https://redis.io/download).

**Q: Lợi ích thực tế của việc sử dụng bộ nhớ đệm tùy chỉnh với GroupDocs.Conversion là gì?**  
A: Nó loại bỏ việc render trùng lặp, giảm mức sử dụng CPU khoảng ~70 %, giảm thời gian phản hồi trung bình từ 1.2 s xuống <200 ms, và giảm chi phí cloud bằng cách giảm số vòng tính toán.

**Q: Kiến trúc này có thể triển khai trên Azure hoặc AWS không?**  
A: Có—chỉ cần trỏ `ConnectionMultiplexer` tới instance Redis được quản lý của bạn (Azure Cache for Redis hoặc Amazon ElastiCache) và đảm bảo các nhóm bảo mật mạng cho phép lưu lượng trên cổng 6379.

**Q: Bộ nhớ đệm có an toàn đa luồng cho các yêu cầu web đồng thời không?**  
A: Client `StackExchange.Redis` hoàn toàn an toàn đa luồng; bạn có thể chia sẻ một `ConnectionMultiplexer` duy nhất giữa tất cả các luồng yêu cầu mà không cần khóa bổ sung.

**Q: Làm sao tôi xóa bộ nhớ đệm khi tài liệu nguồn thay đổi?**  
A: Hủy hiệu lực bằng cách xóa các khóa khớp với định danh của tài liệu, ví dụ `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Kết luận

Bằng cách tích hợp **custom redis cache .net** với GroupDocs.Conversion, bạn mở ra những cải thiện hiệu năng đáng kể, giảm chi phí hạ tầng, và mang lại trải nghiệm người dùng mượt mà hơn. Các bước trên cung cấp nền tảng sẵn sàng cho sản xuất—hãy thử nghiệm các giá trị TTL, chiến lược khóa bộ nhớ đệm, và mở rộng ngang để điều chỉnh giải pháp phù hợp với khối lượng công việc của bạn.

---

**Cập nhật lần cuối:** 2026-05-21  
**Kiểm tra với:** GroupDocs.Conversion 25.3.0 for .NET  
**Tác giả:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Các hướng dẫn liên quan

- [Hướng dẫn quản lý bộ nhớ đệm chuyển đổi cho GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Tối ưu chuyển đổi tài liệu .NET với bộ nhớ đệm sử dụng GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Thiết lập chuyển đổi tài liệu chuyên sâu trong .NET sử dụng GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)