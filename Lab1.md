# Tài liệu mô tả kết quả phân tích hệ thống Payroll System

## Giới thiệu: 

Hệ thống Payroll System được thiết kế để quản lý các quy trình thanh toán và ghi nhận thời gian làm việc của nhân viên. Hệ thống này bao gồm hai ca sử dụng chính: **Payment** và **Maintain Timecard**. Tài liệu này sẽ hợp nhất các phân tích liên quan đến hai ca sử dụng này, xác định các lớp phân tích, hành vi của chúng và các mối quan hệ giữa chúng.

## I. Phân tích ca sử dụng Payment

## 1. Phân tích kiến trúc

Kiến trúc 3 lớp (Three-tier Architecture)

### a. Lớp trình bày (Presentation Layer): 
Mô tả: Đây là lớp giao diện người dùng, nơi người dùng tương tác với hệ thống thông qua các ứng dụng web hoặc desktop.

Chức năng: Hiển thị thông tin và thu thập dữ liệu từ người dùng.

Công nghệ áp dụng: HTML, CSS, JavaScript, các framework như React, Angular hoặc Vue.js.

### b. Lớp xử lý (Business Logic Layer):
Mô tả: Chứa các quy tắc nghiệp vụ và logic xử lý của hệ thống. Đây là nơi diễn ra các tính toán, như tính toán lương và xác thực thông tin.

Chức năng: Xử lý các yêu cầu từ lớp trình bày, thực hiện các tính toán và truy cập dữ liệu từ lớp dữ liệu.

Công nghệ áp dụng: Java, C#, Python, Node.js hoặc bất kỳ ngôn ngữ lập trình nào khác phù hợp với yêu cầu.

### c. Lớp dữ liệu (Data Access Layer):
Mô tả: Quản lý việc lưu trữ và truy xuất dữ liệu từ cơ sở dữ liệu.

Chức năng: Thực hiện các thao tác CRUD (Create, Read, Update, Delete) trên dữ liệu nhân viên, lịch sử thanh toán và thời gian làm việc.

Công nghệ áp dụng: SQL Server, MySQL, PostgreSQL hoặc các hệ quản trị cơ sở dữ liệu khác.

## 2. Lý do lựa chọn kiến trúc:
**Tách biệt rõ ràng:** Việc chia hệ thống thành ba lớp riêng biệt giúp dễ dàng quản lý, bảo trì và nâng cấp từng phần mà không ảnh hưởng đến các phần khác. Điều này làm cho việc phát triển và sửa lỗi trở nên hiệu quả hơn.

**Tính tái sử dụng:** Các thành phần trong kiến trúc có thể được tái sử dụng cho các dự án khác. Ví dụ, lớp xử lý có thể sử dụng cho các hệ thống khác có logic tương tự.

**Khả năng mở rộng:** Khi nhu cầu thay đổi hoặc mở rộng, dễ dàng thêm tính năng mới vào từng lớp mà không cần thay đổi cấu trúc tổng thể. Ví dụ, có thể thay đổi giao diện người dùng mà không ảnh hưởng đến logic xử lý hay dữ liệu.

## 3. Ý nghĩa từng thành phần trong kiến trúc:
**Lớp trình bày:** Đảm bảo trải nghiệm người dùng tốt, giúp người dùng tương tác một cách dễ dàng và hiệu quả. Giao diện người dùng phải trực quan và dễ sử dụng.

**Lớp xử lý:** Chịu trách nhiệm về tất cả các quy tắc nghiệp vụ, điều này đảm bảo rằng dữ liệu được xử lý đúng cách và mọi tính toán đều chính xác.

**Lớp dữ liệu:** Bảo vệ dữ liệu và quản lý truy cập, đảm bảo rằng thông tin được lưu trữ an toàn và có thể truy cập một cách hiệu quả.

## 4. Biểu đồ packages mô tả kiến trúc :

![alt text](https://www.planttext.com/api/plantuml/png/T9112i8m54JtEKNelbUGQdLHS26MhgIBR_oMO9gK_5G8uibSU2IlODCMf5MtmypZCQ_7Co47rhMrOWs82rJ8eoAB-8rnVYW8RQOTsZC8B4EI6ksiKGejbUpEFfjLIr8ZqTPKKepp7VZGpT5UvRZFGO7rAIZHAd36JY5hSB0KeiECX10SWN08UyAcRfJnY7ji3CaEuNl6p9N7yU9ROAB_fp8BXjRSutVhbnfBK9_2ksy0003__mC0).

## II. Cơ chế phân tích:

### 1. Quản lý nhân viên
**Mô tả:** Cơ chế này cho phép thêm, sửa, xóa và truy xuất thông tin nhân viên, bao gồm tên, mã số, chức vụ, và mức lương.
**Giải thích:** Quản lý thông tin nhân viên là cần thiết để đảm bảo rằng mọi thông tin liên quan đến lương và phúc lợi đều chính xác và được cập nhật. Điều này giúp tạo ra một nền tảng vững chắc cho các chức năng khác của hệ thống.

### 2. Tính toán lương
**Mô tả:** Cơ chế này thực hiện các phép tính để xác định số tiền lương của từng nhân viên dựa trên số giờ làm việc, mức lương cơ bản và các yếu tố khác (phụ cấp, khấu trừ).

**Giải thích:** Tính toán lương chính xác là cốt lõi của hệ thống, ảnh hưởng trực tiếp đến sự hài lòng của nhân viên. Nếu lương được tính sai, nó có thể dẫn đến sự không hài lòng và mất niềm tin của nhân viên đối với tổ chức.

### 3. Quản lý thời gian làm việc
**Mô tả:** Cơ chế này cho phép nhân viên ghi nhận thời gian làm việc hàng ngày, bao gồm giờ vào, giờ ra và các ghi chú khác (như ngày nghỉ, làm thêm giờ).

**Giải thích:** Ghi nhận chính xác thời gian làm việc giúp hệ thống tính toán lương chính xác hơn, đồng thời đảm bảo tính minh bạch và công bằng trong việc trả lương cho nhân viên.

### 4. Báo cáo lương:
**Mô tả:** Hệ thống cần tạo ra các báo cáo lương theo kỳ, giúp quản lý theo dõi và phân tích chi phí lương.

**Giải thích:** Các báo cáo này hỗ trợ trong việc lập kế hoạch ngân sách và đưa ra quyết định về nhân sự trong tổ chức.

## III. Phân tích ca sử dụng Payment

###  1. Các lớp phân tích cho ca sử dụng Payment

**Payment:** Quản lý quy trình thanh toán.

**Employee:** Đại diện cho thông tin nhân viên.

**SalaryCalculator:** Tính toán lương dựa trên thông tin nhân viên và giờ làm việc.

**PaymentReport:** Tạo báo cáo thanh toán.

### 2. Quy trình thanh toán thông qua biểu đồ sequence:

![alt text](https://www.planttext.com/api/plantuml/png/R91D2W8n34RtFKKku0Mwa14LSIVZ2KADKEYVcNJHixdmI5x16MYH3hDgoVU-Hzhl-pDCWYpPEuL68iFP9nSBaKhps1gRC0ZSi7WAqitkw93B4Pt93kVcLc6a55cKQbBOxLkaOQHNfkalh-V2hDqQsfrgfjR8IYsPGqNXu6Fk_Trw6YuKY1TttRUBjyGzjn3jXHfETaeEI-l0DJmZUnGRWneeFEQl_W400F__0m00).

### 3. Nhiệm vụ của từng lớp:

**Payment:** Quản lý quá trình yêu cầu thanh toán và điều phối các lớp khác để thực hiện thanh toán.

**Employee:** Cung cấp thông tin cần thiết về nhân viên để thực hiện thanh toán (như tên, mức lương, số giờ làm việc).

**SalaryCalculator:** Thực hiện các phép toán để tính toán số tiền lương dựa trên thông tin từ lớp Employee và các yếu tố khác (phụ cấp, khấu trừ).

**PaymentReport:** Nhiệm vụ: Tạo ra báo cáo thanh toán chi tiết, giúp người dùng hiểu rõ các thông tin liên quan đến lương.

### 4. Thuộc tính và quan hệ giữa các lớp phân tích:
#### Thuộc tính:

*Payment:*

amount: Số tiền thanh toán.

date: Ngày thanh toán.

*Employee:*

id: Mã nhân viên.

name: Tên nhân viên.

hourlyRate: Mức lương theo giờ.

*SalaryCalculator:*

calculateSalary(): Phương thức tính toán lương.

*PaymentReport:*

reportData: Dữ liệu báo cáo.

#### Quan hệ:

Payment có quan hệ với Employee: 1-n (một nhân viên có thể có nhiều lần thanh toán).

Payment có quan hệ với SalaryCalculator: 1-1 (mỗi yêu cầu thanh toán sử dụng một lần tính toán).

Payment có quan hệ với PaymentReport: 1-1 (mỗi lần thanh toán tạo ra một báo cáo).

### Biểu đồ lớp mô tả lớp phân tích: 

![alt text](https://www.planttext.com/api/plantuml/png/R94vRiCm44LxdcAWIYvKf9t2C62d3wmJ3AInBO2BmCM0OEHaANoaN24qISbR6X8p7Bx_F_dxSzquJzO79KKdoJdueacnzd0H00sGCa5xX8Cqv5Ed9yy8kxZ64k38ccqiohLwXN0sGo--HU5zgb6QYRa0XnvXq1cbIKLKw-sWZwbnCi7AQPyKikA2QKcIdROako396vjm05rfS3wlkQZXehjwGnMhUnwDdNFQLCHKz63edYxFrcE-YJFY8UpyRDL71Kq3bQxkoH5Ev5ucrcb_IuKG7Fy_-smR5szER5Ztjm_y0m00__y30000).

## IV. Phân tích ca sử dụng Maintain Timecard:

### Lớp phân tích cho ca sử dụng Maintain Timecard:

**Timecard:** Quản lý thông tin về thời gian làm việc.

**Employee:** Đại diện cho thông tin nhân viên.

**TimeEntry:** Ghi nhận thời gian làm việc cụ thể (giờ vào, giờ ra).

**TimecardManager:** Quản lý việc thêm, sửa, xóa các bản ghi thời gian.

### Mô tả hành vi thông qua biểu đồ sequence:
![alt text](https://www.planttext.com/api/plantuml/png/R94vRiCm44LxdcAWIYvKf9t2C62d3wmJ3AInBO2BmCM0OEHaANoaN24qISbR6X8p7Bx_F_dxSzquJzO79KKdoJdueacnzd0H00sGCa5xX8Cqv5Ed9yy8kxZ64k38ccqiohLwXN0sGo--HU5zgb6QYRa0XnvXq1cbIKLKw-sWZwbnCi7AQPyKikA2QKcIdROako396vjm05rfS3wlkQZXehjwGnMhUnwDdNFQLCHKz63edYxFrcE-YJFY8UpyRDL71Kq3bQxkoH5Ev5ucrcb_IuKG7Fy_-smR5szER5Ztjm_y0m00__y30000).

### Nhiệm vụ của từng lớp phân tích:
**Timecard:**

Quản lý và lưu trữ thông tin về thời gian làm việc của nhân viên, bao gồm các thời gian vào và ra.

**Employee:**

Cung cấp thông tin về nhân viên để xác định ai đang ghi nhận thời gian làm việc.

**TimeEntry:**

Đại diện cho một bản ghi thời gian cụ thể, bao gồm giờ vào, giờ ra và ngày làm việc.

**TimecardManager:**

Quản lý các thao tác liên quan đến timecard, bao gồm thêm, sửa, và xóa các bản ghi thời gian.

### Thuộc tính và quan hệ:
**Thuộc tính:**

*Timecard:*

totalHours: Tổng số giờ làm việc.

*Employee:*

id: Mã nhân viên.

name: Tên nhân viên.

*TimeEntry:*

entryId: Mã bản ghi thời gian.

checkIn: Giờ vào.

checkOut: Giờ ra.

*TimecardManager:*

updateTimecard(): Phương thức để thêm hoặc cập nhật Timecard.

**Quan hệ:**

Timecard có quan hệ với Employee: 1-1 (mỗi timecard thuộc về một nhân viên).

Timecard có quan hệ với TimeEntry: 1-n (một timecard có thể chứa nhiều bản ghi thời gian).

TimecardManager có quan hệ với Timecard: 1-1 (mỗi yêu cầu quản lý timecard sẽ tương tác với một timecard cụ thể).

## Biểu đồ lớp mô tả lớp phân tích: 

![alt text](https://www.planttext.com/api/plantuml/png/R94vRiCm44LxdcAWIYvKf9t2C62d3wmJ3AInBO2BmCM0OEHaANoaN24qISbR6X8p7Bx_F_dxSzquJzO79KKdoJdueacnzd0H00sGCa5xX8Cqv5Ed9yy8kxZ64k38ccqiohLwXN0sGo--HU5zgb6QYRa0XnvXq1cbIKLKw-sWZwbnCi7AQPyKikA2QKcIdROako396vjm05rfS3wlkQZXehjwGnMhUnwDdNFQLCHKz63edYxFrcE-YJFY8UpyRDL71Kq3bQxkoH5Ev5ucrcb_IuKG7Fy_-smR5szER5Ztjm_y0m00__y30000).
