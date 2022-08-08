# Data Engineer


Kiến thức, khái niệm cơ bản và cần thiết cho ngành Data Engineer (tự học)


## Data Engineer vs Data Scientists

### Data Engineer
<center>
    <img src="https://github.com/PhamThe-KHDL/Data-Engineer/blob/main/Images/DE.png" width="800" alt="DE" />
</center>

### Data Scientists
<center>
    <img src="https://github.com/PhamThe-KHDL/Data-Engineer/blob/main/Images/DS.png" width="800" alt="DE" />
</center>







## Khái niệm cơ bản

### DATA SOURCES (NGUỒN DỮ LIỆU):
- Là cơ sở dữ liệu thô (thường là cơ sở dữ liệu quan hệ) đến từ nhiều nguồn khác nhau như các ứng dụng business như Human Resource Management (HRM), Customer relationship management (CRM), phần mềm bán hàng, website thương mại điện tử…
- Có thể là bất cứ hệ quản trị cơ sở dữ liệu nào như MySQL, Oracle, SQL, DB2, …
- Thường được thiết kế theo mô hình cơ sở dữ liệu quan hệ (vì dạng mô hình này đang rất phổ biến trong thực tế)

### DATA WAREHOUSE (NHÀ KHO DỮ LIỆU):
- Là cơ sở dữ liệu được thiết kế theo mô hình khác với CSDL quan hệ và là nơi lưu trữ dữ liệu lâu dài của tổ chức
- Dữ liệu của Data Warehouse chỉ có thể đọc, không ghi hay cập nhật được và chỉ được cập nhật bởi gói ETL khi được vận hành bởi Integrating Server để chuyển đổi dữ liệu từ Data Sources vào Data Warehouse. Mình sẽ bàn kỹ hơn về Data Warehouse ở phần tiếp theo.

### DATA MINING (KHAI THÁC DỮ LIỆU):
- Là quá trình trích xuất thông tin dữ liệu đã qua xử lý (phù hợp với yêu cầu riêng của doanh nghiệp) từ Data Warehouse rồi kết hợp với các thuật toán để đưa ra các quyết định (hoặc dự đoán) có lợi cho việc kinh doanh của doanh nghiệp.
- Đây là một quá trình quan trọng trong BI, thông thường một doanh nghiệp muốn sử dụng giải pháp BI thường kèm theo về Data Mining.

### DATA PRESENTATION (TRÌNH BÀY DỮ LIỆU):
- Từ quá trình data mining, doanh nghiệp phải hiểu được cách làm ra các mô hình tối ưu hóa cho phép chúng ta xác định các giải pháp tốt nhất trong tập hợp các giải pháp được đưa ra.

### MAKING DECISIONS (RA QUYẾT ĐỊNH):
- Đưa ra sự lựa chọn và áp dụng thực tế của một quyết định cụ thể. Ngay cả khi các phương pháp BI được áp dụng thành công, thì việc lựa chọn quyết định thuộc về các nhà ra quyết định, những người nắm bắt được những thông tin không có cấu trúc để hiệu chỉnh các kết luận thông qua việc sử dụng các mô hình toán học.









## Những thuật ngữ thường gặp


### BIG DATA
- Là các tập dữ liệu có khối lượng lớn và phức tạp đến mức khó hoặc không thể sử dụng các phương pháp xử lý truyền thống để phân tích. Những tập dữ liệu lớn này có thể bao gồm các dữ liệu có cấu trúc, không có cấu trúc và bán cấu trúc.

### DATA SOURCE
- Là nơi tích hợp và thu thập các dữ liệu được lưu trữ trong các nguồn dữ liệu khác nhau, không đồng nhất về nguồn gốc và loại.

### DATA WAREHOUSING
Còn được gọi là Nhà kho dữ liệu, sử dụng các công cụ trích xuất và chuyển đổi điển hình như ETL (Extract - Transform - Load) để lưu trữ các nguồn dữ liệu khác nhau vào một CSDL chung nhằm hỗ trợ phân tích kinh doanh.

### ETL (Extract - Transform - Load)
- Quy trình truy xuất dữ liệu từ một hoặc nhiều nguồn khác nhau (từ Data Source), chuyển đổi và làm sạch khối dữ liệu đó trước khi tải lên Nhà kho dữ liệu để lưu trữ và sẵn sàng được sử dụng để phân tích.

### DATA MINING
- Khai thác dữ liệu bao gồm việc tìm tòi và phân tích các khối dữ liệu lớn để chắt lọc ra được những mẫu hình và xu hướng có ý nghĩa. Nó được sử dụng trong nhiều mục đích khác nhau như tiếp thị theo cơ sở dữ liệu, quản trị rủi ro tín dụng, phòng chống gian lận, lọc mail rác, hoặc đơn giản là để tìm hiểu tâm lí và ý kiến của người dùng.

### DATA VISUALIZATION
- Được dịch là trực quan hóa dữ liệu, là cách biểu diễn dữ liệu dưới các hình ảnh, biểu đồ, bản đồ trực quan. Từ đó, truyền tải thông tin đến người xem một cách sinh động hơn, dễ hiểu hơn.

## ETL và DataWarehouse

### Giới thiệu về quy trình ETL

- ETL là từ viết tắt ngắn gọn cho Extract - Transform - Load với nghĩa tạm hiểu đó là việc trích xuất - chuyển đổi - tải. Đây là quá trình tích hợp dữ liệu, nhằm chuyển đổi dữ liệu chưa qua xử lý từ một nguồn trong hệ thống đến một hệ thống dữ liệu khác (data warehouse hoặc data lake) nằm trong một server xác định. Và sau đó chuyển đổi các dữ liệu này thành thông tin để sử dụng tùy theo mục đích của tổ chức.

### Giới thiệu về Data Warehouse
- Kho dữ liệu (Data Warehouse) là nơi lưu trữ và quản lý dữ liệu từ nhiều nguồn khác nhau để cung cấp thông tin chi tiết có ý nghĩa về doanh nghiệp. Kho dữ liệu thường được sử dụng để kết nối và phân tích dữ liệu kinh doanh từ các nguồn không đồng nhất. Kho dữ liệu là cốt lõi của hệ thống BI, được xây dựng để phân tích và báo cáo dữ liệu.
- Kho dữ liệu tập trung và tổng hợp một lượng lớn dữ liệu từ nhiều nguồn và là sự kết hợp của các công nghệ và thành phần hỗ trợ việc sử dụng dữ liệu một cách chiến lược

### Quy trình ETL trong Data Warehouse
- Trong thế giới Data, Chúng ta biết rằng Data Warehouse là cơ sở của Business Intelligence và ETL là cơ sở của Data Warehouse. Và ETL là một quá trình trong đó công cụ ETL trích xuất dữ liệu từ các hệ thống nguồn dữ liệu khác nhau, chuyển đổi dữ liệu đó trong khu vực tổ chức, và cuối cùng, tải nó vào hệ thống Data Warehouse.

#### Extraction (Trích xuất)

- Dữ liệu nguồn từ các hệ thống nguồn khác nhau được trích xuất có thể ở nhiều định dạng khác nhau như nhiều loại cơ sở dữ liệu, từ file excel hay từ file thô. Điều quan trọng là phải trích xuất dữ liệu từ các hệ thống nguồn khác nhau và lưu trữ nó vào khu vực dàn dựng trước tiên chứ không phải trực tiếp vào kho dữ liệu vì dữ liệu được trích xuất có nhiều định dạng khác nhau và cũng có thể bị hỏng.

#### Transformation (Chuyển đổi)

- Tại đây dữ liệu thô trải qua quá trình xử lý dữ liệu. Dữ liệu được chuyển đổi và hợp nhất cho những trường hợp phân tích sau này. Ở bước này nó sẽ phải sử dụng các phép chuyển đổi như:
  + Chọn các cột dữ liệu phù hợp và cần thiết.
  + Chuyển đổi dữ liệu. Ví dụ: Chuyển giá trị 1 thành Nam hay ngược lại.
  + Tạo ra các cột tính toán mới. Ví dụ: Cột điểm trung bình
  + Lọc dữ liệu và sắp xếp dữ liệu.
  + Thực hiện các phép tổng hợp. Ví dụ: Tính tổng các cột, đếm số dòng
  + Tạo ra các giá trị mới. Ví dụ: Tạo khóa tự tăng
  + Tìm kiếm hay so sánh dữ liệu

#### Loading (Tải dữ liệu)

- Đây là quá trình đẩy dữ liệu sau khi được chuyển đổi cuối cùng vào kho dữ liệu. Việc tải dữ liệu vào một nơi lưu trữ tập trung cho phép các nhà phát triển có thể xây dựng ứng dụng và người dùng cuối có thể ra quyết định dựa trên dữ liệu và ứng dụng đó.





## Cách thu thập và lưu trữ dữ liệu

### Data Lake






### Data Warehouse






### Data Mart










































## Thực hiện
```
Phạm Đức Thể

Thể ~/~
```
