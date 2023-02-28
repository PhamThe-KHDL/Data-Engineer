# Mục Lục

* [**Explore relational database services in Azure**](#M01)
    - [Describe Azure SQL services and capabilities](#M01.1)
      + [Compare Azure SQL services](#M01.1.1)
      + [SQL Server on Azure Virtual Machines](#M01.1.2)
        * [Business benefits](#M01.1.2.1)
      + [Azure SQL Database Managed Instance](#M01.1.3)
        * [Use cases](#M01.1.3.1)
        * [Business benefits](#M01.1.3.2)
    - [Understand normalization](#M01.2)
    - [Explore SQL](#M01.3)
      + [SQL statement types](#M01.3.1)
        * [DDL statements](#M01.3.1.1)
        * [DCL statements](#M01.3.1.2)
        * [DML statements](#M01.3.1.3)
    - [Describe database objects](#M01.4)
      + [What is a view?](#M01.4.1)
      + [What is a stored procedure?](#M01.4.2)
      + [What is an index?](#M01.4.3)
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















<a name="M01.1.3.2"></a>
### Business benefits













<a name="M01.3"></a>
## Explore SQL

SQL là viết tắt của Structured Query Language, được sử dụng để giao tiếp với cơ sở dữ liệu quan hệ. Đây là ngôn ngữ tiêu chuẩn cho các hệ thống quản lý cơ sở dữ liệu quan hệ. Các câu lệnh SQL được sử dụng để thực hiện các tác vụ như cập nhật dữ liệu trong cơ sở dữ liệu hoặc truy xuất dữ liệu từ cơ sở dữ liệu. Một số hệ thống quản lý cơ sở dữ liệu quan hệ thông dụng sử dụng SQL bao gồm Microsoft SQL Server, MySQL, PostgreSQL, MariaDB và Oracle.

```
!Note
SQL ban đầu được chuẩn hóa bởi American National Standards Institute (ANSI) vào năm 1986 và bởi International 
Organization for Standardization (ISO) vào năm 1987. Kể từ đó, tiêu chuẩn đã được mở rộng nhiều lần khi 
các nhà cung cấp cơ sở dữ liệu quan hệ đã thêm tính năng mới vào hệ thống của họ. Ngoài ra, hầu hết 
các nhà cung cấp cơ sở dữ liệu đều bao gồm các phần mở rộng độc quyền của riêng họ không phải là một phần 
của tiêu chuẩn, điều này đã dẫn đến một loạt các phiên bản SQL.
```

Bạn có thể sử dụng các câu lệnh SQL như SELECT, INSERT, UPDATE, DELETE, CREATE và DROP để thực hiện hầu hết mọi thứ bạn cần với cơ sở dữ liệu. Mặc dù các câu lệnh SQL này là một phần của tiêu chuẩn SQL, nhiều hệ thống quản lý cơ sở dữ liệu cũng có các phần mở rộng độc quyền của riêng họ để xử lý các chi tiết cụ thể của hệ thống quản lý cơ sở dữ liệu đó. Các phần mở rộng này cung cấp chức năng không được bao gồm trong tiêu chuẩn SQL, và bao gồm các lĩnh vực như quản lý bảo mật và lập trình. Ví dụ, Microsoft SQL Server và các dịch vụ cơ sở dữ liệu Azure dựa trên động cơ cơ sở dữ liệu SQL Server sử dụng Transact-SQL. Bản triển khai này bao gồm các phần mở rộng độc quyền để viết các procedures và triggers (mã ứng dụng có thể được lưu trữ trong cơ sở dữ liệu) và quản lý tài khoản người dùng. PostgreSQL và MySQL cũng có các phiên bản riêng của các tính năng này.

Một số phiên bản SQL phổ biến bao gồm:

- *Transact-SQL (T-SQL)*. Phiên bản SQL này được sử dụng bởi Microsoft SQL Server và các dịch vụ Azure SQL.
- *pgSQL*. Đây là phiên bản có các phần mở rộng được thực hiện trong PostgreSQL.
- *PL/SQL*. Đây là phiên bản được sử dụng bởi Oracle. PL/SQL viết tắt của Procedural Language/SQL.

Người dùng có kế hoạch làm việc với một hệ thống cơ sở dữ liệu cụ thể nên học các chi tiết về phiên bản SQL và nền tảng SQL ưa thích của họ.

```
!Note
Các ví dụ code SQL trong module này dựa trên phiên bản Transact-SQL, trừ khi có chỉ dẫn khác.
Cú pháp cho các phiên bản khác thường tương tự, nhưng có thể khác nhau ở một số chi tiết.
```






<a name="M01.3.1"></a>
### SQL statement types

Các câu lệnh SQL được nhóm thành ba nhóm logic chính:

- Ngôn ngữ định nghĩa dữ liệu (Data Definition Language - DDL)
- Ngôn ngữ điều khiển dữ liệu (Data Control Language - DCL)
- Ngôn ngữ thao tác dữ liệu (Data Manipulation Language - DML)









<a name="M01.3.1.1"></a>
#### DDL statements

Bạn sử dụng các câu lệnh DDL để create, modify, và remove tables và other objects trong cơ sở dữ liệu (table, stored procedures, views, vv.).

Các câu lệnh DDL phổ biến nhất là:

| Statement | Description |
| ----- | ----- |
| CREATE | Create a new object in the database, such as a table or a view. |
| ALTER | Modify the structure of an object. For instance, altering a table to add a new column. |
| DROP | Remove an object from the database. |
| RENAME | Rename an existing object. |

```
!Warning
The DROP statement is very powerful. When you drop a table, all the rows in that table are lost. 
Unless you have a backup, you won't be able to retrieve this data.
```

Ví dụ sau tạo một bảng mới trong cơ sở dữ liệu. Các mục nằm giữa dấu ngoặc đơn chỉ định chi tiết của mỗi cột, bao gồm tên, kiểu dữ liệu, liệu cột có bắt buộc phải chứa giá trị không (NOT NULL), và liệu dữ liệu trong cột được sử dụng để xác định duy nhất một hàng (PRIMARY KEY). Mỗi bảng nên có một khóa chính, tuy nhiên SQL không bắt buộc việc này.

```
!Note
Các cột được đánh dấu là NOT NULL được gọi là các cột bắt buộc. Nếu bạn bỏ qua mệnh đề NOT NULL, 
bạn có thể tạo các hàng không chứa giá trị trong cột. Một cột trống trong một hàng được gọi là có giá trị NULL.
```

```SQL
CREATE TABLE Product
(
    ID INT PRIMARY KEY,
    Name VARCHAR(20) NOT NULL,
    Price DECIMAL NULL
);
```

Định dạng dữ liệu có sẵn cho các cột trong một bảng sẽ khác nhau giữa các hệ thống quản lý cơ sở dữ liệu. Tuy nhiên, hầu hết các hệ thống quản lý cơ sở dữ liệu hỗ trợ các kiểu dữ liệu số như INT (số nguyên) , DECIMAL (số thập phân), và các loại chuỗi như VARCHAR (VARCHAR là viết tắt của variable length character data). Để biết thêm thông tin, hãy xem tài liệu cho hệ thống quản lý cơ sở dữ liệu được chọn của bạn.







<a name="M01.3.1.2"></a>
#### DDL statements

Các quản trị cơ sở dữ liệu thường sử dụng các câu lệnh DCL để quản lý truy cập vào các đối tượng trong cơ sở dữ liệu bằng cách cấp, từ chối hoặc thu hồi quyền truy cập cho các người dùng hoặc nhóm cụ thể.

Ba câu lệnh DCL chính là:

| Statement | Description |
| ----- | ----- |
| GRANT | Grant permission to perform specific actions |
| DENY | Deny permission to perform specific actions |
| REVOKE | Remove a previously granted permission |

Ví dụ, câu lệnh GRANT sau cho phép người dùng có tên là user1 đọc, chèn và sửa đổi dữ liệu trong bảng Product.

```SQL
GRANT SELECT, INSERT, UPDATE
ON Product
TO user1;
```










<a name="M01.3.1.3"></a>
#### DDL statements

Bạn sử dụng các lệnh DML để thao tác với các hàng trong các bảng. Những lệnh này cho phép bạn truy vấn dữ liệu, chèn các hàng mới hoặc sửa đổi các hàng đã tồn tại. Bạn cũng có thể xóa các hàng nếu bạn không còn cần chúng nữa.

Bốn lệnh DML chính là:

| Statement | Description |
| ----- | ----- |
| SELECT | Read rows from a table |
| INSERT | Insert new rows into a table |
| UPDATE | Modify data in existing rows |
| DELETE | Delete existing rows |

Định dạng cơ bản của một câu lệnh INSERT sẽ chèn một hàng một lần. Mặc định, các câu lệnh SELECT, UPDATE và DELETE được áp dụng cho mọi hàng trong bảng. Thông thường bạn sẽ áp dụng một điều kiện WHERE với các câu lệnh này để chỉ định tiêu chí; chỉ các hàng phù hợp với các tiêu chí này sẽ được lựa chọn, cập nhật hoặc xóa.

```
! Warning
SQL không cung cấp những thông báo "are you sure?" nên hãy cẩn thận khi sử dụng DELETE 
hoặc UPDATE mà không có điều kiện WHERE vì bạn có thể mất hoặc thay đổi rất nhiều dữ liệu.
```

Đoạn code sau là một ví dụ về câu lệnh SQL chọn tất cả các cột (được chỉ định bởi \*) từ bảng **Customer** trong đó giá trị cột **City** là "Seattle":

```SQL
SELECT *
FROM Customer
WHERE City = 'Seattle';
```

Để truy xuất chỉ một tập hợp cột cụ thể từ bảng, bạn liệt kê chúng trong mệnh đề SELECT, như sau:

```SQL
SELECT FirstName, LastName, Address, City
FROM Customer
WHERE City = 'Seattle';
```

Nếu một truy vấn trả về nhiều hàng, chúng không nhất thiết phải xuất hiện theo bất kỳ thứ tự cụ thể nào. Nếu bạn muốn sắp xếp dữ liệu, bạn có thể thêm một mệnh đề ORDER BY. Dữ liệu sẽ được sắp xếp theo cột được chỉ định:

```SQL
SELECT FirstName, LastName, Address, City
FROM Customer
WHERE City = 'Seattle'
ORDER BY LastName;
```

Bạn cũng có thể chạy các câu lệnh SELECT để lấy dữ liệu từ nhiều bảng sử dụng mệnh đề JOIN. Các join chỉ ra cách các hàng trong một bảng liên kết với các hàng trong bảng khác để xác định dữ liệu nào sẽ được trả về. Một điều kiện JOIN điển hình sẽ phù hợp với khóa ngoại từ một bảng và khóa chính tương ứng của nó trong bảng khác.

Câu truy vấn sau đây cho thấy một ví dụ về việc kết nối các bảng **Customer** và **Order**. Câu truy vấn sử dụng *aliases* để viết tắt tên bảng khi chỉ định các cột cần lấy trong mệnh đề SELECT và các cột cần phù hợp trong mệnh đề JOIN.

```SQL
SELECT o.OrderNo, o.OrderDate, c.Address, c.City
FROM Order AS o
JOIN Customer AS c
ON o.Customer = c.ID
```

Ví dụ sau cho thấy cách sửa đổi một hàng hiện có bằng cách sử dụng SQL. Nó thay đổi giá trị của cột **Address** trong bảng **Customer** cho các hàng có giá trị 1 trong cột **ID**. Tất cả các hàng khác vẫn giữ nguyên:

```SQL
UPDATE Customer
SET Address = '123 High St.'
WHERE ID = 1;
```

```
!Warning
Nếu bạn bỏ qua mệnh đề WHERE, một câu lệnh UPDATE sẽ sửa đổi tất cả các hàng trong bảng.
```

Sử dụng lệnh DELETE để xóa các hàng. Bạn chỉ định bảng để xóa từ đó và một mệnh đề WHERE xác định các hàng cần được xóa:

```SQL
DELETE FROM Product
WHERE ID = 162;
```

```
!Warning
Nếu bạn bỏ qua mệnh đề WHERE, một câu lệnh DELETE sẽ xóa tất cả các hàng trong bảng.
```

Câu lệnh INSERT có một định dạng khác. Bạn chỉ định một bảng và các cột trong INTO, và một danh sách các giá trị được lưu trữ trong các cột này. SQL chuẩn chỉ hỗ trợ chèn một hàng vào một thời điểm, như được thể hiện trong ví dụ sau. Một số ngôn ngữ hỗ trợ bạn chỉ định nhiều lệnh VALUES để thêm nhiều hàng cùng một lúc:

```SQL
INSERT INTO Product(ID, Name, Price)
VALUES (99, 'Drill', 4.99);
```

```
!Note
Topic này mô tả một số câu lệnh và cú pháp SQL cơ bản để giúp bạn hiểu cách SQL được sử dụng 
để làm việc với các đối tượng trong cơ sở dữ liệu. Nếu bạn muốn tìm hiểu thêm về truy vấn dữ liệu 
với SQL, hãy xem học tập bắt đầu truy vấn với Transact-SQL trên Microsoft Learn.
```












<a name="M01.4"></a>
## Describe database objects

Ngoài bảng, một cơ sở dữ liệu quan hệ có thể chứa các cấu trúc khác giúp tối ưu hóa tổ chức dữ liệu, đóng gói các hành động chương trình và cải thiện tốc độ truy cập. Trong unit này, bạn sẽ tìm hiểu về ba cấu trúc này một cách chi tiết hơn: views, stored procedures và indexes.







<a name="M01.4.1"></a>
### What is a view?

View là một bảng ảo dựa trên kết quả của một truy vấn SELECT. Bạn có thể xem view như một cửa sổ trên các hàng được chỉ định trong một hoặc nhiều bảng cơ sở dữ liệu gốc. Ví dụ, bạn có thể tạo một view trên các bảng **Order** và **Customer** để truy xuất dữ liệu đơn hàng và khách hàng và cung cấp một đối tượng duy nhất giúp dễ dàng xác định địa chỉ giao hàng cho các đơn hàng:

```SQL
CREATE VIEW Deliveries
AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.Customer = c.ID;
```

Bạn có thể truy vấn view và lọc dữ liệu giống như trên một bảng. Truy vấn sau đây tìm chi tiết đơn hàng cho khách hàng sống tại Seattle:

```SQL
SELECT OrderNo, OrderDate, LastName, Address
FROM Deliveries
WHERE City = 'Seattle';
```







<a name="M01.4.2"></a>
### What is a stored procedure?

Một stored procedure định nghĩa các câu lệnh SQL có thể được thực thi khi yêu cầu. Stored procedures được sử dụng để đóng gói logic lập trình trong cơ sở dữ liệu cho các hành động mà ứng dụng cần thực hiện khi làm việc với dữ liệu.

Bạn có thể định nghĩa một stored procedure với các tham số để tạo ra một giải pháp linh hoạt cho các hành động thông thường mà có thể cần được áp dụng vào dữ liệu dựa trên một khóa hoặc tiêu chí cụ thể. Ví dụ, stored procedure sau đây có thể được định nghĩa để thay đổi tên của một sản phẩm dựa trên ID sản phẩm được chỉ định.

```SQL
CREATE PROCEDURE RenameProduct
	@ProductID INT,
	@NewName VARCHAR(20)
AS
UPDATE Product
SET Name = @NewName
WHERE ID = @ProductID;
```

Khi một sản phẩm cần được đổi tên, bạn có thể thực thi stored procedure bằng cách truyền ID của sản phẩm và tên mới cần được gán:

```SQL
EXEC RenameProduct 201, 'Spanner';
```










<a name="M01.4.3"></a>
### What is an index?

Một index giúp bạn tìm kiếm dữ liệu trong một bảng. Hãy tưởng tượng một index trên một bảng giống như một index ở cuối cuốn sách. Một index sách chứa một tập hợp các tham chiếu được sắp xếp, với các trang mà mỗi tham chiếu xuất hiện. Khi bạn muốn tìm tham chiếu đến một mục trong cuốn sách, bạn tìm kiếm thông qua index. Bạn có thể sử dụng số trang trong index để đi trực tiếp đến các trang đúng trong sách. Nếu không có index, bạn có thể phải đọc toàn bộ cuốn sách để tìm các tham chiếu mà bạn đang tìm kiếm.

Khi bạn tạo một index trong cơ sở dữ liệu, bạn chỉ định một cột từ bảng và index chứa một bản sao của dữ liệu này được sắp xếp theo thứ tự, với các con trỏ đến các hàng tương ứng trong bảng. Khi người dùng chạy một truy vấn chỉ định cột này trong mệnh đề WHERE, hệ thống quản lý cơ sở dữ liệu có thể sử dụng index này để truy xuất dữ liệu nhanh hơn so với việc phải quét toàn bộ bảng từng hàng.

Ví dụ, bạn có thể sử dụng đoạn code sau để tạo một index trên cột **Name** của bảng **Product**:

```SQL
CREATE INDEX idx_ProductName
ON Product(Name);
```
Index tạo ra một cấu trúc dựa trên cây mà trình tối ưu truy vấn của hệ thống cơ sở dữ liệu có thể sử dụng để nhanh chóng tìm các hàng trong bảng **Product** dựa trên một **Name** cụ thể.

![image](https://user-images.githubusercontent.com/62134515/221414131-ac3cf302-2bab-4921-bab2-2a182eac73f3.png)

Đối với một bảng chứa ít hàng, sử dụng index có lẽ không hiệu quả hơn là đọc toàn bộ bảng và tìm các hàng được yêu cầu bởi truy vấn (trong trường hợp này, trình tối ưu truy vấn sẽ bỏ qua index). Tuy nhiên, khi một bảng có nhiều hàng, index có thể cải thiện đáng kể hiệu suất của các truy vấn.

Bạn có thể tạo nhiều index trên một bảng. Vì vậy, nếu bạn cũng muốn tìm sản phẩm dựa trên giá, việc tạo một index khác trên cột **Price** trong bảng **Product** có thể hữu ích. Tuy nhiên, index không miễn phí. Một index tiêu tốn không gian lưu trữ, và mỗi khi bạn chèn, cập nhật hoặc xóa dữ liệu trong một bảng, index cho bảng đó phải được bảo trì. Công việc bổ sung này có thể làm chậm các hoạt động chèn, cập nhật và xóa. Bạn phải cân bằng giữa việc có index để tăng tốc truy vấn và chi phí thực hiện các hoạt động khác.








<a name="M01.5"></a>
## Knowledge check

![image](https://user-images.githubusercontent.com/62134515/221415531-b22e84e0-6fb5-4d86-9234-0c323557400a.png)











