# Lab 3

## Subsystem context diagrams

### Biểu đồ ngữ cảnh của các hệ thống con

#### BankSystem
- Biểu đồ ngữ cảnh của hệ thống con BankSystem:
![alt text](https://www.planttext.com/api/plantuml/png/f591JiCm4BplArOz5ObMS8sgg89JRqYym3WROTLPLzuD8a9z6GUUn1U86mmcLKzSxBLdPdSyykVxnrRKHEqx3s2z4S47CyJW_NrWJJj5t6piTAXhV0D4Z3r_ivPNS0Hmh1HROmbtTuRtZuCeTQFivpuB6pe4SReqezm-azrNcAjh7DaXoIjCwuxR43kZBd2QmK49FRLQOUCYMSsz14zomHTdyXF-c93-IQRw4CFhy7yhlpcTsEC8OdKwTJwM7WhX19rdkxXPhsyNk5hLPNPGvbXGBZ0IbEsS0JCZS467Ss2kWorna_x95m000F__0m00)

- Giải thích biểu đồ:

   - PayrollController (control): Là lớp điều khiển xử lý các thao tác liên quan đến việc tính toán và thực hiện trả lương. Lớp này có phương thức runPayroll().
   - IBankSystem (interface): Giao diện mà các hệ thống ngân hàng cần triển khai để thực hiện các thao tác liên quan đến việc gửi tiền (direct deposit). Phương thức deposit() trong giao diện này sẽ thực hiện việc chuyển tiền vào tài khoản ngân hàng.
   - BankSystem (subsystem proxy): Là hệ thống ngân hàng, thực hiện các thao tác gửi tiền trực tiếp vào tài khoản ngân hàng. Nó có phương thức deposit() để gửi tiền từ Paycheck vào tài khoản được mô tả bởi BankInformation.
   - Paycheck (entity): Là đối tượng đại diện cho phiếu lương hoặc số tiền được trả cho nhân viên.
   - BankInformation: Lưu trữ thông tin ngân hàng cần thiết để thực hiện các giao dịch, chẳng hạn như thông tin tài khoản.

- Mô tả:
  
Interface (IBankSystem):

          interface IBankSystem {
          // Thực hiện chuyển tiền lương vào tài khoản ngân hàng
          void deposit(Paycheck aPaycheck, BankInformation intoBank);
          }

  Hệ thống con (BankSystem):

    - Chức năng chính:

     Xử lý giao dịch chuyển lương
  
    - Thành phần:
      
    Transaction Processing: Xử lý giao dịch chuyển tiền
  
    Account Verification: Xác thực thông tin tài khoản
  
    Transaction Logging: Ghi log giao dịch
  
    - Đặc điểm:
      
    Đảm bảo tính bảo mật trong giao dịch
  
    Xác thực thông tin tài khoản trước khi chuyển
  
    Ghi nhận log đầy đủ cho mỗi giao dịch
  
    Hỗ trợ nhiều loại tài khoản ngân hàng khác nhau

Các thành phần chính trong biểu đồ:

  - PayrollController: Điều khiển quá trình tính và chuyển lương
  - IBankSystem: Interface định nghĩa phương thức giao tiếp với ngân hàng
  - BankSystem: Triển khai thực tế việc tương tác với hệ thống ngân hàng
  - Paycheck: Thông tin chi tiết về séc lương
  - BankInformation: Thông tin tài khoản ngân hàng
  
Thuộc tính:
  - PayrollController (control):
    
    - payrollData: Lưu trữ dữ liệu trả lương cần thiết cho việc tính toán và thực hiện trả lương. Thuộc tính này có thể chứa thông tin về các phiếu lương hoặc dữ liệu trả lương cho từng nhân viên.
      
  - IBankSystem (interface):
    
    - IBankSystem là một giao diện, do đó nó chỉ có phương thức mà không có thuộc tính. Giao diện này quy định các hành động mà hệ thống ngân hàng cần thực hiện.
      
  - BankSystem (subsystem proxy):
    
    - bankAPIKey: Chứa một khóa API để tương tác với các dịch vụ ngân hàng bên ngoài (nếu có), có thể được sử dụng để xác thực khi gửi yêu cầu đến ngân hàng.
      
  - Paycheck (entity):
    
    - amount: Số tiền của phiếu lương.
    - employeeId: ID của nhân viên mà phiếu lương này được phát cho.
    - payDate: Ngày trả lương cho nhân viên.
      
  - BankInformation:
    
    - accountNumber: Số tài khoản ngân hàng của nhân viên nhận lương.
    - routingNumber: Số mã định tuyến ngân hàng (dùng để xác định ngân hàng).
    - bankName: Tên ngân hàng nơi nhân viên có tài khoản.
      
- Mối quan hệ của các thuộc tính:
  
  - PayrollController có thể tương tác với IBankSystem (dạng quan hệ tùy chọn "0..1" có nghĩa là một đối tượng PayrollController có thể hoặc không có liên kết với một đối tượng IBankSystem).
  - IBankSystem là giao diện mà BankSystem triển khai, và thông qua đó, BankSystem thực hiện việc gửi tiền vào tài khoản của người lao động (liên kết với Paycheck và BankInformation).
  - Các mối quan hệ giữa các lớp cho thấy cách BankSystem và IBankSystem phối hợp để xử lý các giao dịch gửi tiền từ Paycheck vào tài khoản BankInformation.

 #### PrintService
- Biểu đồ ngữ cảnh của hệ thống con PrintService:
![alt text](https://www.planttext.com/api/plantuml/png/l5D1JiCm4Bpd5HQdzj0Ahb4KLQ92AYfIeIzmxMqQaSIHlQa8Y9Tnu4byWTquZX9L877XudXtrZlZyURhutFbK5fioY9IXNHEx6HhJL7ScWhv2rOaYV91cegtI0XHsxn2gbCdKC-pUVGUHPG0UvGAn6R7w1xiEQSeIGPaSdgcZMfAg30MwtutPp03xCw3tQF4nitciV2xAVhOG0CCTXjMqAkVahlcu5g7K1AhUMd_HK9eHlIqvXXO5u5lesD17JZ5ndOAzaXDCquTZItbIDDT5tV55YI2NjD2CAsSTFahHOMXmuC2hzQJvku9f6vZSJ2c05bn3gmrzW6SancCgMjPWzt26Of189fgaXeukajxYXegJHtkpS75OfixJ8Bsb1sJMXFqaziMIdE6SK5lJtYBZcWBLOOdDjlh4ehk4bw0HLrExTNrSdbp9HQBT3gIqNH0HsM_L34SP4T_GFgvkSZxaV4UJZgio4l-5xy1003__mC0)


Giải thích biểu đồ:

  - PrintService (control): Là lớp điều khiển xử lý các thao tác liên quan đến việc gửi yêu cầu in tài liệu. Lớp này có các phương thức để thực hiện các thao tác như in tài liệu, kiểm tra trạng thái máy in và quản lý hàng đợi công việc in.
    - Phương thức chính: printPaycheck(), getPrinterStatus(), getPrinterQueue()
  - IPrintService (interface): Giao diện mà các hệ thống in cần triển khai để thực hiện các thao tác liên quan đến việc in tài liệu. Các phương thức trong giao diện này sẽ cho phép gửi tài liệu đến máy in, kiểm tra trạng thái máy in và xem hàng đợi in hiện tại.
    
    - Phương thức:
      
      - print(document: Document): In một tài liệu.
      - getPrinterStatus(): Kiểm tra trạng thái của máy in (sẵn sàng hay có lỗi).
      - getPrinterQueue(): Kiểm tra và trả về hàng đợi in.
        
  - PrintService (subsystem proxy): Là hệ thống con thực hiện các thao tác in tài liệu thực tế. Nó triển khai giao diện IPrintService và thực hiện việc in tài liệu qua các máy in thực tế, đồng thời theo dõi trạng thái máy in và hàng đợi in.
    
    - Phương thức:
      
      - print(document: Document): Thực hiện việc in tài liệu qua máy in.
      - getPrinterStatus(): Kiểm tra và trả về trạng thái của máy in.
      - getPrinterQueue(): Kiểm tra và trả về hàng đợi in.
        
  - Document (entity): Là đối tượng đại diện cho tài liệu cần in. Mỗi tài liệu có thể chứa thông tin về nội dung, định dạng và kích thước.
    
    - Thuộc tính:
      
      - documentId: Mã định danh của tài liệu.
      - content: Nội dung của tài liệu cần in.
      - format: Định dạng của tài liệu (ví dụ: PDF, DOCX).
      - createdDate: Ngày tạo tài liệu.
      - size: Kích thước của tài liệu.
        
  - Status: Lưu trữ trạng thái của máy in, có thể bao gồm các thông tin về tình trạng sẵn sàng của máy in, mức giấy, mức mực, và các lỗi có thể xảy ra.
    
    - Thuộc tính:
      
      - isReady: Trạng thái của máy in, xác định xem máy có sẵn sàng để in không.
      - errorMessage: Thông điệp lỗi nếu máy in gặp vấn đề.
      - paperLevel: Mức độ giấy còn lại trong máy in.
      - tonerLevel: Mức độ mực còn lại trong máy in.
        
  - Queue: Quản lý hàng đợi các công việc in. Các tài liệu được thêm vào hàng đợi và sẽ được in theo thứ tự trong hàng đợi.
    
    - Thuộc tính:
      
      - pendingJobs: Danh sách các tài liệu đang chờ được in.
        
    - Phương thức:
      
      - addJob(document: Document): Thêm tài liệu vào hàng đợi.
      - removeJob(documentId: int): Loại bỏ tài liệu khỏi hàng đợi.
      - getQueueLength(): Trả về số lượng tài liệu còn lại trong hàng đợi.
      - clearQueue(): Xóa tất cả các công việc trong hàng đợi.

Mô tả:

Interface (IPrintService):

      interface IPrintService {
          // Thực hiện in tài liệu
          void print(Document document);
      
          // Kiểm tra trạng thái của máy in
          Status getPrinterStatus();
      
          // Lấy hàng đợi các công việc in
          Queue getPrinterQueue();
      }

Hệ thống con (PrintService):

- Chức năng chính:

  - In tài liệu: Nhận yêu cầu từ lớp điều khiển và thực hiện việc in tài liệu.
  - Theo dõi trạng thái máy in: Kiểm tra tình trạng sẵn sàng của máy in và thông báo lỗi nếu có.
  - Quản lý hàng đợi in: Theo dõi các công việc in và đảm bảo chúng được thực hiện theo đúng thứ tự.
    
- Thành phần:

  - In tài liệu: Các phương thức xử lý việc in tài liệu vào máy in.
  - Quản lý trạng thái máy in: Cung cấp thông tin về tình trạng máy in.
  - Quản lý hàng đợi in: Kiểm soát các tài liệu đang chờ được in.
    
- Đặc điểm:

  - Bảo mật: Đảm bảo không có tài liệu nào bị in trái phép.
  - Hiệu suất: Quản lý hàng đợi để tối ưu hóa hiệu suất in.
    
- Các thành phần chính trong biểu đồ:
  
  - PrintService: Là lớp điều khiển chính trong hệ thống, điều khiển quá trình in tài liệu và quản lý các công việc in.
  - IPrintService: Giao diện định nghĩa các phương thức để in tài liệu và theo dõi trạng thái máy in.
  - Document: Tài liệu cần in, có chứa thông tin về nội dung và kích thước.
  - Status: Trạng thái của máy in, bao gồm mức giấy, mức mực và trạng thái sẵn sàng.
  - Queue: Hàng đợi các tài liệu chờ được in.
 
- Thuộc tính:
  
  - PrintService (control):
    
    - printerData: Lưu trữ dữ liệu cần thiết cho quá trình in ấn.
    - queue: Lưu trữ các công việc in đang chờ xử lý.
      
  - IPrintService (interface):
    
    - Giao diện này chỉ định các phương thức mà hệ thống in cần phải thực hiện, do đó không có thuộc tính nào.
      
  - PrintService (subsystem proxy):
    
    - printerID: Mã nhận diện máy in.
    - printerStatus: Trạng thái của máy in.
    - printerType: Loại máy in (ví dụ: laser, phun mực).
      
  - Document (entity):
    
    - documentId: Mã định danh tài liệu.
    - content: Nội dung tài liệu.
    - size: Kích thước tài liệu (đơn vị byte).
    - format: Định dạng của tài liệu (ví dụ: PDF, DOCX).
    - createdDate: Ngày tạo tài liệu.
      
  - Status:
    
    - isReady: Trạng thái của máy in, xem máy có sẵn sàng hay không.
    - errorMessage: Thông điệp lỗi nếu máy in gặp sự cố.
    - paperLevel: Mức độ giấy trong máy in.
    - tonerLevel: Mức độ mực trong máy in.
      
  - Queue:
    
    - pendingJobs: Danh sách các tài liệu đang chờ in.
    - addJob(document: Document): Thêm tài liệu vào hàng đợi.
    - removeJob(documentId: int): Loại bỏ tài liệu khỏi hàng đợi.
    - getQueueLength(): Trả về số lượng tài liệu trong hàng đợi.
    - clearQueue(): Xóa tất cả các công việc trong hàng đợi.
      
  - Mối quan hệ của các thuộc tính:
    
    - PrintService tương tác với IPrintService để thực hiện việc in tài liệu.
    - PrintService sử dụng Status và Queue để kiểm tra trạng thái máy in và quản lý hàng đợi các tài liệu cần in.
    - Document được in và có thể được thêm vào hoặc loại bỏ khỏi Queue.
    - Status và Queue giúp quản lý và theo dõi quá trình in ấn, bao gồm cả kiểm tra trạng thái của máy in và danh sách các công việc in đang chờ.
   

 #### ProjectManagementDatabase subsystems
Biểu đồ ngữ cảnh của hệ thống con ProjectManagementDatabase subsystems

![alt text](https://www.planttext.com/api/plantuml/png/n9D1JiCm44NtFiMeArYaWcqKHHMmYGG8YHCuzZIaIkpA7YCYnCbOS2IkmAHfYaj45cN19jQC_loyZ7y-tpzMdgIZq3P2DT9xU71sWuhkf94LjcZesXfojcdGGPQfeSXpU1K0e1nAmlt8sNOuqz7Zl9TKIFlogYlqg2bq2hKP566hPqtUX60fkhLK2CM4xqQIBAL7fZl8HZuld-VfraZgwUzylwmkGlEXz9qdR84DNhf_1MGSXgjff4YEFQFElMmnXKTojQdwzYuh_5NSx9zz2uq-Rh26We-dog0v1Ibe6yfcft7eRN0AMNPRUye6RVvDEcwEmsUOexPc85M7UXZv0HU_cBtcihouM2ul5v0a-Kocn4pS8eEJvgF1AUW9gkdAn8elf_-plm000F__0m00)

Giải thích biểu đồ:

- ProjectManagementController (control):
  - Lớp điều khiển này có nhiệm vụ xử lý các thao tác liên quan đến quản lý dự án, bao gồm việc lưu trữ và truy xuất thông tin về dự án từ cơ sở dữ liệu.
    
  - Phương thức:
    
    - createProject(project: Project): Tạo một dự án mới và lưu vào cơ sở dữ liệu.
    - getProjectById(projectId: int): Truy xuất thông tin của một dự án từ cơ sở dữ liệu theo ID.
    - updateProject(project: Project): Cập nhật thông tin của dự án trong cơ sở dữ liệu.
  
- ProjectManagementDatabase (interface):
 - Giao diện định nghĩa các phương thức cơ bản mà hệ thống cơ sở dữ liệu phải triển khai để quản lý thông tin dự án.
   
 - Phương thức:
   
   - saveProject(project: Project): Lưu thông tin của dự án vào cơ sở dữ liệu.
   - fetchProjectById(projectId: int): Truy xuất thông tin dự án từ cơ sở dữ liệu.
   - updateProject(project: Project): Cập nhật thông tin của dự án trong cơ sở dữ liệu.

- ProjectManagementDatabase (subsystem proxy):
  - Là hệ thống con thực tế thực hiện các thao tác truy vấn và thao tác với cơ sở dữ liệu để lưu trữ và truy xuất thông tin dự án.
 
  - Phương thức:

    - saveProject(project: Project): Lưu dự án vào cơ sở dữ liệu.
    - fetchProjectById(projectId: int): Truy xuất thông tin dự án từ cơ sở dữ liệu.
    - updateProject(project: Project): Cập nhật thông tin của dự án vào cơ sở dữ liệu.

Mô tả:

Interface (IProjectManagementDatabase):

        interface IProjectManagementDatabase {
            // Lưu dự án vào cơ sở dữ liệu
            void saveProject(Project project);
        
            // Truy xuất dự án theo ID
            Project fetchProjectById(int projectId);
        
            // Cập nhật thông tin của dự án
            void updateProject(Project project);
        }

Hệ thống con (ProjectManagementDatabase):

- Chức năng chính:

  - Lưu trữ thông tin dự án: Các thông tin dự án được lưu vào cơ sở dữ liệu khi được tạo mới hoặc cập nhật.
  - Truy vấn dữ liệu dự án: Cung cấp các phương thức để truy xuất thông tin về dự án từ cơ sở dữ liệu.
  - Cập nhật thông tin dự án: Thực hiện các thao tác cập nhật thông tin dự án khi có thay đổi.

- Thành phần:

  - Quản lý thông tin dự án: Chứa thông tin chi tiết về dự án như ID, tên, ngân sách, ngày bắt đầu và kết thúc.
  - Kết nối cơ sở dữ liệu: Quản lý kết nối tới cơ sở dữ liệu để thực hiện các thao tác như lưu, truy vấn, và cập nhật dữ liệu.

- Đặc điểm:

  - Đảm bảo tính toàn vẹn dữ liệu: Kiểm tra tính hợp lệ của thông tin dự án trước khi lưu vào cơ sở dữ liệu.
  - Quản lý kết nối cơ sở dữ liệu: Quản lý các kết nối đến cơ sở dữ liệu để đảm bảo hiệu quả trong việc truy vấn và lưu trữ dữ liệu.

- Các thành phần chính trong biểu đồ:

  - ProjectManagementController: Là lớp điều khiển, quản lý các thao tác liên quan đến dự án và thông qua IProjectManagementDatabase để tương tác với cơ sở dữ liệu.
  - IProjectManagementDatabase: Giao diện định nghĩa các phương thức truy vấn và lưu trữ dữ liệu cho hệ thống cơ sở dữ liệu của dự án.
  - ProjectManagementDatabase: Triển khai giao diện IProjectManagementDatabase, thực hiện các thao tác lưu trữ, truy vấn, và cập nhật thông tin dự án.
  - Project: Đối tượng chứa các thông tin về dự án cần được lưu trữ trong cơ sở dữ liệu.
  - DatabaseConnection: Quản lý kết nối cơ sở dữ liệu, chịu trách nhiệm đảm bảo các thao tác lưu trữ và truy vấn diễn ra suôn sẻ.

- Thuộc tính:

  - ProjectManagementController (control):
  
    - projectData: Dữ liệu dự án cần thiết cho việc tạo mới hoặc cập nhật dự án.
    - projectId: Mã ID của dự án khi thực hiện tìm kiếm hoặc cập nhật thông tin.
      
  - IProjectManagementDatabase (interface):
  
    - Giao diện này chỉ định các phương thức mà hệ thống cơ sở dữ liệu cần phải triển khai, do đó không có thuộc tính nào.
      
  - ProjectManagementDatabase (subsystem proxy):
  
    - databaseConnection: Kết nối tới cơ sở dữ liệu.
    - transactionId: Mã giao dịch của mỗi thao tác lưu trữ hoặc truy vấn.
  
  - Project (entity):
  
    - projectId: Mã ID của dự án.
    - projectName: Tên của dự án.
    - startDate: Ngày bắt đầu dự án.
    - endDate: Ngày kết thúc dự án.
    - status: Trạng thái của dự án (ví dụ: Đang tiến hành, Hoàn thành).
    - budget: Ngân sách dự án.
    - resources: Các tài nguyên liên quan đến dự án.
      
  - DatabaseConnection:
  
    - connectionString: Chuỗi kết nối tới cơ sở dữ liệu.
    - status: Trạng thái kết nối, ví dụ: "Đã kết nối", "Lỗi kết nối".

# Analysis class to design element map

## BankSystem

| Analysis Class	 | Design Element |
| ----------- | ----------- |
| PayrollController | Controller / Facade |
| IBankSystem | Interface / Banking API |
| BankSystem	 | Subsystem (Banking) |
| Paycheck | Entity Class / Domain Object |
| BankInformation | Entity Class / Domain Object |

## PrintService

| Analysis Class	 | Design Element |
| ----------- | ----------- |
| PayrollController | Controller / Facade |
| IPrintService | Interface / Banking API |
| PrintService	 | Subsystem (Banking) |
| Document | Entity Class / Domain Object |
| Status | Value Object / Domain Object |
| Queue | Value Object / Domain Object |

## ProjectManagementDatabase subsystems

| Analysis Class	 | Design Element |
| ----------- | ----------- |
| ProjectManagementController | Controller / Facade |
| IProjectManagementDatabase | Interface (Database Access) |
| ProjectManagementDatabase	 | Database Subsystem / DAO |
| Project | 	Entity Class / Domain Object |
| DatabaseConnection | Connection Manager / Singleton |

# Design element to owning package map

## BankSystem

| Design Element		 | 	Owning Package |
| ----------- | ----------- |
| PayrollController | com.payroll.controller |
| IBankSystem | 	com.bank.api |
| BankSystem	 | com.bank.system |
| Paycheck | com.payroll.entity |
| BankInformation | com.bank.entity |

## PrintService

| Design Element		 | 	Owning Package |
| ----------- | ----------- |
| PayrollController | 	com.payroll.controller |
| IPrintService | 		com.print.api |
| PrintService	 | com.print.service |
| Document | com.print.entity |
| Status | com.print.entity |
| Queue | com.print.entity |

## ProjectManagementDatabase subsystems

| Design Element		 | 	Owning Package |
| ----------- | ----------- |
| ProjectManagementController	 |com.project.controller |
| IProjectManagementDatabase | 		com.project.api |
| ProjectManagementDatabase		 | com.project.database |
| Project | com.project.entity |
| DatabaseConnection | com.project.entity |


# Architectural layers and their dependencies

Biểu đồ:

![alt text](https://www.planttext.com/api/plantuml/png/l5PBZjD04Dtx5AtPa9781QnHD0op2SgC0Zb1krsJcB6xhVv4CYXh3i46Ji01ic0n9vaJS0MgxNRS_dG02SWYjglhywfULTa_Zj-lbQPIcoAFefAoHxe5Sh6Me81hgZF1oOfM82_8nuZWZ-LKARAcbHHv_bfmRQyWoTKLQnuM2wTP_wJXJdTssKbBcN6DShO3zkWE3hvxATu3qtUK8ve2WVmw49D0DJX3FzOMj9FULClKFp5bEZ8vH0Ul33T6PHmGq4fiCzOl16O0ye4o8CiRoXytbT9G8BgJl8ylXLAeJCzectPCshkNrfUmJc9Y_vVyGSYYhhrV6Y_WsjPl0tAVuLCmP5tbMIgOiIMCoQsx6nQdDjyWsKRDBcFIt4tfl3LWmAhKDo5e0-fkgQO9LMTmAhe_iL0srxXj0G_h0sYsywbqkiiqjW0kJpOEcDTFFOAKILHz_xS9QdktnqqWsl_Z9Z1H7Yq1YF-85d--B0ZoYh5wnCPRfiM8qy_HWTr57RuvEqat6ckmjTMnrmwQA85tjlxeirpuRgTMaECUwuFLodJLAywS5i9Otb9XaXmwEHHbBYe0btrtKD8Aqu7O9ZMcPz1LeQ2CsQZtfaX0ZjATIs4q2aB72SQufmNqJdmGRGy6ehVDEahDxkEwYOSHctp6ycPNfuDwr4Sg-u2oN4p0QthVHvIfTq3JAYQ943bGxj4WfP1ts5ROPkFu9Ir1hc0F-I0JBVZem8TGpvQF01iiHTTlHA9YiigKlcgBkEYQZQOfAfmVTWc5s8ElrivFRzXh02lWMxspi-w3HuX0spKGcly0jVsH7Sb7NTDGPJyRfZZ4cao94vDY1hsHgRV12omhvMJtVFn4jjdpyHibxEah8_dpyND9zazVI6vNWuh67ntp-MBmCeo9KO2gPpuWd55e7peFaVzMjoRU8rO9nxmsKr4_ljKS0EhhXi8sXc5GdfTeWEoqgc9yhGYxJ17_17f_mVYgemHEY-2ibfl7c1GrtWcDPbnyXT_87lML5j9ICB7_HqmutwHx6uJC1hJyYM6ObWalqJKEWFsS_Wa00F__0m00)

