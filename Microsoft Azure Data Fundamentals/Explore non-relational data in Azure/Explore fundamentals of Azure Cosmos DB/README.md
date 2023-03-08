# Mục Lục

* [**Explore fundamentals of Azure Cosmos DB**](#M01)
    - [Describe Azure Cosmos DB](#M01.1)
      + [When to use Cosmos DB](#M01.1.1)
    - [Identify Azure Cosmos DB APIs](#M01.2)
      + [Azure Cosmos DB for NoSQL](#M01.2.1)
      + [Azure Cosmos DB for MongoDB](#M01.2.2)
      + [Azure Cosmos DB for PostgreSQL](#M01.2.3)
      + [Azure Cosmos DB for Table](#M01.2.4)
      + [Azure Cosmos DB for Apache Cassandra](#M01.2.5)
      + [Azure Cosmos DB for Apache Gremlin](#M01.2.6)
    - [Explore Azure Files](#M01.3)
    - [Explore Azure Tables](#M01.4)
    - [Exercise: Explore Azure Storage](#M01.5)
    - [Knowledge check](#M01.6)










<a name="M01"></a>
# [Explore fundamentals of Azure Cosmos DB](https://learn.microsoft.com/en-us/training/modules/explore-non-relational-data-stores-azure/)



<a name="M01.1"></a>
## Describe Azure Cosmos DB

![image](https://user-images.githubusercontent.com/62134515/222652171-7bb15027-99e7-49e3-88b8-22fbd093c735.png)

Azure Cosmos DB hỗ trợ nhiều giao diện lập trình ứng dụng (application programming interfaces - API) khác nhau cho phép nhà phát triển sử dụng cú pháp lập trình của nhiều loại cơ sở dữ liệu phổ biến để làm việc với dữ liệu trong cơ sở dữ liệu Cosmos DB. Cấu trúc dữ liệu bên trong được trừu tượng hóa, cho phép các nhà phát triển sử dụng Cosmos DB để lưu trữ và truy vấn dữ liệu bằng các API mà họ đã quen thuộc.

```
!Note
API là viết tắt của Application Programming Interface. Hệ thống quản lý cơ sở dữ liệu 
(và các khung ứng dụng phần mềm khác) cung cấp một tập hợp các API mà các nhà phát triển 
có thể sử dụng để viết các chương trình cần truy cập dữ liệu. Các API khác nhau 
cho các hệ thống quản lý cơ sở dữ liệu khác nhau.
```

Cosmos DB sử dụng indexes và partitioning để cung cấp hiệu suất đọc và ghi nhanh và có thể mở rộng lên đến quy mô khổng lồ dữ liệu. Bạn có thể bật tính năng ghi đa khu vực (multi-region writes), thêm các khu vực Azure mà bạn muốn vào tài khoản Cosmos DB của mình để người dùng phân tán trên toàn cầu có thể làm việc với dữ liệu trong bản sao địa phương của họ.





<a name="M01.1.1"></a>
### When to use Cosmos DB

Cosmos DB là một hệ thống quản lý cơ sở dữ liệu có khả năng mở rộng cao. Cosmos DB tự động phân bổ không gian trong một container cho các phân vùng của bạn, và mỗi phân vùng có thể tăng lên đến kích thước 10 GB. Chỉ một ít chi phí quản trị hành chính được yêu cầu, vì các chỉ mục được tạo ra và duy trì tự động.

Cosmos DB là một dịch vụ nền tảng trong Azure. Cosmos DB đã được sử dụng bởi nhiều sản phẩm của Microsoft cho các ứng dụng quan trọng toàn cầu, bao gồm Skype, Xbox, Microsoft 365, Azure và nhiều sản phẩm khác. Cosmos DB rất phù hợp cho các trường hợp sau:

- IoT and telematics. Những hệ thống này thường tiếp nhận lượng lớn dữ liệu trong các đợt hoạt động thường xuyên. Cosmos DB có thể chấp nhận và lưu trữ thông tin này nhanh chóng. Dữ liệu sau đó có thể được sử dụng bởi các dịch vụ phân tích, chẳng hạn như Azure Machine Learning, Azure HDInsight và Power BI. Ngoài ra, bạn có thể xử lý dữ liệu theo thời gian thực bằng cách sử dụng Azure Functions được kích hoạt khi dữ liệu được ghi vào cơ sở dữ liệu.
- Retail and marketing. Microsoft sử dụng Cosmos DB cho các nền tảng thương mại điện tử của riêng mình chạy trên Windows Store và Xbox Live. Nó cũng được sử dụng trong ngành bán lẻ để lưu trữ dữ liệu danh mục và cho event sourcing trong các đường ống xử lý đơn hàng.
- Gaming. Lớp cơ sở dữ liệu là một thành phần quan trọng của các ứng dụng trò chơi. Các trò chơi hiện đại thực hiện xử lý đồ họa trên các máy khách di động/máy console, nhưng phụ thuộc vào đám mây để cung cấp nội dung được tùy chỉnh và cá nhân hóa như thống kê trong trò chơi, tích hợp mạng xã hội và bảng xếp hạng điểm cao. Trò chơi thường đòi hỏi độ trễ đọc và ghi một mili giây duy nhất để cung cấp trải nghiệm chơi game hấp dẫn. Cơ sở dữ liệu trò chơi cần phải nhanh và có thể xử lý đợt yêu cầu đột ngột trong suốt giai đoạn ra mắt trò chơi mới và các tính năng cập nhật.
- Web and mobile applications. Azure Cosmos DB thường được sử dụng trong các ứng dụng web và di động và rất phù hợp để mô hình hóa tương tác xã hội, tích hợp với các dịch vụ bên thứ ba và xây dựng trải nghiệm cá nhân phong phú. Các SDK Cosmos DB có thể được sử dụng để xây dựng các ứng dụng iOS và Android phong phú bằng framework Xamarin phổ biến.

For additional information about uses for Cosmos DB, read [Common Azure Cosmos DB use cases](https://learn.microsoft.com/en-us/azure/cosmos-db/use-cases).







<a name="M01.2"></a>
## Identify Azure Cosmos DB APIs

Azure Cosmos DB là cơ sở dữ liệu phân tán được quản lý hoàn toàn và không có máy chủ của Microsoft cho các ứng dụng bất kỳ kích thước hoặc quy mô nào, hỗ trợ cả relational và non-relational workloads. Nhà phát triển có thể xây dựng và di chuyển các ứng dụng nhanh chóng bằng cách sử dụng các công cụ cơ sở dữ liệu mã nguồn mở ưa thích của họ, bao gồm PostgreSQL, MongoDB và Apache Cassandra. Khi bạn cung cấp một phiên bản Cosmos DB mới, bạn chọn công cụ cơ sở dữ liệu mà bạn muốn sử dụng. Lựa chọn công cụ phụ thuộc vào nhiều yếu tố bao gồm loại dữ liệu cần được lưu trữ, nhu cầu hỗ trợ các ứng dụng hiện có và kỹ năng của nhà phát triển làm việc với kho dữ liệu.








<a name="M01.2.1"></a>
### Azure Cosmos DB for NoSQL

Azure Cosmos DB for NoSQL là dịch vụ non-relational của Microsoft để làm việc với mô hình dữ liệu document. Nó quản lý dữ liệu trong định dạng JSON document và mặc dù là một giải pháp lưu trữ dữ liệu NoSQL, nhưng sử dụng cú pháp SQL để làm việc với dữ liệu.

Một truy vấn SQL cho một cơ sở dữ liệu Azure Cosmos DB chứa dữ liệu khách hàng có thể trông giống như thế này:

```SQL
SELECT *
FROM customers c
WHERE c.id = "joe@litware.com"
```

Kết quả của truy vấn này bao gồm một hoặc nhiều JSON documents, như được hiển thị ở đây:

```JSON
{
   "id": "joe@litware.com",
   "name": "Joe Jones",
   "address": {
        "street": "1 Main St.",
        "city": "Seattle"
    }
}
```






<a name="M01.2.2"></a>
### Azure Cosmos DB for MongoDB

MongoDB là một cơ sở dữ liệu mã nguồn mở phổ biến, trong đó dữ liệu được lưu trữ dưới định dạng Binary JSON (BSON). Azure Cosmos DB for MongoDB cho phép nhà phát triển sử dụng thư viện và mã lệnh của MongoDB để làm việc với dữ liệu trong Azure Cosmos DB.

Ngôn ngữ truy vấn MongoDB (MQL) sử dụng cú pháp hướng đối tượng gọn nhẹ, trong đó nhà phát triển sử dụng các đối tượng để gọi các phương thức. Ví dụ, truy vấn sau sử dụng phương thức **find** để truy vấn **products** collection trong đối tượng **db**:

```JavaScript
db.products.find({id: 123})
```

Kết quả của truy vấn này bao gồm các tài liệu JSON, tương tự như sau:

```JSON
{
   "id": 123,
   "name": "Hammer",
   "price": 2.99
}
```







<a name="M01.2.3"></a>
### Azure Cosmos DB for PostgreSQL

Azure Cosmos DB for PostgreSQL là một cơ sở dữ liệu quan hệ toàn cầu của PostgreSQL, được phân tán tự động để giúp bạn xây dựng các ứng dụng có khả năng mở rộng cao. Bạn có thể bắt đầu xây dựng các ứng dụng trên một nhóm máy chủ đơn lẻ, cùng cách với PostgreSQL ở bất kỳ đâu khác. Khi yêu cầu về tính mở rộng và hiệu suất của ứng dụng của bạn tăng lên, bạn có thể mở rộng một cách dễ dàng đến nhiều nút bằng cách phân phối các bảng của bạn một cách minh bạch. PostgreSQL là một hệ quảntrị cơ sở dữ liệu quan hệ (RDBMS) trong đó bạn định nghĩa các bảng dữ liệu quan hệ, ví dụ như bạn có thể định nghĩa một bảng sản phẩm như sau:

| ProductID | ProductName | Price |
| ----- | ----- | -----|
| 123 | Hammer | 2.99 |
| 162 | Screwdriver | 3.49 |

Sau đó, bạn có thể truy vấn bảng này để lấy tên và giá của một sản phẩm cụ thể bằng cách sử dụng SQL như sau:

```SQL
SELECT ProductName, Price 
FROM Products
WHERE ProductID = 123;
```

Kết quả của truy vấn này sẽ chứa một hàng cho sản phẩm 123, giống như sau:

| ProductName | Price |
| ----- | ----- |
| Hammer | 2.99 |






<a name="M01.2.4"></a>
### Azure Cosmos DB for Table

Azure Cosmos DB for Table được sử dụng để làm việc với dữ liệu trong các bảng key-value, tương tự như Azure Table Storage. Nó cung cấp khả năng mở rộng và hiệu suất tốt hơn so với Azure Table Storage. Ví dụ, bạn có thể định nghĩa một bảng có tên là Customers như sau:

| PartitionKey | RowKey | Name | Email |
| ----- | ----- | ----- | ----- |
| 1 | 123 | Joe Jones | joe@litware.com |
| 1 | 124 | Samir Nadoy | samir@northwind.com |

Sau đó, bạn có thể sử dụng Table API thông qua một trong các SDK cụ thể cho ngôn ngữ để gọi đến điểm cuối dịch vụ của mình để lấy dữ liệu từ bảng. Ví dụ, yêu cầu sau đây trả về hàng chứa bản ghi cho Samir Nadoy trong bảng trên:

```text
https://endpoint/Customers(PartitionKey='1',RowKey='124')
```







<a name="M01.2.5"></a>
### Azure Cosmos DB for Apache Cassandra

Azure Cosmos DB for Apache Cassandra tương thích với Apache Cassandra, là một cơ sở dữ liệu mã nguồn mở phổ biến sử dụng cấu trúc lưu trữ column-family. Column-families là các bảng, tương tự như trong cơ sở dữ liệu quan hệ, với sự khác biệt là không bắt buộc mỗi hàng phải có cùng các cột.

Ví dụ, bạn có thể tạo một bảng **Employees** như sau:

| ID | Name | Manager |
| -----| ----- | ----- |
| 1 | Sue Smith |   |
| 2 | Ben Chan | Sue Smith |

Cassandra hỗ trợ cú pháp dựa trên SQL, vì vậy một client application có thể lấy bản ghi cho Ben Chan như sau:

```SQL
SELECT * FROM Employees WHERE ID = 2
```





<a name="M01.2.6"></a>
### Azure Cosmos DB for Apache Gremlin

Azure Cosmos DB for Apache Gremlin được sử dụng với dữ liệu trong *cấu trúc đồ thị (graph structure)*; trong đó các thực thể được xác định là các đỉnh tạo thành các nút trong đồ thị liên kết. Các nút được kết nối bằng các cạnh thể hiện mối quan hệ, như sau:

![image](https://user-images.githubusercontent.com/62134515/223378792-62618121-2e57-41f4-9b23-3fe1be4e047f.png)

Ví dụ trong hình minh họa hai loại đỉnh (nhân viên và phòng ban) và các cạnh kết nối chúng (nhân viên "Ben" báo cáo cho nhân viên "Sue" và cả hai nhân viên đều làm việc ở phòng ban "Hardware").

Cú pháp Gremlin bao gồm các hàm để thao tác trên các đỉnh và cạnh, cho phép bạn chèn, cập nhật, xóa và truy vấn dữ liệu trong đồ thị. Ví dụ, bạn có thể sử dụng code sau để thêm một nhân viên mới có tên là Alice và báo cáo cho nhân viên có ID 1 (Sue):

```
g.addV('employee').property('id', '3').property('firstName', 'Alice')
g.V('3').addE('reports to').to(g.V('1'))
```

Câu truy vấn sau trả về tất cả các đỉnh nhân viên, theo thứ tự ID.

```
g.V().hasLabel('employee').order().by('id')
```


















<a name="M01.3"></a>
## Explore Azure Files





<a name="M01.4"></a>
## Explore Azure Tables










<a name="M01.4"></a>
## Explore Azure Tables

[Launch Exercise](https://microsoftlearning.github.io/DP-900T00A-Azure-Data-Fundamentals/Instructions/Labs/dp900-02-storage-lab.html)








<a name="M01.6"></a>
## Knowledge check















