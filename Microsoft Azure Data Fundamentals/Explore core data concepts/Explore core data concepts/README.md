# Mục Lục

* [**Explore core data concepts**](#M01)
    - [Identify data formats](#M01.1)
      + [Structured data](#M01.1.1)
      + [Semi-structured data](#M01.1.2)
      + [Unstructured data](#M01.1.3)
    - [Identify data formats](#M01.2)
      + [Delimited text files](#M01.2.1)
      + [JavaScript Object Notation (JSON)](#M01.2.2)
      + [Extensible Markup Language (XML)](#M01.2.3)
      + [Binary Large Object (BLOB)](#M01.2.4)
      + [Optimized file formats](#M01.2.5)












<a name="M01"></a>
# [Explore core data concepts](https://learn.microsoft.com/en-us/training/modules/explore-core-data-concepts/)
<a name="M01.1"></a>
## Xác định định dạng dữ liệu (Identify data formats)
<a name="M01.1.1"></a>
### Dữ liệu có cấu trúc (Structured data)

Structured data là dữ liệu được tổ chức theo cấu trúc định sẵn và có thể được đọc và hiểu bởi máy tính và các chương trình phần mềm khác một cách dễ dàng. Các dữ liệu được sắp xếp theo các bảng, cột, hàng, trường, hoặc các đối tượng có liên quan khác, được xác định trước bởi một loại cấu trúc hoặc schema. Dữ liệu có cấu trúc này cho phép các ứng dụng phân tích, truy vấn, và xử lý dữ liệu một cách hiệu quả hơn.

Các ví dụ phổ biến về dữ liệu có cấu trúc bao gồm các bảng dữ liệu, ví dụ như các bảng trong cơ sở dữ liệu quan hệ, các tập tin Excel hoặc các tập tin CSV. Các bảng này có các cột dữ liệu rõ ràng, mỗi cột đại diện cho một trường dữ liệu cụ thể và mỗi hàng đại diện cho một bản ghi dữ liệu.

Dữ liệu có cấu trúc thường được sử dụng trong các ứng dụng doanh nghiệp để lưu trữ và quản lý thông tin liên quan đến khách hàng, sản phẩm, đơn hàng, thanh toán và nhiều loại thông tin khác. Nó cũng là định dạng phổ biến để trao đổi dữ liệu giữa các ứng dụng, máy chủ và hệ thống khác nhau bởi vì các ứng dụng có thể dễ dàng trích xuất và sử dụng thông tin từ dữ liệu có cấu trúc.

![image](https://user-images.githubusercontent.com/62134515/220317287-b613b3a4-d919-4b1c-8a6d-d45ce5c16b1b.png)




<a name="M01.1.2"></a>
### Dữ liệu bán cấu trúc (Semi-structured data)

Semi-structured data (dữ liệu bán cấu trúc) là dữ liệu không có cấu trúc hoàn toàn, tuy nhiên chúng vẫn chứa một số thông tin về cấu trúc của dữ liệu. Semi-structured data có thể được định dạng bằng các định dạng như XML, JSON, hoặc YAML, v.v. và thường được sử dụng để mô tả dữ liệu liên quan đến nội dung văn bản, đồ họa hoặc dữ liệu đa phương tiện.

Các ví dụ về semi-structured data bao gồm các tập tin log, các tập tin cấu hình, dữ liệu HTML, hoặc các tài liệu tóm tắt. Các loại dữ liệu này không theo một cấu trúc rõ ràng như dữ liệu có cấu trúc, nhưng vẫn chứa các thông tin quan trọng được đánh dấu bằng các thẻ hay nhãn.

Vì semi-structured data không có một cấu trúc đơn giản, việc truy xuất và xử lý dữ liệu thường đòi hỏi sự kết hợp giữa các phương pháp xử lý dữ liệu có cấu trúc và không có cấu trúc. Nhiều công nghệ và phương pháp đã được phát triển để xử lý semi-structured data, bao gồm các công nghệ Big Data, các công cụ đọc hiểu ngôn ngữ tự nhiên và các công cụ xử lý dữ liệu văn bản tự động.

```JSON
// Customer 1
{
  "firstName": "Joe",
  "lastName": "Jones",
  "address":
  {
    "streetAddress": "1 Main St.",
    "city": "New York",
    "state": "NY",
    "postalCode": "10099"
  },
  "contact":
  [
    {
      "type": "home",
      "number": "555 123-1234"
    },
    {
      "type": "email",
      "address": "joe@litware.com"
    }
  ]
}

// Customer 2
{
  "firstName": "Samir",
  "lastName": "Nadoy",
  "address":
  {
    "streetAddress": "123 Elm Pl.",
    "unit": "500",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98999"
  },
  "contact":
  [
    {
      "type": "email",
      "address": "samir@northwind.com"
    }
  ]
}
```



<a name="M01.1.3"></a>
### Dữ liệu không có cấu trúc (Unstructured data)

Unstructured data (dữ liệu không có cấu trúc) là loại dữ liệu không có bất kỳ cấu trúc hay định dạng cụ thể nào. Nó là một tập hợp các dữ liệu không đồng nhất, không theo quy tắc, không có định dạng chuẩn hoặc mô hình dữ liệu cụ thể. Unstructured data có thể bao gồm các tài liệu văn bản không định dạng, hình ảnh, video, âm thanh, email, tweet, blog, trang web, v.v.

Các ví dụ phổ biến về unstructured data bao gồm các tài liệu văn bản như email, tài liệu Word, tài liệu PDF, các bài blog và trang web, các tệp hình ảnh như JPEG, PNG, các tệp video như MP4, AVI, các tệp âm thanh như MP3, WAV, v.v.

Do không có cấu trúc cụ thể, việc xử lý unstructured data trở nên khó khăn và phức tạp. Tuy nhiên, các công nghệ mới như Machine Learning, Natural Language Processing, Computer Vision và Big Data Analytics đang được phát triển để giúp trích xuất và phân tích thông tin từ các nguồn dữ liệu không có cấu trúc này. Các ứng dụng của unstructured data rất rộng và đa dạng, bao gồm phân tích dữ liệu khách hàng, phân tích cảm xúc, phát hiện lỗi và sự cố, và các nhiệm vụ tự động hóa nhiều khác.

![image](https://user-images.githubusercontent.com/62134515/220317374-ab1f5b16-b47b-4ef0-bc53-6580bb1cbaca.png)






<a name="M01.2"></a>
## Explore file storage


<a name="M01.2.1"></a>
### Delimited text files

Delimited text files là một loại tệp văn bản được sử dụng để lưu trữ và truyền dữ liệu. Tệp văn bản này chứa dữ liệu được phân tách bởi một ký tự đặc biệt, thường là dấu phẩy (,) hoặc tab (\t). Khi dữ liệu được phân tách bằng ký tự này, nó có thể được dễ dàng đọc bởi các chương trình hoặc công cụ phân tích dữ liệu, chẳng hạn như các chương trình xử lý văn bản hoặc các chương trình tính toán.

Delimited text files thường được sử dụng để lưu trữ các bảng dữ liệu hoặc danh sách dữ liệu. Ví dụ, một danh sách khách hàng có thể được lưu trữ trong một tệp văn bản được phân tách bằng dấu phẩy, trong đó mỗi hàng đại diện cho một khách hàng và các cột chứa các thông tin khác nhau về khách hàng, chẳng hạn như tên, địa chỉ, số điện thoại, v.v.

Ví dụ sau hiển thị dữ liệu khách hàng ở định dạng được phân cách bằng dấu phẩy:
```
FirstName,LastName,Email
Joe,Jones,joe@litware.com
Samir,Nadoy,samir@northwind.com
```





<a name="M01.2.2"></a>
### JavaScript Object Notation (JSON)

JavaScript Object Notation (JSON) là một định dạng dữ liệu dựa trên văn bản, được sử dụng để truyền tải dữ liệu giữa các ứng dụng web và lưu trữ dữ liệu trong cơ sở dữ liệu. JSON sử dụng cú pháp đơn giản, dễ hiểu và có khả năng đọc và ghi trên nhiều ngôn ngữ lập trình khác nhau.

JSON sử dụng các cặp key-value để đại diện cho dữ liệu. Một key trong JSON tương ứng với một tên trường hoặc thuộc tính, còn giá trị value tương ứng với giá trị của trường hoặc thuộc tính đó. Các cặp key-value trong JSON được phân tách bởi dấu phẩy và được bao quanh bởi cặp dấu ngoặc nhọn {}.

Ví dụ, một đối tượng JSON đại diện cho thông tin một người có thể được biểu diễn như sau:

```json
{
  "name": "John Smith",
  "age": 30,
  "city": "New York"
}
```
Trong ví dụ này, "name", "age" và "city" là các key, tương ứng với tên, tuổi và thành phố của người, và giá trị tương ứng là "John Smith", 30 và "New York".





<a name="M01.2.3"></a>
### DExtensible Markup Language (XML)

Extensible Markup Language (XML) là một ngôn ngữ đánh dấu được sử dụng để lưu trữ và truyền tải dữ liệu giữa các ứng dụng web, đặc biệt là các ứng dụng web liên quan đến việc trao đổi dữ liệu. XML được sử dụng rộng rãi trong các ứng dụng web như các trang web, các dịch vụ web, và các cơ sở dữ liệu trên web.

XML sử dụng cú pháp đánh dấu để biểu diễn dữ liệu. Mỗi phần tử (element) trong XML được bao quanh bởi cặp thẻ mở và thẻ đóng, và có thể chứa các thuộc tính (attributes) và giá trị (value) tương ứng. Các phần tử trong XML có thể được lồng nhau để biểu diễn cấu trúc phức tạp hơn.

Ví dụ, một tài liệu XML đại diện cho thông tin một người có thể được biểu diễn như sau:

```php
<person>
  <name>John Smith</name>
  <age>30</age>
  <city>New York</city>
</person>
```
Trong ví dụ này, "person" là một phần tử chính, tương ứng với thông tin về một người. "name", "age" và "city" là các phần tử con của phần tử "person", tương ứng với tên, tuổi và thành phố của người, và giá trị tương ứng được chứa trong các thẻ tương ứng. Các phần tử trong XML có thể có các thuộc tính để cung cấp thêm thông tin về phần tử, chẳng hạn như sau:
```php
<person id="12345">
  <name>John Smith</name>
  <age>30</age>
  <city>New York</city>
</person>
```
Trong ví dụ này, thuộc tính "id" cung cấp thông tin về ID của người tương ứng.


<a name="M01.2.4"></a>
### Binary Large Object (BLOB)

Binary Large Object (BLOB) là một kiểu dữ liệu được sử dụng để lưu trữ các đối tượng nhị phân lớn trong cơ sở dữ liệu. BLOB thường được sử dụng để lưu trữ các tệp ảnh, âm thanh, video và các loại tệp khác trong cơ sở dữ liệu.

Dữ liệu BLOB thường được lưu trữ dưới dạng một mảng nhị phân lớn, không được mã hóa hoặc chuyển đổi sang định dạng văn bản. Khi cần truy xuất dữ liệu BLOB, các ứng dụng sẽ yêu cầu cơ sở dữ liệu trả về các mảng nhị phân này và sau đó xử lý các dữ liệu nhị phân để hiển thị các tệp đính kèm.

Ví dụ, nếu bạn lưu trữ một hình ảnh JPEG trong một cơ sở dữ liệu dưới dạng BLOB, thì dữ liệu của hình ảnh đó sẽ được lưu trữ dưới dạng một chuỗi các số nhị phân đại diện cho các byte trong tệp hình ảnh đó. Khi cần truy xuất hình ảnh, ứng dụng sẽ lấy các số nhị phân này và chuyển đổi chúng trở lại thành định dạng JPEG để hiển thị hình ảnh đó.



<a name="M01.2.5"></a>
### Optimized file formats

Các định dạng tệp đọc được bởi con người cho dữ liệu có cấu trúc và bán cấu trúc có thể hữu ích, tuy nhiên chúng thường không được tối ưu hóa cho không gian lưu trữ hoặc xử lý. Với thời gian, một số định dạng tệp chuyên dụng cho phép nén, chỉ mục và lưu trữ và xử lý hiệu quả đã được phát triển.

Một số định dạng tệp tối ưu hóa phổ biến mà bạn có thể thấy bao gồm Avro, ORC và Parquet:

- Avro là định dạng dữ liệu dựa trên hàng. Nó được tạo ra bởi Apache. Mỗi bản ghi chứa một tiêu đề mô tả cấu trúc dữ liệu trong bản ghi. Tiêu đề này được lưu trữ dưới dạng JSON. Dữ liệu được lưu trữ dưới dạng thông tin nhị phân. Một ứng dụng sử dụng thông tin trong tiêu đề để phân tích dữ liệu nhị phân và trích xuất các trường nó chứa. Avro là định dạng tốt để nén dữ liệu và giảm thiểu yêu cầu lưu trữ và băng thông mạng.
- ORC (Optimized Row Columnar format) tổ chức dữ liệu thành các cột thay vì các hàng. Nó được phát triển bởi HortonWorks để tối ưu hóa hoạt động đọc và ghi trong Apache Hive (Hive là hệ thống kho dữ liệu hỗ trợ tóm tắt dữ liệu và truy vấn nhanh chóng trên các tập dữ liệu lớn). Một tệp ORC chứa các vạch dữ liệu. Mỗi vạch chứa dữ liệu cho một cột hoặc tập hợp các cột. Một vạch chứa một chỉ mục vào các hàng trong vạch, dữ liệu cho mỗi hàng và một chân trang chứa thông tin thống kê (số lượng, tổng, max, min, v.v.) cho mỗi cột.
- Parquet là một định dạng dữ liệu theo cột khác. Nó được tạo bởi Cloudera và Twitter. Một tệp Parquet chứa các nhóm hàng. Dữ liệu cho mỗi cột được lưu trữ cùng nhau trong cùng một nhóm hàng. Mỗi nhóm hàng chứa một hoặc nhiều mảnh dữ liệu. Một tệp Parquet bao gồm siêu dữ liệu mô tả tập hợp các hàng được tìm thấy trong mỗi mảnh. Một ứng dụng có thể sử dụng siêu dữ liệu này để nhanh chóng xác định mảnh chính xác cho một tập hợp các hàng nhất định và lấy dữ liệu trong các cột được chỉ định cho các hàng này. Parquet chuyên về việc lưu trữ và xử lý các loại dữ liệu lồng nhau một cách hiệu quả. Nó hỗ trợ các kế hoạch nén và mã hóa rất hiệu quả.



















