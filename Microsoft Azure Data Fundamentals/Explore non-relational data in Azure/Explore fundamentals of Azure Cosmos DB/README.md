# Mục Lục

* [**Explore fundamentals of Azure Cosmos DB**](#M01)
    - [Describe Azure Cosmos DB](#M01.1)
      + [When to use Cosmos DB](#M01.1.1)
    - [Explore Azure DataLake Storage Gen2](#M01.2)
    - [Explore Azure Files](#M01.3)
    - [Explore Azure Tables](#M01.4)
    - [Exercise: Explore Azure Storage](#M01.5)
    - [Knowledge check](#M01.6)










<a name="M01"></a>
# [Explore fundamentals of Azure Cosmos DB](https://learn.microsoft.com/en-us/training/modules/explore-non-relational-data-stores-azure/)



<a name="M01.1"></a>
## Describe Azure Cosmos DB

![image](https://user-images.githubusercontent.com/62134515/222652171-7bb15027-99e7-49e3-88b8-22fbd093c735.png)

Azure Cosmos DB hỗ trợ nhiều giao diện lập trình ứng dụng (API) khác nhau cho phép nhà phát triển sử dụng cú pháp lập trình của nhiều loại cơ sở dữ liệu phổ biến để làm việc với dữ liệu trong cơ sở dữ liệu Cosmos DB. Cấu trúc dữ liệu bên trong được trừu tượng hóa, cho phép các nhà phát triển sử dụng Cosmos DB để lưu trữ và truy vấn dữ liệu bằng các API mà họ đã quen thuộc.

```
!Note
API là viết tắt của Application Programming Interface. Hệ thống quản lý cơ sở dữ liệu 
(và các khung ứng dụng phần mềm khác) cung cấp một tập hợp các API mà các nhà phát triển 
có thể sử dụng để viết các chương trình cần truy cập dữ liệu. Các API khác nhau 
cho các hệ thống quản lý cơ sở dữ liệu khác nhau.
```

Cosmos DB sử dụng các chỉ mục và phân vùng để cung cấp hiệu suất đọc và ghi nhanh và có thể mở rộng lên đến quy mô khổng lồ dữ liệu. Bạn có thể bật tính năng ghi đa khu vực (multi-region writes), thêm các khu vực Azure mà bạn muốn vào tài khoản Cosmos DB của mình để người dùng phân tán trên toàn cầu có thể làm việc với dữ liệu trong bản sao địa phương của họ.





<a name="M01.1.1"></a>
### When to use Cosmos DB

Cosmos DB là một hệ thống quản lý cơ sở dữ liệu có khả năng mở rộng cao. Cosmos DB tự động phân bổ không gian trong một container cho các phân vùng của bạn, và mỗi phân vùng có thể tăng lên đến kích thước 10 GB. Chỉ một ít chi phí quản trị hành chính được yêu cầu, vì các chỉ mục được tạo ra và duy trì tự động.

Cosmos DB là một dịch vụ nền tảng trong Azure. Cosmos DB đã được sử dụng bởi nhiều sản phẩm của Microsoft cho các ứng dụng quan trọng toàn cầu, bao gồm Skype, Xbox, Microsoft 365, Azure và nhiều sản phẩm khác. Cosmos DB rất phù hợp cho các kịch bản sau:

- IoT and telematics. Những hệ thống này thường tiếp nhận lượng lớn dữ liệu trong các đợt hoạt động thường xuyên. Cosmos DB có thể chấp nhận và lưu trữ thông tin này nhanh chóng. Dữ liệu sau đó có thể được sử dụng bởi các dịch vụ phân tích, chẳng hạn như Azure Machine Learning, Azure HDInsight và Power BI. Ngoài ra, bạn có thể xử lý dữ liệu theo thời gian thực bằng cách sử dụng Azure Functions được kích hoạt khi dữ liệu được ghi vào cơ sở dữ liệu.
- Retail and marketing. Microsoft sử dụng Cosmos DB cho các nền tảng thương mại điện tử của riêng mình chạy trên Windows Store và Xbox Live. Nó cũng được sử dụng trong ngành bán lẻ để lưu trữ dữ liệu danh mục và cho event sourcing trong các đường ống xử lý đơn hàng.
- Gaming. Lớp cơ sở dữ liệu là một thành phần quan trọng của các ứng dụng trò chơi. Các trò chơi hiện đại thực hiện xử lý đồ họa trên các máy khách di động/máy console, nhưng phụ thuộc vào đám mây để cung cấp nội dung được tùy chỉnh và cá nhân hóa như thống kê trong trò chơi, tích hợp mạng xã hội và bảng xếp hạng điểm cao. Trò chơi thường đòi hỏi độ trễ đọc và ghi một mili giây duy nhất để cung cấp trải nghiệm chơi game hấp dẫn. Cơ sở dữ liệu trò chơi cần phải nhanh và có thể xử lý đợt yêu cầu đột ngột trong suốt giai đoạn ra mắt trò chơi mới và các tính năng cập nhật.
- Web and mobile applications. Azure Cosmos DB thường được sử dụng trong các ứng dụng web và di động và rất phù hợp để mô hình hóa tương tác xã hội, tích hợp với các dịch vụ bên thứ ba và xây dựng trải nghiệm cá nhân phong phú. Các SDK Cosmos DB có thể được sử dụng để xây dựng các ứng dụng iOS và Android phong phú bằng framework Xamarin phổ biến.

For additional information about uses for Cosmos DB, read [Common Azure Cosmos DB use cases](https://learn.microsoft.com/en-us/azure/cosmos-db/use-cases).







<a name="M01.2"></a>
## Explore Azure DataLake Storage Gen2

Azure Data Lake Store (Gen1) là một dịch vụ riêng biệt của Microsoft Azure được thiết kế để lưu trữ dữ liệu theo hệ thống phân cấp cho các hồ dữ liệu phân tích. Nó thường được sử dụng trong các giải pháp phân tích dữ liệu lớn (big data) và làm việc với các dữ liệu có cấu trúc, bán cấu trúc và không cấu trúc được lưu trữ trong các tệp tin. Azure Data Lake Storage Gen2 là phiên bản mới hơn của dịch vụ này, được tích hợp vào Azure Storage, cho phép bạn tận dụng tính mở rộng của lưu trữ blob và kiểm soát chi phí của các lớp lưu trữ, kết hợp với khả năng hệ thống tệp tin phân cấp và khả năng tương thích với các hệ thống phân tích chính của Azure Data Lake Store.

![image](https://user-images.githubusercontent.com/62134515/222390315-26a738b7-1941-4043-a95f-53983123afa5.png)

Các hệ thống như Hadoop trong Azure HDInsight, Azure Databricks và Azure Synapse Analytics có thể gắn kết một hệ thống tệp phân tán được lưu trữ trong Azure Data Lake Store Gen2 và sử dụng nó để xử lý các khối lượng dữ liệu lớn.

Để tạo một hệ thống tệp tin Azure Data Lake Store Gen2, bạn phải bật tùy chọn **Hierarchical Namespace** của một tài khoản Azure Storage. Bạn có thể làm điều này khi tạo tài khoản lưu trữ ban đầu, hoặc bạn có thể nâng cấp một tài khoản lưu trữ Azure hiện có để hỗ trợ Data Lake Gen2. Tuy nhiên, hãy lưu ý rằng việc nâng cấp là một quá trình một chiều - sau khi nâng cấp một tài khoản lưu trữ để hỗ trợ hierarchical namespacecho lưu trữ blob, bạn không thể hoàn nguyên nó về flat namespace.











<a name="M01.3"></a>
## Explore Azure Files

Nhiều hệ thống on-premises bao gồm một mạng lưới các máy tính trong nhà sử dụng chia sẻ tệp. Chia sẻ tệp cho phép bạn lưu trữ một tệp trên một máy tính và cấp quyền truy cập vào tệp đó cho người dùng và ứng dụng chạy trên các máy tính khác. Chiến lược này có thể hoạt động tốt cho các máy tính trong cùng mạng nội bộ, nhưng không mở rộng tốt khi số lượng người dùng tăng lên hoặc nếu người dùng được đặt tại các địa điểm khác nhau.

Azure Files thực chất là một cách để tạo chia sẻ mạng dựa trên cloud, giống như bạn thường thấy trong các tổ chức on-premises để làm cho tài liệu và các tệp khác có sẵn cho nhiều người dùng. Bằng cách lưu trữ chia sẻ tệp trên Azure, các tổ chức có thể loại bỏ chi phí phần cứng và chi phí bảo trì, và tận dụng được tính khả dụng cao và lưu trữ cloud có khả năng mở rộng cho các tệp.

![image](https://user-images.githubusercontent.com/62134515/222397747-d1ea6507-0e77-4fa5-a948-c479bc452b65.png)

Bạn có thể tạo lưu trữ Azure File trong một tài khoản lưu trữ. Azure Files cho phép bạn chia sẻ tối đa 100 TB dữ liệu trong một tài khoản lưu trữ. Dữ liệu này có thể phân phối trên bất kỳ số lượng chia sẻ tệp nào trong tài khoản. Kích thước tối đa của một tệp đơn lẻ là 1 TB, nhưng bạn có thể thiết lập các hạn ngạch để giới hạn kích thước của mỗi chia sẻ dưới con số này. Hiện tại, Azure File Storage hỗ trợ đến 2000 kết nối đồng thời cho mỗi tệp được chia sẻ.

Sau khi bạn đã tạo tài khoản lưu trữ, bạn có thể tải lên các tệp vào Azure File Storage bằng cách sử dụng cổng thông tin Azure hoặc các công cụ như tiện ích AzCopy. Bạn cũng có thể sử dụng dịch vụ đồng bộ hóa Azure File Sync để đồng bộ hóa các bản sao được lưu trữ cục bộ của các tệp được chia sẻ với dữ liệu trong Azure File Storage.

Azure File Storage cung cấp hai cấp độ hiệu suất. Cấp độ Standard sử dụng disk-based hardware trong một trung tâm dữ liệu, và cấp độ Premium sử dụng solid-state disks. Cấp độ Premium cung cấp khả năng thông lượng lớn hơn, nhưng được tính phí với mức giá cao hơn.

Azure Files hỗ trợ hai giao thức chia sẻ tệp mạng phổ biến:

- Chia sẻ tệp Server Message Block (SMB) được sử dụng phổ biến trên nhiều hệ điều hành (Windows, Linux, macOS).
- Chia sẻ tệp Network File System (NFS) được sử dụng bởi một số phiên bản Linux và macOS. Để tạo một chia sẻ NFS, bạn phải sử dụng một tài khoản lưu trữ loại premium và tạo và cấu hình một mạng ảo để kiểm soát truy cập vào chia sẻ được.











<a name="M01.4"></a>
## Explore Azure Tables

Azure Table Storage là một giải pháp lưu trữ NoSQL sử dụng các bảng chứa các mục dữ liệu key/value. Mỗi mục được đại diện bởi một hàng chứa các cột cho các trường dữ liệu cần được lưu trữ.

![image](https://user-images.githubusercontent.com/62134515/222404588-f1d8709e-2009-41f1-9966-2bff7f5bbdc3.png)

Tuy nhiên, đừng bị lừa khi nghĩ rằng một bảng Azure Table Storage giống như một bảng trong cơ sở dữ liệu quan hệ. Azure Table cho phép bạn lưu trữ dữ liệu bán cấu trúc. Tất cả các hàng trong một bảng phải có một khóa duy nhất (bao gồm khóa phân vùng và khóa hàng), và khi bạn sửa đổi dữ liệu trong một bảng, một cột timestamp ghi lại ngày và giờ mà sửa đổi được thực hiện; nhưng ngoài ra, các cột trong mỗi hàng có thể khác nhau. Bảng Azure Table Storage không có khái niệm về oreign keys, relationships, stored procedures, views, hoặc các đối tượng khác mà bạn có thể tìm thấy trong cơ sở dữ liệu quan hệ. Dữ liệu trong bộ lưu trữ Azure Table thường được denormalized, với mỗi hàng chứa toàn bộ dữ liệu cho một thực thể logic. Ví dụ, một bảng chứa thông tin khách hàng có thể lưu trữ tên, họ, một hoặc nhiều số điện thoại và một hoặc nhiều địa chỉ cho mỗi khách hàng. Số lượng trường trong mỗi hàng có thể khác nhau, tùy thuộc vào số lượng số điện thoại và địa chỉ cho mỗi khách hàng và các chi tiết được ghi lại cho mỗi địa chỉ. Trong cơ sở dữ liệu quan hệ, thông tin này sẽ được chia thành nhiều hàng trong nhiều bảng.


Để đảm bảo truy cập nhanh, Azure Table Storage chia một bảng thành các phân vùng. Phân vùng là cơ chế để nhóm các hàng liên quan vào một thuộc tính chung hoặc khóa phân vùng. Các hàng chia sẻ cùng khóa phân vùng sẽ được lưu trữ cùng nhau. Phân vùng không chỉ giúp tổ chức dữ liệu mà còn có thể cải thiện khả năng mở rộng và hiệu suất theo các cách sau:

- Các phân vùng độc lập với nhau và có thể tăng hoặc giảm khi các hàng được thêm vào hoặc xóa khỏi phân vùng. Một bảng có thể chứa bất kỳ số lượng phân vùng nào.

- Khi bạn tìm kiếm dữ liệu, bạn có thể bao gồm khóa phân vùng trong tiêu chí tìm kiếm. Điều này giúp thu hẹp phạm vi dữ liệu cần xem xét và cải thiện hiệu suất bằng cách giảm lượng I/O (các hoạt động nhập và xuất hoặc đọc và ghi) cần thiết để định vị dữ liệu.

Khóa trong một bảng Azure Table Storage bao gồm hai phần; *khóa phân vùng (partition key)* xác định phân vùng chứa hàng và một *khóa hàng (row key)* duy nhất cho mỗi hàng trong cùng phân vùng. Các mục trong cùng một phân vùng được lưu trữ theo thứ tự khóa hàng. Nếu một ứng dụng thêm một hàng mới vào một bảng, Azure đảm bảo rằng hàng được đặt ở vị trí chính xác trong bảng. Hệ thống này cho phép ứng dụng nhanh chóng thực hiện các truy vấn điểm xác định một hàng duy nhất và các truy vấn phạm vi để truy xuất một khối hàng liên tiếp trong một phân vùng.









<a name="M01.4"></a>
## Explore Azure Tables

[Launch Exercise](https://microsoftlearning.github.io/DP-900T00A-Azure-Data-Fundamentals/Instructions/Labs/dp900-02-storage-lab.html)








<a name="M01.6"></a>
## Knowledge check

![image](https://user-images.githubusercontent.com/62134515/222419553-3df76bbd-01ee-4fb2-91b6-391c59cebf97.png)













