# Mục Lục

* [**Explore Azure Storage for non-relational data**](#M01)
    - [Explore Azure blob storage](#M01.1)
    - [Explore Azure DataLake Storage Gen2](#M01.2)
    - [Explore Azure Files](#M01.3)
    - [Knowledge check](#M01.5)










<a name="M01"></a>
# [Explore Azure Storage for non-relational data](https://learn.microsoft.com/en-us/training/modules/explore-provision-deploy-non-relational-data-services-azure/)



<a name="M01.1"></a>
## Explore Azure blob storage

Azure Blob Storage là một dịch vụ cho phép bạn lưu trữ lượng lớn dữ liệu phi cấu trúc dưới dạng các đối tượng lớn nhị phân, hay còn được gọi là "blobs", trên Cloud. Blobs là cách lưu trữ hiệu quả cho các tệp tin dữ liệu với định dạng được tối ưu hóa cho việc lưu trữ trên Cloud, và ứng dụng có thể đọc và ghi chúng bằng cách sử dụng Azure blob storage API.

![image](https://user-images.githubusercontent.com/62134515/222375011-3e07f759-90d6-4e53-b154-bab72a9b3482.png)

Trong một tài khoản lưu trữ Azure, bạn lưu trữ các blobs trong các container. Một container cung cấp một cách thuận tiện để nhóm các blobs có liên quan với nhau. Bạn có thể kiểm soát ai có thể đọc và ghi blobs bên trong một container ở mức container.

Trong một container, bạn có thể tổ chức các blobs theo một cấu trúc phân cấp của các thư mục ảo, tương tự như các tệp tin trong hệ thống tệp tin trên ổ đĩa. Tuy nhiên, theo mặc định, các thư mục này chỉ là một cách sử dụng ký tự "/" trong tên blob để tổ chức các blobs thành các "namespace". Các thư mục là hoàn toàn ảo và bạn không thể thực hiện các thao tác cấp thư mục để kiểm soát truy cập hoặc thực hiện các thao tác hàng loạt.

Azure Blob Storage hỗ trợ ba loại blob khác nhau:

- **Block blobs**: Là một tập hợp các block, mỗi block có thể có kích thước khác nhau, tối đa là 100 MB. Một block blob có thể chứa tối đa 50.000 block, cho phép dung lượng tối đa lên đến hơn 4,7 TB. Block là lượng dữ liệu nhỏ nhất có thể được đọc hoặc ghi dưới dạng một đơn vị riêng lẻ. Block blobs được sử dụng tốt nhất để lưu trữ các đối tượng nhị phân lớn rời rạc mà thay đổi ít.
- **Page blobs**: Là một tập hợp các trang có kích thước cố định là 512 byte. Page blob được tối ưu hóa để hỗ trợ các hoạt động đọc và ghi ngẫu nhiên; bạn có thể lấy và lưu trữ dữ liệu cho một trang nếu cần thiết. Một page blob có thể chứa lên đến 8 TB dữ liệu. Azure sử dụng page blobs để triển khai lưu trữ đĩa ảo cho các máy ảo.
- **Append blobs**: Là một block blob tối ưu hóa để hỗ trợ các hoạt động ghi thêm. Bạn chỉ có thể thêm block vào cuối của append blob; không hỗ trợ cập nhật hoặc xóa các block đã có sẵn. Mỗi block có thể có kích thước khác nhau, tối đa là 4 MB. Dung lượng tối đa của một append blob là hơn 195 GB.

Blob storage cung cấp ba cấp độ truy cập khác nhau, giúp cân bằng độ trễ truy cập và chi phí lưu trữ:

- Cấp độ Hot là mặc định. Bạn sử dụng cấp độ này cho các blob được truy cập thường xuyên. Dữ liệu blob được lưu trữ trên phương tiện hiệu suất cao.
- Cấp độ Cool có hiệu suất thấp hơn và gây ra chi phí lưu trữ giảm so với cấp độ Hot. Sử dụng cấp độ Cool cho dữ liệu được truy cập ít. Thông thường, các blob được tạo mới sẽ được truy cập thường xuyên ban đầu, nhưng ít hơn theo thời gian. Trong những tình huống như vậy, bạn có thể tạo blob ở cấp độ Hot, nhưng sau đó chuyển đổi sang cấp độ Cool. Bạn có thể di chuyển một blob từ cấp độ Cool trở lại cấp độ Hot.
-  Cấp độ Archive cung cấp chi phí lưu trữ thấp nhất, nhưng với độ trễ tăng lên. Cấp độ Archive dành cho dữ liệu lịch sử không được mất, nhưng chỉ được yêu cầu hiếm khi. Các blob trong cấp độ Archive được lưu trữ hiệu quả trong trạng thái offline. Thời gian đọc thông thường cho các cấp độ Hot và Cool là vài mili giây, nhưng đối với cấp độ Archive, có thể mất vài giờ để dữ liệu trở nên có sẵn. Để lấy một blob từ cấp độ Archive, bạn phải thay đổi cấp độ truy cập sang Hot hoặc Cool. Sau đó, blob sẽ được tái tạo. Bạn chỉ có thể đọc blob khi quá trình tái tạo hoàn tất.

Bạn có thể tạo các chính sách quản lý vòng đời (lifecycle management policies) cho các đối tượng blob trong tài khoản lưu trữ. Một chính sách quản lý vòng đời có thể tự động di chuyển một đối tượng blob từ Hot đến Cool, sau đó đến Archive khi nó lão hóa và được sử dụng ít hơn (chính sách dựa trên số ngày kể từ khi sửa đổi). Một chính sách quản lý vòng đời cũng có thể sắp xếp xóa các đối tượng blob lỗi thời.













<a name="M01.2"></a>
## Explore Azure DataLake Storage Gen2

Azure Data Lake Store (Gen1) là một dịch vụ riêng biệt của Microsoft Azure được thiết kế để lưu trữ dữ liệu theo hệ thống phân cấp cho các hồ dữ liệu phân tích. Nó thường được sử dụng trong các giải pháp phân tích dữ liệu lớn (big data) và làm việc với các dữ liệu có cấu trúc, bán cấu trúc và không cấu trúc được lưu trữ trong các tệp tin. Azure Data Lake Storage Gen2 là phiên bản mới hơn của dịch vụ này, được tích hợp vào Azure Storage, cho phép bạn tận dụng tính mở rộng của lưu trữ blob và kiểm soát chi phí của các lớp lưu trữ, kết hợp với khả năng hệ thống tệp tin phân cấp và khả năng tương thích với các hệ thống phân tích chính của Azure Data Lake Store.

![image](https://user-images.githubusercontent.com/62134515/222390315-26a738b7-1941-4043-a95f-53983123afa5.png)

Các hệ thống như Hadoop trong Azure HDInsight, Azure Databricks và Azure Synapse Analytics có thể gắn kết một hệ thống tệp phân tán được lưu trữ trong Azure Data Lake Store Gen2 và sử dụng nó để xử lý các khối lượng dữ liệu lớn.

Để tạo một hệ thống tệp tin Azure Data Lake Store Gen2, bạn phải bật tùy chọn **Hierarchical Namespace** của một tài khoản Azure Storage. Bạn có thể làm điều này khi tạo tài khoản lưu trữ ban đầu, hoặc bạn có thể nâng cấp một tài khoản lưu trữ Azure hiện có để hỗ trợ Data Lake Gen2. Tuy nhiên, hãy lưu ý rằng việc nâng cấp là một quá trình một chiều - sau khi nâng cấp một tài khoản lưu trữ để hỗ trợ hierarchical namespacecho lưu trữ blob, bạn không thể hoàn nguyên nó về flat namespace.











<a name="M01.3"></a>
## Explore Azure Files
[Launch Exercise](https://microsoftlearning.github.io/DP-900T00A-Azure-Data-Fundamentals/Instructions/Labs/dp900-01-sql-lab.html)






<a name="M01.4"></a>
## Knowledge check

![image](https://user-images.githubusercontent.com/62134515/221832102-0b9f9d0d-6fae-4b4d-86f0-d38f65a9f942.png)












