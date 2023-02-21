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





<a name="M01.2.2"></a>
### JavaScript Object Notation (JSON)



<a name="M01.2.3"></a>
### DExtensible Markup Language (XML)





<a name="M01.2.4"></a>
### Binary Large Object (BLOB)





<a name="M01.2.5"></a>
### Optimized file formats
























