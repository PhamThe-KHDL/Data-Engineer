# Mục Lục

* [**Explore fundamental relational data concepts**](#M01)
    - [Understand relational data](#M01.1)
    - [Understand normalization](#M01.2)
    - [Explore SQL](#M01.3)
      + [Relational databases](#M01.3.1)
      + [Non-relational databases](#M01.3.2)
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






<a name="M01.3.1"></a>
### Relational databases











<a name="M01.3.2"></a>
### Non-relational databases











<a name="M01.4"></a>
## Explore transactional data processing









<a name="M01.5"></a>
## Explore analytical data processing













<a name="M01.6"></a>
## Knowledge check











