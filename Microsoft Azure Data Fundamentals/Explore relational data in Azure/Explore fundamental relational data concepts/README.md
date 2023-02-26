# Mục Lục

* [**Explore fundamental relational data concepts**](#M01)
    - [Understand relational data](#M01.1)
    - [Understand normalization](#M01.2)
    - [Explore SQL](#M01.3)
      + [SQL statement types](#M01.3.1)
        * [DDL statements](#M01.3.1.1)
        * [DCL statements](#M01.3.1.2)
        * [DML statements](#M01.3.1.3)
    - [Explore transactional data processing](#M01.4)
    - [Explore analytical data processing](#M01.5)
    - [Knowledge check](#M01.6)










<a name="M01"></a>
# [Explore fundamental relational data concepts](https://learn.microsoft.com/en-us/training/modules/explore-relational-data-offerings/)



<a name="M01.1"></a>
## Understand relational data 

Trong cơ sở dữ liệu quan hệ, bạn mô hình các tập hợp thực thể từ thế giới thực dưới dạng bảng. Một thực thể có thể là bất cứ thứ gì mà bạn muốn ghi lại thông tin; thường là các đối tượng và sự kiện quan trọng. Ví dụ, trong một hệ thống bán lẻ, bạn có thể tạo các bảng cho khách hàng, sản phẩm, đơn hàng và các item trong đơn hàng. Một bảng chứa các hàng và mỗi hàng đại diện cho một trường hợp của một thực thể. Trong trường hợp bán lẻ, mỗi hàng trong bảng khách hàng chứa dữ liệu cho một khách hàng duy nhất, mỗi hàng trong bảng sản phẩm xác định một sản phẩm duy nhất, mỗi hàng trong bảng đơn hàng đại diện cho một đơn hàng được thực hiện bởi một khách hàng, và mỗi hàng trong bảng item đại diện cho một sản phẩm được bao gồm trong một đơn hàng.

![image](https://user-images.githubusercontent.com/62134515/221326906-ab147d53-eba6-445a-a87c-185c17fcb155.png)

Các bảng quan hệ là một định dạng cho dữ liệu có cấu trúc, và mỗi hàng trong bảng có các cột giống nhau; tuy nhiên, trong một số trường hợp, không phải tất cả các cột đều cần có giá trị - ví dụ, một bảng khách hàng có thể bao gồm một cột MiddleName; mà có thể trống (hoặc NULL) cho các hàng đại diện cho khách hàng không có tên đệm hoặc tên đệm không biết.

Mỗi cột lưu trữ dữ liệu của một *kiểu dữ liệu (datatype)* cụ thể. Ví dụ, một cột Email trong bảng Customer có lẽ sẽ được xác định để lưu trữ dữ liệu character-based (text) (có thể có độ dài cố định hoặc biến đổi), một cột Price trong bảng Product có thể được xác định để lưu trữ dữ liệu decimal numeric, trong khi một cột Quantity trong bảng Order có thể bị giới hạn bởi giá trị số nguyên; và một cột OrderDate trong cùng bảng Order sẽ được xác định để lưu trữ các giá trị ngày/giờ. Các loại dữ liệu có sẵn mà bạn có thể sử dụng khi xác định một bảng phụ thuộc vào hệ thống cơ sở dữ liệu mà bạn đang sử dụng; tuy nhiên, có các loại dữ liệu tiêu chuẩn được xác định bởi Viện Tiêu chuẩn Quốc gia Hoa Kỳ (American National Standards Institute - ANSI) được hỗ trợ bởi hầu hết các hệ thống cơ sở dữ liệu.












<a name="M01.2"></a>
## Understand normalization

Normalization là thuật ngữ được sử dụng bởi các chuyên gia cơ sở dữ liệu để thiết kế schema (cấu trúc) giảm thiểu sự trùng lặp dữ liệu và bảo vệ tính toàn vẹn dữ liệu.

Mặc dù có nhiều quy tắc phức tạp xác định quá trình tái cấu trúc dữ liệu thành các cấp độ khác nhau của normalization, định nghĩa đơn giản cho mục đích thực tế như sau:

1. Tách mỗi thực thể thành một bảng riêng.
2. Tách từng thuộc tính riêng lẻ thành một cột riêng.
3. Xác định mỗi thể hiện thực thể (hàng) một cách độc nhất bằng cách sử dụng khóa chính (primary key).
4. Sử dụng cột khóa ngoại (foreign key) để liên kết các thực thể liên quan.

Để hiểu các nguyên tắc cốt lõi của normalization, giả sử bảng sau đây đại diện cho một bảng tính mà một công ty sử dụng để theo dõi doanh số bán hàng.


![image](https://user-images.githubusercontent.com/62134515/221387496-d61d6d16-9c0a-4537-af92-aa58ce9b33e2.png)

Lưu ý rằng thông tin chi tiết của khách hàng và sản phẩm bị nhân bản cho mỗi mặt hàng được bán; và tên khách hàng và địa chỉ bưu điện cùng với tên sản phẩm và giá cả được kết hợp trong cùng một ô trong bảng tính.

Bây giờ hãy xem cách normalization thay đổi dữ liệu được lưu trữ.

![image](https://user-images.githubusercontent.com/62134515/221387502-c0ba63aa-1bf5-42ce-9548-c65632e96b8a.png)

Mỗi thực thể được đại diện trong dữ liệu (khách hàng, sản phẩm, đơn hàng bán hàng và item) được lưu trữ trong bảng riêng của nó, và mỗi thuộc tính riêng lẻ của các thực thể đó được lưu trữ trong cột riêng của nó.

Việc ghi lại mỗi trường hợp của một thực thể như một hàng trong bảng riêng của thực thể đó loại bỏ sự trùng lặp dữ liệu. Ví dụ, để thay đổi địa chỉ của một khách hàng, bạn chỉ cần sửa đổi giá trị trong một hàng đơn.

Việc phân rã các thuộc tính thành các cột riêng biệt đảm bảo rằng mỗi giá trị được giới hạn trong một loại dữ liệu phù hợp - ví dụ, giá sản phẩm phải là giá trị thập phân, trong khi số lượng item phải là số nguyên. Ngoài ra, việc tạo ra các cột riêng biệt cung cấp một cấp độ chi tiết hữu ích trong dữ liệu để truy vấn - ví dụ, bạn có thể dễ dàng lọc khách hàng để tìm những người sống ở một thành phố cụ thể.

Các trường hợp của mỗi thực thể được định danh duy nhất bằng một ID hoặc giá trị khóa khác, được gọi là khóa chính (primary key); và khi một thực thể liên quan đến thực thể khác (ví dụ: một đơn hàng có khách hàng liên quan), khóa chính của thực thể liên quan được lưu trữ dưới dạng khóa ngoại (foreign key). Bạn có thể tra cứu địa chỉ của khách hàng (chỉ được lưu trữ một lần) cho mỗi bản ghi trong bảng Order bằng cách tham chiếu đến bản ghi tương ứng trong bảng Customer. Thông thường, một hệ quản trị cơ sở dữ liệu quan hệ (relational database management system - RDBMS) có thể áp dụng tính nguyên tắc của toàn vẹn tham chiếu để đảm bảo rằng giá trị nhập vào trường khóa ngoại phải có khóa chính tương ứng đã tồn tại trong bảng liên quan - ví dụ: ngăn không cho phép tạo đơn hàng cho khách hàng không tồn tại.

Trong một số trường hợp, một khóa (khóa chính hoặc khóa ngoại) có thể được định nghĩa là một khóa tổ hợp dựa trên sự kết hợp duy nhất của nhiều cột. Ví dụ: bảng LineItem trong ví dụ ở trên sử dụng một kết hợp độc nhất của OrderNo và ItemNo để xác định một mặt hàng trong một đơn hàng cụ thể.














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
để làm việc với các đối tượng trong cơ sở dữ liệu. Nếu bạn muốn tìm hiểu thêm về truy vấn dữ liệu với SQL, 
hãy xem học tập bắt đầu truy vấn với Transact-SQL trên Microsoft Learn.
```












<a name="M01.4"></a>
## Explore transactional data processing









<a name="M01.5"></a>
## Explore analytical data processing













<a name="M01.6"></a>
## Knowledge check











