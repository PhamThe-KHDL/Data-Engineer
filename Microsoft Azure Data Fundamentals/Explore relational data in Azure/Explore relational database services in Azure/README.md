# Mục Lục

* [**Explore relational database services in Azure**](#M01)
    - [Describe Azure SQL services and capabilities](#M01.1)
      + [Compare Azure SQL services](#M01.1.1)
      + [SQL Server on Azure Virtual Machines](#M01.1.2)
        * [Business benefits](#M01.1.2.1)
      + [Azure SQL Database Managed Instance](#M01.1.3)
        * [Use cases](#M01.1.3.1)
        * [Business benefits](#M01.1.3.2)
      + [Azure SQL Database](#M01.1.4)
        * [Single Database](#M01.1.4.1)
        * [Elastic Pool](#M01.1.4.2)
        * [Use cases](#M01.1.4.3)
        * [Business benefits](#M01.1.4.4)
    - [Describe Azure services for open-source databases](#M01.2)
      + [What are MySQL, MariaDB, and PostgreSQL?](#M01.2.1)
      + [Azure Database for MySQL](#M01.2.2)
        * [Benefits of Azure Database for MySQL](#M01.2.2.1)
      + [Azure Database for MariaDB](#M01.2.3)
        * [Benefits of Azure Database for MariaDB](#M01.2.3.1)
      + [Azure Database for PostgreSQL](#M01.2.4)
        * [Azure Database for PostgreSQL Flexible Server](#M01.2.4.1)
        * [Benefits of Azure Database for PostgreSQL](#M01.2.4.2)
    - [Knowledge check](#M01.5)










<a name="M01"></a>
# [Explore relational database services in Azure](https://learn.microsoft.com/en-us/training/modules/explore-provision-deploy-relational-database-offerings-azure/)



<a name="M01.1"></a>
## Describe Azure SQL services and capabilities

Azure SQL là thuật ngữ tổng quát để chỉ một họ các dịch vụ cơ sở dữ liệu dựa trên Microsoft SQL Server trong Azure. Các dịch vụ cụ thể của Azure SQL bao gồm:

- **SQL Server on Azure Virtual Machines (VMs)** - Một máy ảo chạy trên Azure với một bản cài đặt SQL Server. Việc sử dụng máy ảo làm cho lựa chọn này trở thành một giải pháp cơ sở hạ tầng dưới dạng dịch vụ (infrastructure-as-a-service - IaaS) ảo hóa cơ sở hạ tầng phần cứng cho tính toán, lưu trữ và mạng trong Azure; là một lựa chọn tuyệt vời cho việc di chuyển "lift and shift" các cài đặt SQL Server đang tồn tại trên nền tảng địa phương lên đám mây.
- **Azure SQL Managed Instance** - Một lựa chọn dưới dạng nền tảng dịch vụ (platform-as-a-service - PaaS) cung cấp khả năng tương thích gần như 100% với các phiên bản SQL Server đang tồn tại trên nền tảng địa phương trong khi trừu tượng hóa phần cứng và hệ điều hành bên dưới. Dịch vụ này bao gồm quản lý cập nhật phần mềm tự động, sao lưu và các tác vụ bảo trì khác, giảm bớt gánh nặng quản trị hỗ trợ một phiên bản máy chủ cơ sở dữ liệu.
- **Azure SQL Database** - Một dịch vụ cơ sở dữ liệu PaaS được quản lý hoàn toàn, có khả năng mở rộng cao, được thiết kế cho đám mây. Dịch vụ này bao gồm các khả năng cơ bản của cấp độ cơ sở dữ liệu của SQL Server trên nền tảng địa phương và là một lựa chọn tốt khi bạn cần tạo một ứng dụng mới trên đám mây.
- **Azure SQL Edge** - Một công cụ SQL được tối ưu hóa cho các kịch bản Internet-of-things (IoT) cần làm việc với streaming time-series data.

```
!Note
Azure SQL Edge được bao gồm trong danh sách này để đầy đủ. Trong module này, chúng tôi sẽ tập trung 
vào các tùy chọn khác cho các kịch bản cơ sở dữ liệu quan hệ tổng quát hơn.
```







<a name="M01.1.1"></a>
### Compare Azure SQL services

![image](https://user-images.githubusercontent.com/62134515/221515155-7db5bea8-f2a3-46f0-b5f9-b4f72ec6c9e0.png)







<a name="M01.1.2"></a>
### SQL Server on Azure Virtual Machines

SQL Server on Virtual Machines cho phép bạn sử dụng các phiên bản đầy đủ của SQL Server trên Cloud mà không cần quản lý bất kỳ on-premises hardware nào. Đây là một ví dụ về phương pháp IaaS.

SQL Server chạy trên một máy ảo Azure hiệu quả giống như cơ sở dữ liệu chạy trên on-premises hardware thực. Di chuyển từ hệ thống on-premises sang một máy ảo Azure không khác gì việc di chuyển các cơ sở dữ liệu từ một máy chủ on-premises sang một máy chủ on-premises khác.

Phương pháp này phù hợp cho các ứng dụng yêu cầu truy cập các tính năng của hệ điều hành có thể không được hỗ trợ ở mức độ PaaS. SQL virtual machine đã sẵn sàng cho các ứng dụng hiện có đòi hỏi di chuyển nhanh chóng lên Cloud với sự thay đổi tối thiểu. Bạn cũng có thể sử dụng SQL Server trên các máy ảo Azure để mở rộng các ứng dụng on-premises hiện có lên Cloud trong các triển khai kết hợp.

```
!Note
Một triển khai kết hợp là một hệ thống trong đó một phần hoạt động được thực hiện on-premises (tại chỗ), 
và một phần khác được thực hiện trên cloud. Cơ sở dữ liệu của bạn có thể là một phần của một hệ thống 
lớn hơn chạy on-premises, tuy nhiên các phần tử cơ sở dữ liệu có thể được lưu trữ trên đám mây.
```

Bạn có thể sử dụng SQL Server trên máy ảo để phát triển và kiểm thử các ứng dụng SQL Server truyền thống. Với một máy ảo, bạn có đầy đủ quyền quản trị đối với DBMS và hệ điều hành. Đây là lựa chọn hoàn hảo khi một tổ chức đã có tài nguyên IT sẵn có để duy trì các máy ảo.

Những khả năng này cho phép bạn:

- Tạo các kịch bản phát triển và kiểm thử nhanh chóng khi bạn không muốn mua phần cứng SQL Server không sản xuất on-premises.
- Trở thành lift-and-shift sẵn sàng cho các ứng dụng hiện có yêu cầu di chuyển nhanh chóng đến cloud với sự thay đổi tối thiểu hoặc không có thay đổi.
- Mở rộng nền tảng trên đó SQL Server đang chạy, bằng cách phân bổ nhiều bộ nhớ, sức mạnh CPU và không gian đĩa cho máy ảo. Bạn có thể nhanh chóng thay đổi kích thước máy ảo Azure mà không cần phải cài đặt lại phần mềm đang chạy trên đó.










<a name="M01.1.2.1"></a>
#### Business benefits

Chạy SQL Server trên các máy ảo cho phép bạn đáp ứng các nhu cầu kinh doanh đa dạng và độc đáo thông qua việc kết hợp triển khai on-premises và cloud-hosted, trong khi sử dụng cùng một bộ sản phẩm máy chủ, công cụ phát triển và chuyên môn qua các môi trường này.

Việc chuyển DBMS của doanh nghiệp sang một dịch vụ được quản lý hoàn toàn không phải lúc nào cũng đơn giản. Có thể có các yêu cầu cụ thể phải được đáp ứng để di chuyển sang một dịch vụ được quản lý, điều này đòi hỏi phải thay đổi cơ sở dữ liệu và các ứng dụng sử dụng nó. Vì lý do này, sử dụng các máy ảo có thể cung cấp một giải pháp, nhưng việc sử dụng chúng không loại bỏ nhu cầu quản trị DBMS của bạn một cách cẩn thận như khi triển khai on-premises.







<a name="M01.1.3"></a>
## Azure SQL Database Managed Instance

Azure SQL Managed Instance là một phiên bản SQL Server đầy đủ được điều khiển trong cloud. Bạn có thể cài đặt nhiều cơ sở dữ liệu trên cùng một phiên bản. Bạn hoàn toàn kiểm soát phiên bản này giống như bạn làm với một máy chủ on-premises. SQL Managed Instance tự động hóa sao lưu, cập nhật phần mềm, giám sát cơ sở dữ liệu và các tác vụ chung khác, nhưng bạn hoàn toàn kiểm soát bảo mật và phân bổ tài nguyên cho cơ sở dữ liệu của mình. Bạn có thể tìm thông tin chi tiết tại đây: "[What is Azure SQL Managed Instance?](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/sql-managed-instance-paas-overview?view=azuresql)".

Các phiên bản được quản lý phụ thuộc vào các dịch vụ Azure khác như Azure Storage for backups, Azure Event Hubs for telemetry, Azure Active Directory for authentication, Azure Key Vault for Transparent Data Encryption (TDE) và một số dịch vụ nền tảng Azure cung cấp các tính năng bảo mật và hỗ trợ. Các phiên bản quản lý kết nối với các dịch vụ này.

Tất cả các thông tin truyền tải đều được mã hóa và ký bằng chứng chỉ. Để kiểm tra tính đáng tin cậy của các bên liên lạc, phiên bản quản lý liên tục xác minh các chứng chỉ này thông qua danh sách thu hồi chứng chỉ. Nếu các chứng chỉ bị thu hồi, phiên bản quản lý sẽ đóng kết nối để bảo vệ dữ liệu.










<a name="M01.1.3.1"></a>
### Use cases

Hãy xem xét Azure SQL Managed Instance nếu bạn muốn lift-and-shift một SQL Server instance trên nền tảng on-premises và tất cả các cơ sở dữ liệu của nó lên cloud, mà không phải chịu chi phí quản lý khi chạy SQL Server trên máy ảo.

Azure SQL Managed Instance cung cấp các tính năng không có sẵn trong Azure SQL Database (được thảo luận dưới đây). Nếu hệ thống của bạn sử dụng các tính năng như linked servers, Service Broker (hệ thống xử lý tin nhắn có thể được sử dụng để phân phối công việc trên các máy chủ) hoặc Database Mail (cho phép cơ sở dữ liệu của bạn gửi tin nhắn email cho người dùng), thì bạn nên sử dụng managed instance. Để kiểm tra tính tương thích với hệ thống on-premises hiện có, bạn có thể cài đặt [Data Migration Assistant (DMA)](https://www.microsoft.com/en-us/download/details.aspx?id=53595). Công cụ này phân tích cơ sở dữ liệu của bạn trên SQL Server và báo cáo bất kỳ vấn đề nào có thể chặn quá trình di chuyển sang managed instance.










<a name="M01.1.3.2"></a>
### Business benefits

Azure SQL Managed Instance cho phép quản trị viên hệ thống tiết kiệm thời gian hơn cho các nhiệm vụ quản trị do dịch vụ thực hiện hoặc đơn giản hóa các tác vụ đó. Các tác vụ tự động bao gồm cài đặt và vá phần mềm hệ thống và hệ thống quản trị cơ sở dữ liệu, thay đổi và cấu hình động của các trường hợp, sao lưu, sao chép cơ sở dữ liệu (bao gồm các cơ sở dữ liệu hệ thống), cấu hình tính sẵn cao và cấu hình các luồng dữ liệu giám sát sức khỏe và hiệu suất.

Azure SQL Managed Instance có khả năng tương thích gần như 100% với SQL Server Enterprise Edition, chạy trên nền tảng on-premises.

Azure SQL Managed Instance hỗ trợ công cụ đăng nhập cơ sở dữ liệu SQL Server và đăng nhập tích hợp với Azure Active Directory (AD). Công cụ đăng nhập cơ sở dữ liệu SQL Server bao gồm tên người dùng và mật khẩu. Bạn phải nhập thông tin đăng nhập mỗi khi kết nối với máy chủ. Đăng nhập Azure AD sử dụng các thông tin đăng nhập liên quan đến đăng nhập máy tính hiện tại của bạn và bạn không cần cung cấp chúng mỗi khi kết nối với máy chủ.











<a name="M01.1.4"></a>
## Azure SQL Database

Azure SQL Database là một dịch vụ PaaS từ Microsoft. Bạn tạo một máy chủ cơ sở dữ liệu quản lý trên cloud, sau đó triển khai các cơ sở dữ liệu của bạn trên máy chủ này.

```
!Note
Một SQL Database server là một cấu trúc logic hoạt động như một điểm quản trị trung tâm 
cho nhiều cơ sở dữ liệu đơn lẻ hoặc gộp, các đăng nhập, các quy tắc tường lửa, 
các quy tắc kiểm tra đăng nhập, và các nhóm chuyển đổi dự phòng.
```

Azure SQL Database có sẵn dưới dạng Single Database hoặc Elastic Pool.





<a name="M01.1.4.1"></a>
### Single Database

Tùy chọn này cho phép bạn nhanh chóng thiết lập và chạy một single SQL Server database. Bạn tạo và chạy một máy chủ cơ sở dữ liệu trong cloud và truy cập cơ sở dữ liệu của mình thông qua máy chủ này. Microsoft quản lý máy chủ, vì vậy tất cả những gì bạn cần làm là cấu hình cơ sở dữ liệu, tạo bảng của bạn và điền dữ liệu vào chúng. Bạn có thể mở rộng cơ sở dữ liệu nếu bạn cần thêm không gian lưu trữ, bộ nhớ hoặc sức mạnh xử lý. Theo mặc định, tài nguyên được cấp phát trước và bạn được tính phí theo giờ cho các tài nguyên mà bạn đã yêu cầu. Bạn cũng có thể chỉ định một cấu hình serverless. Trong cấu hình này, Microsoft tạo ra máy chủ của riêng mình, có thể được chia sẻ bởi các cơ sở dữ liệu thuộc về các đăng ký Azure khác nhau. Microsoft đảm bảo tính riêng tư của cơ sở dữ liệu của bạn. Cơ sở dữ liệu của bạn tự động mở rộng và tài nguyên được cấp hoặc giải phóng theo yêu cầu.




<a name="M01.1.4.2"></a>
### Elastic Pool

Tùy chọn này tương tự như Single Database, ngoại trừ việc mặc định nhiều cơ sở dữ liệu có thể chia sẻ các tài nguyên như bộ nhớ, không gian lưu trữ dữ liệu và sức mạnh xử lý thông qua multiple-tenancy. Các tài nguyên được gọi là một pool. Bạn tạo ra pool và chỉ các cơ sở dữ liệu của bạn có thể sử dụng pool. Mô hình này hữu ích nếu bạn có các cơ sở dữ liệu có yêu cầu tài nguyên thay đổi theo thời gian và giúp bạn giảm chi phí. Ví dụ, cơ sở dữ liệu lương của bạn có thể yêu cầu nhiều sức mạnh CPU vào cuối mỗi tháng khi bạn xử lý việc xử lý lương, nhưng vào những thời điểm khác, cơ sở dữ liệu có thể ít hoạt động hơn nhiều. Bạn có thể có một cơ sở dữ liệu khác được sử dụng để chạy các báo cáo. Cơ sở dữ liệu này có thể hoạt động trong vài ngày giữa tháng khi báo cáo quản lý được tạo ra, nhưng với load nhẹ hơn trong những lần khác. Elastic Pool cho phép bạn sử dụng các tài nguyên có sẵn trong pool và sau đó giải phóng các tài nguyên sau khi xử lý hoàn thành.




<a name="M01.1.4.3"></a>
### Use cases

Azure SQL Database cung cấp cho bạn tùy chọn tốt nhất với chi phí thấp và yêu cầu quản trị tối thiểu. Tuy nhiên, nó không hoàn toàn tương thích với các cài đặt SQL Server trên nền tảng on-premises. Nó thường được sử dụng trong các dự án cloud mới trong đó thiết kế ứng dụng có thể đáp ứng bất kỳ thay đổi nào cần thiết đối với ứng dụng của bạn.

```
!Note
Bạn có thể sử dụng Data Migration Assistant để phát hiện các vấn đề tương thích với cơ sở dữ liệu của bạn có thể ảnh hưởng đến chức năng cơ sở dữ liệu trong Azure SQL Database. 
```

For more information, see [Overview of Data Migration Assistant](https://learn.microsoft.com/en-us/sql/dma/dma-overview?view=sql-server-ver16).

Azure SQL Database thường được sử dụng cho:

- Các ứng dụng cloud hiện đại cần sử dụng các tính năng SQL Server ổn định nhất.
- Các ứng dụng yêu cầu khả năng sẵn sàng cao.
- Các hệ thống có variable load cần máy chủ cơ sở dữ liệu có thể tự động mở rộng và thu hẹp nhanh chóng.








<a name="M01.1.4.4"></a>
### Business benefits

Azure SQL Database tự động cập nhật và vá phần mềm SQL Server để đảm bảo rằng bạn luôn chạy phiên bản mới nhất và an toàn nhất của dịch vụ.

Các tính năng mở rộng của Azure SQL Database đảm bảo rằng bạn có thể tăng tài nguyên để lưu trữ và xử lý dữ liệu mà không cần phải thực hiện một bản nâng cấp thủ công đắt tiền.

Dịch vụ này đảm bảo tính khả dụng cao, để đảm bảo rằng cơ sở dữ liệu của bạn luôn sẵn sàng ít nhất 99,995%. Azure SQL Database hỗ trợ khôi phục point-in-time, cho phép bạn phục hồi cơ sở dữ liệu về trạng thái nó đang ở bất kỳ điểm nào trong quá khứ. Các cơ sở dữ liệu có thể được sao chép sang các khu vực khác để cung cấp độ bền cao hơn và khả năng phục hồi sau sự cố.

Advanced threat protection (ATP) cung cấp khả năng bảo mật nâng cao, bao gồm các tính năng đánh giá lỗ hổng để giúp phát hiện và khắc phục các vấn đề bảo mật tiềm ẩn trong cơ sở dữ liệu của bạn. ATP cũng phát hiện các hoạt động bất thường cho thấy các nỗ lực không bình thường và có thể gây hại để truy cập hoặc khai thác cơ sở dữ liệu của bạn. Nó liên tục giám sát cơ sở dữ liệu của bạn để phát hiện các hoạt động đáng ngờ và cung cấp cảnh báo bảo mật ngay lập tức về các lỗ hổng tiềm ẩn, các cuộc tấn công SQL injection và các mô hình truy cập cơ sở dữ liệu bất thường. Các cảnh báo phát hiện các hoạt động đáng ngờ cung cấp chi tiết về các hoạt động đáng ngờ và đề xuất các hành động để điều tra và giảm thiểu rủi ro.

Auditing trong Azure SQL Database theo dõi các sự kiện của cơ sở dữ liệu và ghi chúng vào một nhật ký kiểm tra trong tài khoản lưu trữ Azure của bạn. Kiểm tra có thể giúp bạn duy trì tuân thủ quy định, hiểu hoạt động của cơ sở dữ liệu và có cái nhìn về những sự khác biệt và sự bất thường có thể cho thấy các vấn đề kinh doanh hoặc vi phạm an ninh nghi ngờ.

SQL Database giúp bảo vệ dữ liệu của bạn bằng cách cung cấp mã hóa bảo vệ dữ liệu được lưu trữ trong cơ sở dữ liệu (at rest) và khi nó được truyền qua mạng (in motion).






<a name="M01.2"></a>
## Describe Azure services for open-source databases

Ngoài các dịch vụ Azure SQL, các dịch vụ dữ liệu Azure cũng có sẵn cho các hệ thống cơ sở dữ liệu quan hệ phổ biến khác, bao gồm MySQL, MariaDB và PostgreSQL. Lý do chính cho các dịch vụ này là để cho phép các tổ chức sử dụng chúng trong các ứng dụng trên nền tảng đang sử dụng chuyển sang Azure nhanh chóng, mà không cần thực hiện những thay đổi đáng kể cho ứng dụng của họ.







<a name="M01.2.1"></a>
### What are MySQL, MariaDB, and PostgreSQL?

MySQL, MariaDB và PostgreSQL là các hệ thống quản lý cơ sở dữ liệu quan hệ được thiết kế để phục vụ các chuyên ngành khác nhau.

MySQL bắt đầu ra đời như một hệ thống quản lý cơ sở dữ liệu mã nguồn mở dễ sử dụng. Đây là hệ thống quản lý cơ sở dữ liệu quan hệ mã nguồn mở hàng đầu dành cho các ứng dụng Linux, Apache, MySQL và PHP (LAMP). MySQL có nhiều phiên bản, bao gồm phiên bản Cộng đồng, Tiêu chuẩn và Doanh nghiệp. Phiên bản Cộng đồng có sẵn miễn phí và đã từng được ưa chuộng như một hệ thống quản lý cơ sở dữ liệu cho các ứng dụng web chạy trên nền Linux. Các phiên bản cũng có sẵn cho Windows. Phiên bản Tiêu chuẩn cung cấp hiệu suất cao hơn và sử dụng công nghệ lưu trữ dữ liệu khác. Phiên bản Doanh nghiệp cung cấp một bộ công cụ và tính năng toàn diện, bao gồm tính bảo mật, khả năng sẵn có và khả năng mở rộng tốt hơn. Phiên bản Tiêu chuẩn và Doanh nghiệp là những phiên bản được sử dụng phổ biến nhất bởi các tổ chức thương mại, tuy nhiên, các phiên bản này không miễn phí.

MariaDB là một hệ thống quản lý cơ sở dữ liệu mới hơn, được tạo ra bởi các nhà phát triển ban đầu của MySQL. Sau đó, động cơ cơ sở dữ liệu đã được viết lại và tối ưu hóa để cải thiện hiệu suất. MariaDB cung cấp tính tương thích với Oracle Database (một hệ thống quản lý cơ sở dữ liệu thương mại phổ biến khác). Một tính năng đáng chú ý của MariaDB là khả năng hỗ trợ dữ liệu thời gian tích hợp sẵn. Một bảng có thể chứa nhiều phiên bản dữ liệu, cho phép ứng dụng truy vấn dữ liệu khi nó xuất hiện ở một thời điểm nào đó trong quá khứ.

PostgreSQL là một hệ thống quản lý cơ sở dữ liệu đối tượng-quan hệ kết hợp. Bạn có thể lưu trữ dữ liệu trong các bảng quan hệ, nhưng cơ sở dữ liệu PostgreSQL cũng cho phép bạn lưu trữ các loại dữ liệu tùy chỉnh, với các thuộc tính không quan hệ riêng của chúng. Hệ thống quản lý cơ sở dữ liệu này có tính mở rộng; bạn có thể thêm các module mã vào cơ sở dữ liệu, các module này có thể chạy bởi các truy vấn. Một tính năng chính khác là khả năng lưu trữ và xử lý dữ liệu hình học, chẳng hạn như đường thẳng, vòng tròn và đa giác.

PostgreSQL có ngôn ngữ truy vấn riêng gọi là pgsql. Ngôn ngữ này là một biến thể của ngôn ngữ truy vấn quan hệ chuẩn, SQL, với các tính năng cho phép bạn viết các thủ tục lưu trữ chạy bên trong cơ sở dữ liệu.











<a name="M01.2.2"></a>
### Azure Database for MySQL

![image](https://user-images.githubusercontent.com/62134515/221767897-b85b3370-7f81-43c7-8d20-b9afe7f8c40c.png)








<a name="M01.2.2.1"></a>
#### Benefits of Azure Database for MySQL








<a name="M01.2.3"></a>
### Azure Database for MariaDB

![image](https://user-images.githubusercontent.com/62134515/221767925-03be905e-0211-4d95-8975-3d0643472020.png)





<a name="M01.2.3.1"></a>
#### Benefits of Azure Database for MariaDB





<a name="M01.2.4"></a>
### Azure Database for PostgreSQL

![image](https://user-images.githubusercontent.com/62134515/221767967-d1b0927f-87ac-4586-8144-9539c3c5e62a.png)







<a name="M01.2.4.1"></a>
#### Azure Database for PostgreSQL Flexible Server







<a name="M01.2.4.2"></a>
#### Benefits of Azure Database for PostgreSQL

















<a name="M01.5"></a>
## Knowledge check

![image](https://user-images.githubusercontent.com/62134515/221415531-b22e84e0-6fb5-4d86-9234-0c323557400a.png)











