# Mục Lục

* [**Explore Azure Storage for non-relational data**](#M01)
    - [Explore Azure blob storage](#M01.1)
    - [Describe Azure services for open-source databases](#M01.2)
      + [What are MySQL, MariaDB, and PostgreSQL?](#M01.2.1)
      + [Azure Database for MySQL](#M01.2.2)
        * [Benefits of Azure Database for MySQL](#M01.2.2.1)
      + [Azure Database for MariaDB](#M01.2.3)
        * [Benefits of Azure Database for MariaDB](#M01.2.3.1)
      + [Azure Database for PostgreSQL](#M01.2.4)
        * [Azure Database for PostgreSQL Flexible Server](#M01.2.4.1)
        * [Benefits of Azure Database for PostgreSQL](#M01.2.4.2)
    - [Exercise: Explore Azure relational database services](#M01.3)
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
## Describe Azure services for open-source databases

Ngoài các dịch vụ Azure SQL, các dịch vụ dữ liệu Azure cũng có sẵn cho các hệ thống cơ sở dữ liệu quan hệ phổ biến khác, bao gồm MySQL, MariaDB và PostgreSQL. Lý do chính cho các dịch vụ này là để cho phép các tổ chức sử dụng chúng trong các ứng dụng on-premises đang sử dụng chuyển sang Azure nhanh chóng, mà không cần thực hiện những thay đổi đáng kể cho ứng dụng của họ.







<a name="M01.2.1"></a>
### What are MySQL, MariaDB, and PostgreSQL?

MySQL, MariaDB và PostgreSQL là các hệ quản trị cơ sở dữ liệu quan hệ được thiết kế để phục vụ các chuyên ngành khác nhau.

MySQL bắt đầu ra đời như một hệ quản trị cơ sở dữ liệu mã nguồn mở dễ sử dụng. Đây là hệ quản trị cơ sở dữ liệu quan hệ mã nguồn mở hàng đầu dành cho các ứng dụng Linux, Apache, MySQL và PHP (LAMP). MySQL có nhiều phiên bản, bao gồm phiên bản Community, Standard và Enterprise. Phiên bản Community có sẵn miễn phí và đã từng được ưa chuộng như một hệ quản trị cơ sở dữ liệu cho các ứng dụng web chạy trên nền Linux. Các phiên bản cũng có sẵn cho Windows. Phiên bản Standard cung cấp hiệu suất cao hơn và sử dụng công nghệ lưu trữ dữ liệu khác. Phiên bản Enterprise cung cấp một bộ công cụ và tính năng toàn diện, bao gồm tính bảo mật, khả năng sẵn có và khả năng mở rộng tốt hơn. Standard và Enterprise là những phiên bản được sử dụng phổ biến nhất bởi các tổ chức thương mại, tuy nhiên, các phiên bản này không miễn phí.

MariaDB là một hệ quản trị cơ sở dữ liệu mới hơn, được tạo ra bởi các nhà phát triển của MySQL. Sau đó, công cụ cơ sở dữ liệu đã được viết lại và tối ưu hóa để cải thiện hiệu suất. MariaDB cung cấp tính tương thích với Oracle Database (một hệ quản trị cơ sở dữ liệu thương mại phổ biến khác). Một tính năng đáng chú ý của MariaDB là khả năng hỗ trợ dữ liệu thời gian tích hợp sẵn. Một bảng có thể chứa nhiều phiên bản dữ liệu, cho phép ứng dụng truy vấn dữ liệu khi nó xuất hiện ở một thời điểm nào đó trong quá khứ.

PostgreSQL là một hybrid relational-object database. Bạn có thể lưu trữ dữ liệu trong các bảng quan hệ, nhưng cơ sở dữ liệu PostgreSQL cũng cho phép bạn lưu trữ các loại dữ liệu tùy chỉnh, với các thuộc tính phi quan hệ riêng của chúng. Hệ thống quản lý cơ sở dữ liệu này có tính mở rộng; bạn có thể thêm các code module vào cơ sở dữ liệu, các module này có thể chạy bởi các truy vấn. Một tính năng chính khác là khả năng lưu trữ và xử lý dữ liệu hình học, chẳng hạn như đường thẳng, vòng tròn và đa giác.

PostgreSQL có ngôn ngữ truy vấn riêng gọi là pgsql. Ngôn ngữ này là một biến thể của ngôn ngữ truy vấn quan hệ chuẩn, SQL, với các tính năng cho phép bạn viết các thủ tục lưu trữ chạy bên trong cơ sở dữ liệu.











<a name="M01.2.2"></a>
### Azure Database for MySQL

![image](https://user-images.githubusercontent.com/62134515/221767897-b85b3370-7f81-43c7-8d20-b9afe7f8c40c.png)

Azure Database for MySQL là một triển khai PaaS của MySQL trên Azure cloud, dựa trên phiên bản MySQL Community Edition.

Dịch vụ Azure Database for MySQL bao gồm tính sẵn sàng cao mà không cần phải trả thêm chi phí, và khả năng mở rộng theo nhu cầu. Bạn chỉ trả tiền cho những gì bạn sử dụng. Các bản sao lưu tự động được cung cấp, với khả năng phục hồi theo thời gian.

Máy chủ cung cấp bảo mật kết nối để thực thi các quy tắc tường lửa và tùy chọn yêu cầu các kết nối SSL. Nhiều tham số máy chủ cho phép bạn cấu hình các thiết lập máy chủ như chế độ khóa, số kết nối tối đa và thời gian chờ.

Azure Database for MySQL cung cấp một hệ thống cơ sở dữ liệu toàn cầu có thể mở rộng đến các cơ sở dữ liệu lớn mà không cần quản lý phần cứng, các thành phần mạng, máy chủ ảo, các bản vá phần mềm và các thành phần cơ bản khác.

Một số thao tác không khả dụng với Azure Database for MySQL. Những chức năng này chủ yếu liên quan đến bảo mật và quản trị. Azure quản lý những khía cạnh này của máy chủ cơ sở dữ liệu chính nó.






<a name="M01.2.2.1"></a>
#### Benefits of Azure Database for MySQL

Bạn sẽ nhận được các tính năng sau khi sử dụng Azure Database for MySQL:

- Các tính năng high availability được tích hợp sẵn.
- Hiệu suất dự đoán được.
- Dễ dàng mở rộng và đáp ứng nhanh các yêu cầu về nhu cầu.
- Dữ liệu an toàn, ở cả trạng thái lưu trữ và khi truyền tải.
- Các bản sao lưu tự động và khôi phục theo thời gian cho 35 ngày gần đây nhất.
- Bảo mật và tuân thủ quy định cấp doanh nghiệp về an ninh.

Hệ thống sử dụng cơ chế tính phí theo hình thức trả tiền dựa trên sử dụng, do đó bạn chỉ trả tiền cho những gì bạn sử dụng.

Các máy chủ Azure Database for MySQL cung cấp chức năng giám sát để thêm cảnh báo và xem các số liệu và nhật ký.








<a name="M01.2.3"></a>
### Azure Database for MariaDB

![image](https://user-images.githubusercontent.com/62134515/221767925-03be905e-0211-4d95-8975-3d0643472020.png)

Azure Database for MariaDB là một phiên bản của hệ quản trị cơ sở dữ liệu MariaDB được tích hợp để chạy trên nền tảng Azure. Nó dựa trên phiên bản MariaDB Community.

Cơ sở dữ liệu được quản lý và điều khiển hoàn toàn bởi Azure. Sau khi bạn cung cấp dịch vụ và chuyển dữ liệu của bạn, hệ thống chỉ cần rất ít công việc quản trị bổ sung.







<a name="M01.2.3.1"></a>
#### Benefits of Azure Database for MariaDB

Azure Database for MariaDB cung cấp:

- Có sẵn tính năng high availability mà không phát sinh chi phí bổ sung.
- Hiệu suất đáng tin cậy, với giá cả tính theo hình thức thanh toán dựa trên sử dụng.
- Có thể mở rộng theo nhu cầu trong vài giây.
- Bảo vệ an toàn dữ liệu nhạy cảm trong quá trình lưu trữ và truyền tải.
- Tự động sao lưu và khôi phục điểm thời gian trong vòng tối đa 35 ngày.
- Bảo mật và tuân thủ tiêu chuẩn an ninh doanh nghiệp.







<a name="M01.2.4"></a>
### Azure Database for PostgreSQL

![image](https://user-images.githubusercontent.com/62134515/221767967-d1b0927f-87ac-4586-8144-9539c3c5e62a.png)

Nếu bạn thích PostgreSQL, bạn có thể chọn Azure Database for PostgreSQL để chạy một phiên bản PaaS của PostgreSQL trong Azure Cloud. Dịch vụ này cung cấp các lợi ích về availability, performance, scaling, security, và administrative tương tự như dịch vụ MySQL.

Một số tính năng của on-premises PostgreSQL databases không có sẵn trong Azure Database for PostgreSQL. Những tính năng này chủ yếu liên quan đến các tiện ích mà người dùng có thể thêm vào cơ sở dữ liệu để thực hiện các tác vụ chuyên biệt, chẳng hạn như viết các thủ tục lưu trữ bằng các ngôn ngữ lập trình khác (ngoài pgsql, được cung cấp), và tương tác trực tiếp với hệ điều hành. Một tập hợp cốt lõi của các tiện ích được sử dụng thường xuyên nhất được hỗ trợ, và danh sách các tiện ích có sẵn được liên tục xem xét.





<a name="M01.2.4.1"></a>
#### Azure Database for PostgreSQL Flexible Server

Tùy chọn triển khai flexible-server cho PostgreSQL là một dịch vụ cơ sở dữ liệu được quản lý hoàn toàn. Nó cung cấp mức độ kiểm soát cao và tùy chỉnh cấu hình máy chủ và cung cấp các điều khiển tối ưu hóa chi phí.





<a name="M01.2.4.2"></a>
#### Benefits of Azure Database for PostgreSQL

Azure Database for PostgreSQL là một dịch vụ highly available. Nó được tích hợp các cơ chế phát hiện lỗi và cơ chế chuyển đổi dự phòng.

Người dùng PostgreSQL sẽ quen thuộc với công cụ **pgAdmin**, mà bạn có thể sử dụng để quản lý và giám sát cơ sở dữ liệu PostgreSQL. Bạn có thể tiếp tục sử dụng công cụ này để kết nối với Azure Database for PostgreSQL. Tuy nhiên, một số chức năng tập trung vào máy chủ, chẳng hạn như thực hiện sao lưu và khôi phục máy chủ, không có sẵn vì máy chủ được quản lý và bảo trì bởi Microsoft.

Azure Database for PostgreSQL ghi lại thông tin về các truy vấn chạy trên cơ sở dữ liệu trên máy chủ và lưu chúng trong cơ sở dữ liệu có tên azure_sys. Bạn truy vấn view query_store.qs_view để xem thông tin này và sử dụng nó để giám sát các truy vấn mà người dùng đang chạy. Thông tin này có thể rất hữu ích nếu bạn cần điều chỉnh tinh chỉnh các truy vấn được thực hiện bởi ứng dụng của mình.







<a name="M01.3"></a>
## Exercise: Explore Azure relational database services
[Launch Exercise](https://microsoftlearning.github.io/DP-900T00A-Azure-Data-Fundamentals/Instructions/Labs/dp900-01-sql-lab.html)






<a name="M01.4"></a>
## Knowledge check

![image](https://user-images.githubusercontent.com/62134515/221832102-0b9f9d0d-6fae-4b4d-86f0-d38f65a9f942.png)












