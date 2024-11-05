
# Các ca sử dụng còn lại của hệ thống PayrollSystem

## Manage Employee Information 

### Mô tả ca sử dụng:
- Cho phép quản lý thông tin nhân viên trong hệ thống, bao gồm các thao tác thêm mới, sửa đổi, xóa và tìm kiếm nhân viên. Các thông tin có thể bao gồm mã nhân viên, tên, chức vụ, mức lương, các thông tin liên quan đến bảo hiểm và thuế.
### Các hành động chính:
- Thêm nhân viên: Nhập thông tin mới của nhân viên vào hệ thống.
- Chỉnh sửa thông tin nhân viên: Cập nhật các thông tin thay đổi như chức vụ, lương, và các thông tin cá nhân.
- Xóa nhân viên: Xóa thông tin nhân viên khỏi hệ thống khi họ rời công ty.
- Xem thông tin nhân viên: Truy xuất thông tin chi tiết về từng nhân viên.
### Lớp phân tích liên quan:
- Employee: Đại diện cho thông tin của nhân viên.
- EmployeeManager: Quản lý các thao tác thêm, sửa, xóa và tìm kiếm thông tin nhân viên.
### Thuộc tính:

- Add Employee (Thêm nhân viên)

employeeId: Mã nhân viên (String).

name: Tên nhân viên (String).

position: Chức vụ của nhân viên (String).

salary: Mức lương của nhân viên (Double).

contactInfo: Thông tin liên lạc của nhân viên (String).

dateOfJoining: Ngày gia nhập của nhân viên (Date).

- Update Employee Information (Cập nhật thông tin nhân viên)

employeeId: Mã nhân viên cần cập nhật (String).

newName: Tên mới của nhân viên (String).

newPosition: Chức vụ mới của nhân viên (String).

newSalary: Mức lương mới của nhân viên (Double).

newContactInfo: Thông tin liên lạc mới của nhân viên (String).

- Delete Employee (Xóa nhân viên)

employeeId: Mã nhân viên cần xóa (String).

View Employee Information (Xem thông tin nhân viên)

employeeId: Mã nhân viên cần xem (String).

employeeInfo: Thông tin chi tiết của nhân viên (Employee object).

### Phương thức: 
- addEmployee(String id, String name, String position, double salary): Thêm nhân viên.
  
- updateEmployee(String id, String newName, String newPosition, double newSalary): Cập nhật thông tin nhân viên.
  
- deleteEmployee(String id): Xóa nhân viên.
  
- getEmployeeInfo(String id): Lấy thông tin nhân viên.
### Biểu đồ ca sử dụng:
![alt text](https://www.planttext.com/api/plantuml/png/V92z2i8m54RtFCMbUmVRJWvIKQ4EWbJgVcclfP2VagH84P_CmKVo5Kmbbjh1CPoJZvEy7i_KMDIs4vnXQPM60qgiIVjJbZDDfKLPSuBWYBrMdCEfDvP403S6q1agqJYuhYhOYPQhdYW0D51i5bDUj1LQ6XNOoulI0csZfDUZgRubJXFTA_5KEJTq_RUNi3jZ_ZqGXgkX29OmX9A_DSEHmxxpQq3ZTcTQx3JVDmvbkOU9Wv-otuMKP3NyyXi00F__0m00).

## Generate Payroll Report

### Mô tả ca sử dụng:
- Tạo ra các báo cáo lương cho nhân viên dựa trên dữ liệu từ hệ thống, cung cấp thông tin chi tiết về số tiền lương, phụ cấp, và các khoản khấu trừ cho mỗi nhân viên trong một kỳ tính lương.
### Các hành động chính:
- Tạo báo cáo lương: Tạo báo cáo tổng hợp cho tất cả nhân viên hoặc từng nhân viên.
- Xem báo cáo lương: Xem chi tiết các khoản chi trả, khấu trừ và lương cuối cùng.
- Xuất báo cáo: Xuất báo cáo dưới các định dạng khác nhau như PDF, Excel.
### Lớp phân tích liên quan:
- PayrollReport: Lớp này chứa các phương thức để tạo và lưu trữ báo cáo lương.
- Employee: Cung cấp thông tin nhân viên, mức lương và số giờ làm việc để tính toán báo cáo.
- SalaryCalculator: Đảm bảo tính toán chính xác các khoản chi trả cho nhân viên.
### Thuộc tính: 
- Generate Payroll Report (Tạo báo cáo lương)

reportPeriod: Thời gian báo cáo (String, ví dụ: "Tháng 10/2024").

employeeList: Danh sách nhân viên trong kỳ báo cáo (List<Employee>).

totalPayroll: Tổng số tiền lương trong kỳ báo cáo (Double).

payrollDetails: Chi tiết bảng lương cho từng nhân viên (Map<Employee, Double>).


- View Payroll Report (Xem báo cáo lương)

reportId: Mã báo cáo lương cần xem (String).

payrollReport: Nội dung chi tiết của báo cáo lương (PayrollReport object).

### Phương thức: 
- generateReport(Date period, List<Employee> employees): Tạo báo cáo lương.
  
- viewReport(String reportId): Xem báo cáo lương.
  
- getPayrollDetails(String employeeId): Lấy chi tiết lương của nhân viên.

### Biểu đồ ca sử dụng:
![alt text](https://www.planttext.com/api/plantuml/png/VD2n2i9030RWFKyHkdUmeuDK7EmYI8lkeOsbSBsMN8eKySaSV2HVmMivHKISBiTzVqZkSRkdJabqQ0rGgPtWZYpLBE6MvQ5O3rNZJn0kbMnj6ACzZT8PWyNebDi8Bu0uE2x9-SSjMnPInfVAkUz48oI7XytYanuRFlzc2Lm1ma0OnwifYKjyz-v3IEOGP7b0YKTproyGblYlyEG5JRAnDQHig-bpdW000F__0m00)
## Handle Leave and Absence

### Mô tả ca sử dụng:
- Quản lý các yêu cầu nghỉ phép và vắng mặt của nhân viên. Điều này bao gồm việc nhân viên đăng ký nghỉ phép, xử lý các yêu cầu này và cập nhật hệ thống về các ngày nghỉ, ngày vắng mặt.
### Các hành động chính: 
- Đăng ký nghỉ phép: Nhân viên đăng ký ngày nghỉ phép hoặc nghỉ bệnh.
- Phê duyệt yêu cầu nghỉ phép: Người quản lý duyệt hoặc từ chối các yêu cầu nghỉ phép.
- Cập nhật vắng mặt: Ghi nhận các ngày vắng mặt không có lý do.
- Điều chỉnh lương: Cập nhật thông tin lương khi có sự thay đổi do nghỉ phép hoặc vắng mặt.
### Lớp phân tích liên quan:
- LeaveRequest: Đại diện cho các yêu cầu nghỉ phép của nhân viên.
- Employee: Thông tin về nhân viên đăng ký nghỉ phép.
- AttendanceManager: Quản lý các thao tác liên quan đến nghỉ phép và vắng mặt.
- PayrollSystem: Cập nhật các thay đổi vào bảng lương khi có nghỉ phép hoặc vắng mặt.
### Thuộc tính: 
- Request Leave (Yêu cầu nghỉ phép)

employeeId: Mã nhân viên yêu cầu nghỉ phép (String).

leaveStartDate: Ngày bắt đầu nghỉ (Date).

leaveEndDate: Ngày kết thúc nghỉ (Date).

leaveType: Loại nghỉ phép (String: ví dụ "Nghỉ ốm", "Nghỉ phép thường", "Nghỉ không lương").

leaveReason: Lý do nghỉ phép (String).

- Approve Leave (Phê duyệt nghỉ phép)

employeeId: Mã nhân viên yêu cầu nghỉ phép (String).

leaveStartDate: Ngày bắt đầu nghỉ (Date).

leaveEndDate: Ngày kết thúc nghỉ (Date).

leaveApprovalStatus: Trạng thái phê duyệt (Boolean: true - Phê duyệt, false - Từ chối).

- Reject Leave (Từ chối nghỉ phép)

employeeId: Mã nhân viên yêu cầu nghỉ phép (String).

leaveStartDate: Ngày bắt đầu nghỉ (Date).

leaveEndDate: Ngày kết thúc nghỉ (Date).

leaveReasonForRejection: Lý do từ chối (String).

- Update Leave Status (Cập nhật trạng thái nghỉ phép)

employeeId: Mã nhân viên nghỉ phép (String).

leaveStartDate: Ngày bắt đầu nghỉ (Date).

leaveEndDate: Ngày kết thúc nghỉ (Date).

newLeaveStatus: Trạng thái mới của nghỉ phép (String: ví dụ "Đã phê duyệt", "Đang xử lý", "Từ chối").

- Update Payroll for Leave (Cập nhật bảng lương cho nghỉ phép)

employeeId: Mã nhân viên nghỉ phép (String).

leaveDays: Số ngày nghỉ phép (Integer).

adjustedSalary: Lương điều chỉnh cho nhân viên (Double, ví dụ sau khi trừ đi các ngày nghỉ không lương).

### Phương thức: 
- requestLeave(String id, Date start, Date end, String type): Yêu cầu nghỉ phép.
  
- approveLeave(String id, Date start, Date end): Phê duyệt nghỉ phép.
  
- rejectLeave(String id, Date start, Date end, String reason): Từ chối nghỉ phép.
  
- updateLeaveStatus(String id, Date start, Date end, String status): Cập nhật trạng thái nghỉ phép.
  
### Biểu đồ ca sử dụng:
![alt text](https://www.planttext.com/api/plantuml/png/R9712e9048Rl-nI3Tm-fNJf44O67Wb1wWC4c8LRTTaT1eYVhq2Fr2gssaeB7uVjdzflPp-kzCOoQwq8ApBZIi2-Kh5eYLnwnn9oqg-94QCeOormIU2TiTIKbfArXAZnu283QK8R6meJkDHc60s537g21ysun3coLqbL3aq0mdN2pRqruEEPdTK5s_P0oScrSB9g93R9NkyPuv58yXHYM1jzVTvwmWi5VTbdXpk1uOFcWFyV3lh-t_-4uSIIon0dr14pl_Gyi_m4rClwDsL1vwNxg2m00__y30000)
## Audit and Compliance

### Mô tả ca sử dụng:
- Đảm bảo hệ thống tính lương và các quy trình khác tuân thủ đúng theo luật pháp và các quy định nội bộ của công ty. Các kiểm tra này bao gồm việc tuân thủ các quy định về thuế, bảo hiểm, và các khoản khấu trừ bắt buộc.
### Các hành động chính: 
- Kiểm tra bảng lương: Đảm bảo rằng tất cả các khoản thanh toán và khấu trừ là hợp lý và đúng đắn.
- Kiểm tra tuân thủ pháp lý: Kiểm tra các thông tin liên quan đến thuế, bảo hiểm xã hội, và các yêu cầu pháp lý khác.
- Tạo báo cáo kiểm tra: Tạo báo cáo để phục vụ cho các cuộc kiểm toán hoặc cho cơ quan chức năng.
### Lớp phân tích liên quan:
- PayrollAudit: Lớp này thực hiện các kiểm tra và kiểm toán bảng lương.
- Employee: Cung cấp thông tin về nhân viên để xác nhận các khoản thanh toán và khấu trừ.
- ComplianceManager: Đảm bảo tuân thủ các quy định về thuế, bảo hiểm và các yêu cầu pháp lý khác.
### Thuộc tính:
- Perform Payroll Audit (Kiểm toán bảng lương)

auditPeriod: Thời gian kiểm toán (String: ví dụ "Quý 1 2024").

auditResults: Kết quả kiểm toán (AuditResult object).

discrepanciesFound: Các sai lệch phát hiện trong bảng lương (List<Discrepancy>).

- Ensure Legal Compliance (Đảm bảo tuân thủ pháp lý)

complianceCheck: Kiểm tra tính hợp pháp của bảng lương (Boolean: true - hợp pháp, false - không hợp pháp).

complianceReport: Báo cáo tuân thủ pháp lý (ComplianceReport object).

regulatoryRequirements: Các yêu cầu pháp lý cần tuân thủ (List<String>).

- Generate Compliance Report (Tạo báo cáo tuân thủ)

reportPeriod: Thời gian báo cáo (String: ví dụ "Tháng 6/2024").

complianceDetails: Chi tiết về tuân thủ trong kỳ (ComplianceReport object).

nonComplianceIssues: Các vấn đề không tuân thủ (List<String>).

### Phương thức: 
- performAudit(Date period, List<PayrollReport> reports): Kiểm toán báo cáo lương.
  
- ensureCompliance(List<PayrollReport> reports): Kiểm tra tính tuân thủ.
  
- generateComplianceReport(Date period, List<PayrollReport> reports): Tạo báo cáo tuân thủ.
  
- identifyDiscrepancies(List<AuditReport> auditReports): Phát hiện sai lệch trong báo cáo kiểm toán.
  
### Biểu đồ ca sử dụng:
![alt text](https://www.planttext.com/api/plantuml/png/JD312e9040RW-pp5uDr3UkiGXaGT2iBe0OPr4c7TbTdr8D6JTUYHUeLKLlEq3Finyyzytv_CUHBVDHf8UIkuxyfwU4Dr8KCLpzMf067boLIQCRfIBrPhlFNESnFX4n0xnuhS-CdoiDBWZAQs4PB3UxvPmuDndJ2UkIADkMrQNPDH76YofaSsBEHvnR3WrihSE8KNG5W0utWtpi8jpbdQa8L60M6ru9B1XIXwYgAM6N0g0ae7j8Ju0vGf16Hiol6Gy0C00F__0m00)

# Code java mô phỏng ca sử dụng Maintain Timecard.

## Lớp Employee





    public class Employee {

    private String employeeId;
    
    private String name;

    public Employee(String employeeId, String name) {
        this.employeeId = employeeId;
        this.name = name;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public String getName() {
        return name;
    }

    @Override
    public String toString() {
        return "Employee ID: " + employeeId + ", Name: " + name;
    }
    }


## Lớp PayrollSystem




    import java.util.HashMap;

    import java.util.Map;

    public class PayrollSystem {

    private Map<String, Employee> employees;  
    
    private Map<String, Timecard> timecards;  

    public PayrollSystem() {
        employees = new HashMap<>();
        timecards = new HashMap<>();
    }

    public void addEmployee(String employeeId, String name) {
        if (employees.containsKey(employeeId)) {
            System.out.println("Employee with ID " + employeeId + " already exists.");
            return;
        }
        Employee employee = new Employee(employeeId, name);
        employees.put(employeeId, employee);
        timecards.put(employeeId, new Timecard());
        System.out.println("Added new employee: " + employee);
    }

    public void updateEmployee(String employeeId, String newName) {
        Employee employee = employees.get(employeeId);
        if (employee != null) {
            employee = new Employee(employeeId, newName);
            employees.put(employeeId, employee);
            System.out.println("Updated employee: " + employee);
        } else {
            System.out.println("Employee with ID " + employeeId + " not found.");
        }
    }

    public void deleteEmployee(String employeeId) {
        Employee employee = employees.remove(employeeId);
        if (employee != null) {
            timecards.remove(employeeId);  // Xóa bảng chấm công tương ứng
            System.out.println("Deleted employee: " + employee);
        } else {
            System.out.println("Employee with ID " + employeeId + " not found.");
        }
    }

    public void displayEmployees() {
        if (employees.isEmpty()) {
            System.out.println("No employees in the system.");
        } else {
            System.out.println("Employees in the system:");
            for (Employee employee : employees.values()) {
                System.out.println(employee);
            }
        }
    }

    public void checkIn(String employeeId) {
        Timecard timecard = timecards.get(employeeId);
        if (timecard != null) {
            timecard.checkIn();
        } else {
            System.out.println("Employee not found.");
        }
    }

    public void checkOut(String employeeId) {
        Timecard timecard = timecards.get(employeeId);
        if (timecard != null) {
            timecard.checkOut();
        } else {
            System.out.println("Employee not found.");
        }
    }

    public void displayWorkedHours(String employeeId) {
        Timecard timecard = timecards.get(employeeId);
        if (timecard != null) {
            System.out.println("Worked hours for " + employeeId + ": " + timecard.getWorkedHours() + " hours");
        } else {
            System.out.println("Employee not found.");
        }
    }

    public void displayWorkDuration(String employeeId) {
        Timecard timecard = timecards.get(employeeId);
        if (timecard != null) {
            System.out.println("Worked duration for " + employeeId + ": " + timecard.getWorkDuration());
        } else {
            System.out.println("Employee not found.");
        }
    }
    }

## Lớp Timecard




    import java.time.LocalDateTime;

    import java.time.Duration;

    public class Timecard {

    private LocalDateTime checkInTime;
    
    private LocalDateTime checkOutTime;

    public void checkIn() {
        this.checkInTime = LocalDateTime.now();
        System.out.println("Checked in at: " + checkInTime);
    }

    public void checkOut() {
        this.checkOutTime = LocalDateTime.now();
        System.out.println("Checked out at: " + checkOutTime);
    }

    public long getWorkedHours() {
        if (checkInTime == null || checkOutTime == null) {
            return 0;
        }
        Duration duration = Duration.between(checkInTime, checkOutTime);
        return duration.toHours(); // return hours worked
    }

    public String getWorkDuration() {
        if (checkInTime == null || checkOutTime == null) {
            return "Work time not complete.";
        }
        Duration duration = Duration.between(checkInTime, checkOutTime);
        return String.format("%d hours and %d minutes", duration.toHours(), duration.toMinutesPart());
    }
    }


## Lớp PayrollSystemTest



    public class PayrollSystemTest {

    public static void main(String[] args) {
    
        PayrollSystem payrollSystem = new PayrollSystem();

        System.out.println("Adding employees...");
        payrollSystem.addEmployee("E001", "John Doe");
        payrollSystem.addEmployee("E002", "Jane Smith");

        System.out.println("\nUpdating employee information...");
        payrollSystem.updateEmployee("E001", "John A. Doe");

        System.out.println("\nDeleting employee...");
        payrollSystem.deleteEmployee("E002");

        System.out.println("\nDisplaying all employees...");
        payrollSystem.displayEmployees();

        System.out.println("\nEmployee E001 checking in...");
        payrollSystem.checkIn("E001");

        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("\nEmployee E001 checking out...");
        payrollSystem.checkOut("E001");

        System.out.println("\nDisplaying work duration for E001...");
        payrollSystem.displayWorkDuration("E001");

        payrollSystem.displayWorkedHours("E001");
    }
    }
