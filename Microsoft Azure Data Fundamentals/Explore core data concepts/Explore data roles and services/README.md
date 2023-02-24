# Mục Lục

* [**Explore data roles and services**](#M01)
    - [Explore job roles in the world of data](#M01.1)
      + [Database Administrator](#M01.1.1)
      + [Data Engineer](#M01.1.2)
      + [Data Analyst](#M01.1.3)
    - [Identify data services](#M01.2)
      + [Azure SQL](#M01.2.1)
      + [Azure Database for open-source relational databases](#M01.2.2)
      + [Azure Cosmos DB](#M01.2.3)
      + [Azure Storage](#M01.2.4)
      + [Azure Data Factory](#M01.2.5)
      + [Azure Synapse Analytics](#M01.2.6)
      + [Azure Databricks](#M01.2.7)
      + [Azure HDInsight](#M01.2.8)
      + [Azure Stream Analytics](#M01.2.9)
      + [Azure Data Explorer](#M01.2.10)
      + [Microsoft Purview](#M01.2.11)
      + [Microsoft Power BI](#M01.2.12)
    - [Knowledge check](#M01.3)










<a name="M01"></a>
# [Explore data roles and services](https://learn.microsoft.com/en-us/training/modules/explore-roles-responsibilities-world-of-data/)
<a name="M01.1"></a>
## Explore job roles in the world of data

Có rất nhiều vai trò liên quan đến quản lý, điều khiển và sử dụng dữ liệu. Một số vai trò tập trung vào kinh doanh, một số vai trò có liên quan đến kỹ thuật, một số tập trung vào nghiên cứu, và một số là các vai trò kết hợp giữa các khía cạnh khác nhau của quản lý dữ liệu. Tuy nhiên, tổ chức của bạn có thể định nghĩa các vai trò khác nhau hoặc đặt tên khác cho chúng, nhưng các vai trò được mô tả trong đơn vị này tóm tắt các phân chia công việc và trách nhiệm phổ biến nhất.

Ba vai trò chính liên quan đến dữ liệu trong hầu hết các tổ chức bao gồm:

- **Quản trị cơ sở dữ liệu (Database administrators)** quản lý cơ sở dữ liệu, gán quyền truy cập cho người dùng, lưu trữ các bản sao dự phòng của dữ liệu và khôi phục dữ liệu trong trường hợp xảy ra sự cố.
- **Kỹ sư dữ liệu (Data engineers)** quản lý cơ sở hạ tầng và quy trình tích hợp dữ liệu trên toàn tổ chức, áp dụng các quy trình làm sạch dữ liệu, xác định các quy tắc quản lý dữ liệu và triển khai các đường ống (pipelines) để chuyển và biến đổi dữ liệu giữa các hệ thống.
- **Nhà phân tích dữ liệu (Data analysts)** khám phá và phân tích dữ liệu để tạo ra các biểu đồ và biểu đồ trực quan giúp tổ chức đưa ra các quyết định có căn cứ.

``` 
!Note
Các vai trò công việc xác định các nhiệm vụ và trách nhiệm khác nhau. Ở một số tổ chức, cùng một người có thể 
thực hiện nhiều vai trò khác nhau; vì vậy, trong vai trò của họ như một quản trị cơ sở dữ liệu, họ có thể 
cung cấp một cơ sở dữ liệu giao dịch và sau đó trong vai trò của một kỹ sư dữ liệu, họ có thể tạo 
một đường ống để chuyển dữ liệu từ cơ sở dữ liệu đó đến một kho dữ liệu (data warehouse) để phân tích.
```


<a name="M01.1.1"></a>
### Database Administrator

![image](https://user-images.githubusercontent.com/62134515/221132737-17a896fb-8f09-4f63-800d-7e17e321787d.png)

Một người quản trị cơ sở dữ liệu có trách nhiệm thiết kế, triển khai, bảo trì và các khía cạnh hoạt động của các hệ thống cơ sở dữ liệu tại chỗ (on-premises) và trên đám mây (cloud-based). Họ chịu trách nhiệm cho sự khả dụng tổng thể và hiệu suất ổn định và tối ưu hóa của cơ sở dữ liệu. Họ làm việc với các bên liên quan để triển khai các chính sách, công cụ và quy trình cho các kế hoạch sao lưu và khôi phục để phục hồi sau một sự cố tự nhiên hoặc lỗi do con người.

Quản trị cơ sở dữ liệu cũng chịu trách nhiệm quản lý bảo mật dữ liệu trong cơ sở dữ liệu, cấp đặc quyền truy cập vào dữ liệu, cho phép hoặc từ chối truy cập cho người dùng phù hợp.





<a name="M01.1.2"></a>
### Data Engineer

![image](https://user-images.githubusercontent.com/62134515/221133279-18cf490c-ca0a-4832-b31e-9b3ae6bf64f4.png)

Một kỹ sư dữ liệu hợp tác với các bên liên quan để thiết kế và triển khai các khối lượng công việc liên quan đến dữ liệu, bao gồm đường ống nhập dữ liệu, các hoạt động làm sạch và chuyển đổi dữ liệu và các kho dữ liệu cho các khối lượng công việc phân tích. Họ sử dụng một loạt các công nghệ nền tảng dữ liệu, bao gồm các cơ sở dữ liệu quan hệ và phi quan hệ, các kho lưu trữ tệp và các luồng dữ liệu.

Họ cũng chịu trách nhiệm đảm bảo rằng sự riêng tư của dữ liệu được duy trì trong đám mây và trải dài từ kho dữ liệu tại chỗ đến các kho dữ liệu đám mây. Họ quản lý và giám sát các đường ống dữ liệu để đảm bảo rằng load dữ liệu hoạt động như mong đợi.






<a name="M01.1.3"></a>
### Data Analyst

![image](https://user-images.githubusercontent.com/62134515/221133350-ebddeecc-88ee-4e13-80af-05b95ff03c88.png)

Một nhà phân tích dữ liệu giúp các doanh nghiệp tối đa hóa giá trị của tài sản dữ liệu của họ. Họ chịu trách nhiệm khám phá dữ liệu để xác định xu hướng và mối quan hệ, thiết kế và xây dựng các mô hình phân tích, và kích hoạt khả năng phân tích tiên tiến thông qua các báo cáo và trực quan hóa.

Một nhà phân tích dữ liệu xử lý dữ liệu thô thành các thông tin cần thiết dựa trên các yêu cầu kinh doanh đã xác định để cung cấp thông tin cần thiết.

```
!Note
Các vai trò được mô tả ở đây đại diện cho các vai trò chính liên quan đến dữ liệu được tìm thấy trong hầu hết 
các tổ chức vừa đến lớn. Có các vai trò liên quan đến dữ liệu khác không được đề cập ở đây, chẳng hạn như 
nhà khoa học dữ liệu và kiến trúc sư dữ liệu; và còn có các chuyên gia kỹ thuật khác làm việc với dữ liệu, 
bao gồm các nhà phát triển ứng dụng và kỹ sư phần mềm.
```








<a name="M01.2"></a>
## Identify data services

Microsoft Azure là một nền tảng đám mây cung cấp năng lượng cho các ứng dụng và cơ sở hạ tầng IT cho một số tổ chức lớn nhất thế giới. Nó bao gồm nhiều dịch vụ để hỗ trợ các giải pháp đám mây, bao gồm các công việc liên quan đến dữ liệu giao dịch và phân tích.

Dưới đây là một số dịch vụ đám mây thường được sử dụng nhất cho dữ liệu trên Microsoft Azure.

```
!Note
Topic này chỉ đề cập đến một số dịch vụ dữ liệu được sử dụng phổ biến nhất cho các giải pháp giao dịch 
và phân tích hiện đại. Ngoài ra còn có các dịch vụ khác cũng có sẵn trên nền tảng Microsoft Azure.
```





<a name="M01.2.1"></a>
### Azure SQL

![image](https://user-images.githubusercontent.com/62134515/221138532-0394e85c-a3ca-4e78-8e62-17c3477d43dc.png)

Azure SQL là tên chung cho một họ các giải pháp cơ sở dữ liệu quan hệ dựa trên cơ sở dữ liệu Microsoft SQL Server. Các dịch vụ Azure SQL cụ thể bao gồm:

 - **Azure SQL Database** - cơ sở dữ liệu được quản lý hoàn toàn dưới dạng nền tảng dịch vụ (platform-as-a-service - PaaS) được lưu trữ trên Azure.
 - **Azure SQL Managed Instance** - một phiên bản được lưu trữ của SQL Server với bảo trì tự động, cho phép cấu hình linh hoạt hơn Azure SQL DB nhưng có trách nhiệm quản trị nhiều hơn cho chủ sở hữu.
 - **Azure SQL VM** - một máy ảo với cài đặt SQL Server, cho phép tối đa hóa khả năng cấu hình với trách nhiệm quản lý đầy đủ.

Nhà quản trị cơ sở dữ liệu thông thường cung cấp và quản lý hệ thống cơ sở dữ liệu Azure SQL để hỗ trợ các ứng dụng line of business (LOB) cần lưu trữ dữ liệu giao dịch.

Các kỹ sư dữ liệu có thể sử dụng các hệ thống cơ sở dữ liệu Azure SQL làm nguồn dữ liệu cho các đường ống dữ liệu thực hiện các hoạt động extract, transform, và load (ETL) để nhập dữ liệu giao dịch vào hệ thống phân tích.

Các nhà phân tích dữ liệu có thể truy vấn trực tiếp cơ sở dữ liệu Azure SQL để tạo báo cáo, tuy nhiên trong các tổ chức lớn, dữ liệu thường được kết hợp với dữ liệu từ các nguồn khác trong kho dữ liệu phân tích để hỗ trợ phân tích doanh nghiệp.




<a name="M01.2.2"></a>
### Azure Database for open-source relational databases

![image](https://user-images.githubusercontent.com/62134515/221138595-81c28331-9d71-4007-a616-241560681fc0.png)









<a name="M01.2.3"></a>
### Azure Cosmos DB

![image](https://user-images.githubusercontent.com/62134515/221138641-18351cac-d3c1-4fcd-a119-bf7b05c27d37.png)









<a name="M01.2.4"></a>
### Azure Storage

![image](https://user-images.githubusercontent.com/62134515/221138740-bae04b8d-d2e6-44de-9432-781b8056f818.png)








<a name="M01.2.5"></a>
### Azure Data Factory

![image](https://user-images.githubusercontent.com/62134515/221138788-c2f37016-7295-46fa-a985-1e5ff4891b72.png)







<a name="M01.2.6"></a>
### Azure Synapse Analytics

![image](https://user-images.githubusercontent.com/62134515/221139142-6eb0960f-3ae2-4310-82fd-2312b8345b1a.png)







<a name="M01.2.7"></a>
### Azure Databricks

![image](https://user-images.githubusercontent.com/62134515/221139200-21025737-ab63-4ee8-8899-baa2d212e540.png)










<a name="M01.2.8"></a>
### Azure HDInsight

![image](https://user-images.githubusercontent.com/62134515/221139247-b95d7cf8-7eda-4d1a-8ada-7a32e5b583e8.png)










<a name="M01.2.9"></a>
### Azure Stream Analytics

![image](https://user-images.githubusercontent.com/62134515/221139302-30dce632-c1aa-40f0-a617-446bd6e9f5d0.png)








<a name="M01.2.10"></a>
### Azure Data Explorer

![image](https://user-images.githubusercontent.com/62134515/221139379-62a6f6b9-072d-4d38-bf0f-21d41631bf23.png)









<a name="M01.2.11"></a>
### Microsoft Purview

![image](https://user-images.githubusercontent.com/62134515/221139560-df406d12-f109-4318-b741-1047e4ccdfd4.png)








<a name="M01.2.12"></a>
### Microsoft Power BI

![image](https://user-images.githubusercontent.com/62134515/221139617-fda8e42a-f908-48af-8952-cfc9c8fe7ac1.png)














<a name="M01.3"></a>
## Knowledge check
![image](https://user-images.githubusercontent.com/62134515/220530981-9be56694-f628-4332-a4b9-e54bf6bd2f4b.png)










