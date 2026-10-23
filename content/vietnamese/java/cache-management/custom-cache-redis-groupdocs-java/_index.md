---
date: '2026-10-21'
description: Tìm hiểu cách tạo cache key Java và tích hợp Redis với GroupDocs.Conversion
  để tăng hiệu năng render, giảm thời gian chuyển đổi, và cấu hình TTL trong một dự
  án Java đơn giản.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Tạo cache key Java trong hướng dẫn từng bước này, cho thấy cách tích
  hợp Redis với GroupDocs.Conversion để cache byte tài liệu, tăng hiệu năng render
  và giảm thời gian chuyển đổi. Cấu hình TTL và đo lường mức tăng tốc.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Tạo cache key Java – cache tài liệu với Redis và GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  headline: Create cache key Java – cache docs with Redis and GroupDocs
  type: TechArticle
- description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  name: Create cache key Java – cache docs with Redis and GroupDocs
  steps:
  - name: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
    text: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
  - name: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
    text: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
  - name: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
    text: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
  - name: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
    text: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
  - name: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
    text: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
  type: HowTo
- questions:
  - answer: Absolutely. The same caching pattern works for DOCX, HTML, images, and
      more – just change the `ConvertOptions` type.
    question: Can I use this approach with other GroupDocs output formats?
  - answer: Combine the source file path, conversion options, and any version identifiers.
      This guarantees uniqueness per configuration.
    question: How do I choose a good cache key?
  - answer: Invalidate the cache manually (e.g., delete the key) or use a shorter
      TTL so stale data expires quickly.
    question: What if a document changes after it’s cached?
  - answer: No, but Redis offers low latency, built‑in TTL, and wide Java client support,
      making it a popular choice for this scenario.
    question: Is Redis the only option for caching?
  - answer: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived
      connections via Jedis.
    question: Does this increase memory usage on the application server?
  type: FAQPage
tags:
- create cache key java
- java redis cache
- groupdocs conversion
- document rendering
title: Tạo cache key Java – cache tài liệu trong Java với Redis
type: docs
url: /vi/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Tạo khóa cache Java – lưu trữ tài liệu trong Java với Redis

Trong các ứng dụng web hiện đại, việc phục vụ cùng một tài liệu đã chuyển đổi liên tục có thể lãng phí vòng CPU và làm tăng thời gian phản hồi. **Tạo khóa cache trong Java** cho phép bạn lưu trữ kết quả chuyển đổi một lần và truy xuất ngay lập tức trong các yêu cầu tiếp theo. Hướng dẫn này cho bạn cách tích hợp Redis vào quy trình làm việc của GroupDocs.Conversion, tạo ra các khóa cache đáng tin cậy, cấu hình TTL và đo lường những cải thiện hiệu năng mà bạn có thể mong đợi.

## Câu trả lời nhanh
- **Nội dung của hướng dẫn này là gì?** Một hướng dẫn đầy đủ về caching java redis tích hợp Redis với GroupDocs.Conversion.  
- **Tại sao lại sử dụng Redis?** Nó cung cấp độ trễ dưới một mili giây, hỗ trợ hết hạn TTL, và mở rộng theo chiều ngang trên nhiều instance của ứng dụng.  
- **Tôi có cần giấy phép GroupDocs không?** Giấy phép dùng thử hoặc tạm thời là đủ cho việc thử nghiệm; giấy phép đầy đủ cần thiết cho triển khai sản xuất.  
- **Các bước chính là gì?** Thêm các phụ thuộc Maven, cấu hình một `JedisPool`, xây dựng các phương thức trợ giúp cache, và tích hợp cache vào quy trình chuyển đổi.  
- **Phiên bản Java nào được hỗ trợ?** Java 8+ (tương thích với các phiên bản mới nhất của GroupDocs.Conversion).

## Caching tài liệu với Redis là gì?
Caching tài liệu với Redis có nghĩa là lưu trữ đầu ra nhị phân của một quá trình chuyển đổi (ví dụ, mảng byte PDF) trong Redis để các yêu cầu tương tự trong tương lai có thể truy xuất các byte đã được cache thay vì chạy lại engine chuyển đổi. Điều này loại bỏ công việc CPU dư thừa, giảm băng thông mạng và mang lại trải nghiệm người dùng mượt mà hơn.

## Tại sao triển khai cache Redis trong Java?
Việc tải một tài liệu một lần, lưu trữ kết quả và phục vụ ngay lập tức khi có các yêu cầu lặp lại có thể **giảm thời gian chuyển đổi tới 90 %** cho các tệp được truy cập thường xuyên, **giảm chi phí hạ tầng** bằng cách giảm sử dụng CPU, và **cung cấp một nguồn dữ liệu duy nhất** cho tất cả các node ứng dụng trong môi trường cụm. Redis có thể xử lý hơn 200 k thao tác mỗi giây trên một node duy nhất, đảm bảo tra cứu dưới một mili giây.

## Yêu cầu trước
- **GroupDocs.Conversion** – phiên bản 25.2 hoặc mới hơn (hỗ trợ **120+** định dạng đầu vào và đầu ra).  
- **Jedis** (client Redis chính thức cho Java).  
- Một instance Redis đang chạy (phát triển cục bộ có thể sử dụng mặc định `localhost:6379`).  
- Maven để quản lý phụ thuộc.  
- Hiểu biết cơ bản về xử lý ngoại lệ Java và các luồng I/O.

## Cài đặt GroupDocs.Conversion cho Java

`GroupDocs.Conversion` là một thư viện Java chuyển đổi và render tài liệu sang nhiều định dạng, tự động xử lý bảo toàn bố cục, nhúng phông chữ và trích xuất hình ảnh.

Thêm repository GroupDocs và phụ thuộc vào `pom.xml` của bạn:

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2.0</version>
    </dependency>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>4.2.3</version>
    </dependency>
</dependencies>
```

### Nhận giấy phép
Bạn có thể bắt đầu với **Free Trial**, yêu cầu **Temporary License** để đánh giá, hoặc mua **License** đầy đủ cho môi trường sản xuất.

Khởi tạo GroupDocs.Conversion trong mã Java của bạn:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Hướng dẫn triển khai

### Tạo cache tùy chỉnh bằng Redis

#### Tổng quan
Cache Redis tùy chỉnh lưu trữ các byte tài liệu đã render, cho phép truy xuất ngay lập tức khi có các yêu cầu lặp lại.

#### Cài đặt JedisPool
JedisPool là một pool các kết nối Redis có thể tái sử dụng, an toàn với đa luồng, giúp giảm tải socket và cải thiện thông lượng.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Lưu và truy xuất dữ liệu cache
Các phương thức trợ giúp dưới đây sẽ serialize một mảng byte thành chuỗi Base64 để lưu trữ an toàn và truy xuất lại thành mảng byte.

```java
import java.util.Base64;
import redis.clients.jedis.Jedis;

public class RedisCacheHelper {

    private final JedisPool pool;
    private final int ttlSeconds; // time‑to‑live for cached entries

    public RedisCacheHelper(JedisPool pool, int ttlSeconds) {
        this.pool = pool;
        this.ttlSeconds = ttlSeconds;
    }

    public void put(String key, byte[] data) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = Base64.getEncoder().encodeToString(data);
            jedis.setex(key, ttlSeconds, encoded); // configure redis ttl
        }
    }

    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = jedis.get(key);
            return encoded != null ? Base64.getDecoder().decode(encoded) : null;
        }
    }
}
```

#### Tích hợp với GroupDocs.Conversion
Bây giờ kết nối cache vào quy trình chuyển đổi. Phương thức sẽ kiểm tra cache trước; nếu không có, nó thực hiện chuyển đổi, lưu kết quả và trả về các byte.

```java
import com.groupdocs.conversion.options.convertoptions.PdfConvertOptions;

public class DocumentService {

    private final ConversionApi conversionApi;
    private final RedisCacheHelper cacheHelper;

    public DocumentService(ConversionApi conversionApi, RedisCacheHelper cacheHelper) {
        this.conversionApi = conversionApi;
        this.cacheHelper = cacheHelper;
    }

    public byte[] convertToPdf(String sourcePath, PdfConvertOptions options) throws Exception {
        // Build a deterministic cache key
        String cacheKey = "pdf:" + sourcePath + ":" + options.hashCode();

        // Attempt to fetch from Redis
        byte[] cached = cacheHelper.get(cacheKey);
        if (cached != null) {
            // Cache hit – return stored bytes
            return cached;
        }

        // Cache miss – perform conversion
        byte[] result = conversionApi.convert(sourcePath, options).toByteArray();

        // Store result for future calls
        cacheHelper.put(cacheKey, result);
        return result;
    }
}
```

## Cách tạo khóa cache Java cho caching Redis?
Tạo một khóa xác định bằng cách nối đường dẫn tệp nguồn, các giá trị `ConvertOptions` đã chọn và một thẻ phiên bản tùy chọn, sau đó hash chuỗi bằng SHA‑256. Khóa này duy nhất xác định mỗi cấu hình chuyển đổi, đảm bảo các yêu cầu giống nhau sẽ truy cập cache trong khi các tùy chọn khác tạo ra các mục riêng biệt.

Lớp `ConversionApi` là thành phần cốt lõi trong GroupDocs.Conversion thực hiện chuyển đổi tài liệu. Bạn có thể tạo một khóa cache, tra cứu nó trong Redis, và chỉ gọi `ConversionApi.convert` khi khóa không tồn tại, giảm đáng kể thời gian chuyển đổi và tải máy chủ.

## Cách triển khai caching Redis trong Java?
`ConversionApi` là lớp chính trong GroupDocs.Conversion thực hiện các thao tác chuyển đổi tài liệu. Tải tài liệu nguồn của bạn, tạo một khóa cache xác định, tra cứu nó trong Redis, và chỉ gọi `ConversionApi` khi khóa không tồn tại. Mô hình này đảm bảo mỗi chuyển đổi duy nhất chỉ được thực hiện một lần, sau đó được phục vụ từ cache trong thời gian TTL đã cấu hình.

## Mẹo khắc phục sự cố
- Xác minh máy chủ Redis có thể truy cập được (`redis-cli ping` nên trả về `PONG`).  
- Đảm bảo host và port của `JedisPool` khớp với triển khai Redis của bạn.  
- Bao quanh các lời gọi cache bằng khối try‑catch để xử lý các sự cố kết nối mà không làm gián đoạn quy trình chuyển đổi.  
- Giám sát bộ nhớ Redis (`INFO memory`) và thiết lập các chính sách `maxmemory` (ví dụ, `volatile-lru`) để xóa các mục cũ một cách nhẹ nhàng.  
- Nếu gặp `OutOfMemoryError` trên JVM, tăng kích thước heap hoặc bật `-XX:+UseCompressedOops`.

## Ứng dụng thực tiễn

1. **Cổng thông tin có lưu lượng cao** – Phục vụ các PDF được yêu cầu thường xuyên (catalogs, whitepapers) ngay lập tức.  
2. **Enterprise DMS** – Giảm tải khi người dùng liên tục xem cùng một hợp đồng hoặc tài liệu chính sách.  
3. **Thương mại điện tử** – Cache các hoá đơn hoặc catalog sản phẩm đã tạo để tăng tốc quá trình thanh toán.  
4. **Nền tảng học tập** – Cung cấp tài liệu giảng dạy và e‑book mà không cần render lại cho mỗi yêu cầu của sinh viên.  
5. **Dịch vụ pháp lý** – Tăng tốc phân phối hồ sơ vụ án trong khi giữ chi phí lưu trữ thấp.

## Các cân nhắc về hiệu năng

- **Tinh chỉnh Redis** – Điều chỉnh `maxmemory`, chọn chính sách loại bỏ như `allkeys-lru`, và đặt các giá trị `timeout` phù hợp dựa trên mô hình lưu lượng của bạn.  
- **Theo dõi tỷ lệ hit/miss của cache** – Sử dụng `INFO stats` hoặc các bộ đếm `keyspace_hits` / `keyspace_misses` của Redis để tinh chỉnh TTL.  
- **Kích thước heap JVM** – Đảm bảo heap có thể chứa các bộ đệm của GroupDocs; quy tắc chung là 1 GB heap cho mỗi 100 MB tải chuyển đổi đồng thời.  
- **Chuyển đổi hàng loạt** – Khi chuyển đổi nhiều tệp, tái sử dụng một instance `Jedis` duy nhất cho mỗi luồng để giảm thiểu việc tạo socket.

## Câu hỏi thường gặp

**Q: Bạn có thể sử dụng cách tiếp cận này với các định dạng đầu ra khác của GroupDocs không?**  
A: Chắc chắn. Mẫu cache này hoạt động cho DOCX, HTML, hình ảnh và hơn thế nữa – chỉ cần thay đổi kiểu `ConvertOptions`.

**Q: Làm sao để chọn một khóa cache tốt?**  
A: Kết hợp đường dẫn tệp nguồn, các tùy chọn chuyển đổi và bất kỳ định danh phiên bản nào. Điều này đảm bảo tính duy nhất cho mỗi cấu hình.

**Q: Nếu tài liệu thay đổi sau khi đã được cache thì sao?**  
A: Hủy bỏ cache thủ công (ví dụ, xóa khóa) hoặc sử dụng TTL ngắn hơn để dữ liệu cũ hết hạn nhanh chóng.

**Q: Redis có phải là lựa chọn duy nhất cho caching không?**  
A: Không, nhưng Redis cung cấp độ trễ thấp, TTL tích hợp và hỗ trợ rộng rãi các client Java, khiến nó trở thành lựa chọn phổ biến cho kịch bản này.

**Q: Điều này có làm tăng việc sử dụng bộ nhớ trên máy chủ ứng dụng không?**  
A: Tối thiểu. Công việc nặng được Redis thực hiện; ứng dụng chỉ giữ các kết nối ngắn hạn qua Jedis.

## Kết luận
Bạn giờ đã có một hướng dẫn **java redis caching** đầy đủ, cho thấy cách cache tài liệu bằng Redis và GroupDocs.Conversion. Bằng cách lưu trữ đầu ra đã render trong Redis, bạn sẽ **tăng hiệu năng render**, **giảm thời gian chuyển đổi**, và cung cấp trải nghiệm mượt mà hơn cho người dùng cuối. Thử nghiệm với các giá trị TTL khác nhau, giám sát các chỉ số cache, và mở rộng mẫu này sang các định dạng tài liệu khác khi ứng dụng của bạn phát triển.

---

**Cập nhật lần cuối:** 2026-10-21  
**Kiểm tra với:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Tác giả:** GroupDocs

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

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class DocumentConversion {
    public static void main(String[] args) {
        // Initialize the Converter with a document path
        Converter converter = new Converter("input.docx");
        
        // Set up conversion options for PDF
        PdfConvertOptions options = new PdfConvertOptions();
        converter.convert("output.pdf", options);
    }
}
```

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

```java
import redis.clients.jedis.Jedis;

public class CacheManager {

    public static void storeDocument(String key, String documentContent) {
        try (Jedis jedis = jedisPool.getResource()) {
            // Set the content in Redis cache with an expiration time of one hour
            jedis.setex(key, 3600, documentContent);
        }
    }

    public static String retrieveDocument(String key) {
        try (Jedis jedis = jedisPool.getResource()) {
            return jedis.get(key); // Retrieve cached content if available
        }
    }
}
```

```java
public class DocumentConversion {

    public static void convertWithCache(String inputPath, String outputPath) {
        Converter converter = new Converter(inputPath);
        PdfConvertOptions options = new PdfConvertOptions();

        // Generate a cache key based on the document path and conversion settings
        String cacheKey = "doc:" + inputPath;

        // Check if the converted document is already cached
        String cachedDocument = CacheManager.retrieveDocument(cacheKey);

        if (cachedDocument != null) {
            System.out.println("Using cached version of the document.");
            // Save cached content to output file
            Files.write(Paths.get(outputPath), cachedDocument.getBytes());
        } else {
            // Perform conversion and cache the result
            converter.convert(output -> {
                String documentContent = new String(output.toByteArray());
                CacheManager.storeDocument(cacheKey, documentContent);
                Files.write(Paths.get(outputPath), output.toByteArray());
            }, options);
        }
    }

    public static void main(String[] args) {
        convertWithCache("input.docx", "output.pdf");
    }
}
```

## Hướng dẫn liên quan

- [Triển khai Cache Tùy chỉnh Java – Cache GroupDocs Conversion](/conversion/java/cache-management/)
- [Cách Sử dụng Cache Redis trong Java với GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Cách Cache Tập tin trong Java với GroupDocs.Conversion – Hướng dẫn toàn diện cho chuyển đổi tài liệu hiệu quả](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
