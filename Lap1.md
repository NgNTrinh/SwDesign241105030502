# **LAP 1**
## **Phân tích kiến trúc, cơ chế, ca sử dụng hệ thống "Payroll System"**
>Nguyễn Ngọc Trình
>MSV: 4451051154

### 1.Phân tích kiến trúc

- Kiến trúc được em đề xuất là: **Kiến trúc phân lớp "Layered Architecture"**

- Lý do em lựa chọn kiến trúc phân lớp là vì:

    *Mỗi lớp có trách nhiệm rõ ràng, giúp dễ bảo trì và phát triển.*

    *Các thành phần trong từng lớp có khả năng tái sử dụng trong các ứng dụng khác.*

    *Dễ dàng mở rộng hệ thống bằng cách thêm các lớp mới hoặc cải thiện các lớp hiện tại mà không làm ảnh hưởng đến toàn bộ hệ thống.*

    *Bằng cách quản lý quyền truy cập tại các lớp khác nhau, có thể cải thiện bảo mật tổng thể của hệ thống.*

- Ý nghĩa của từng thành phần trong kiến trúc.

    **Lớp Giao diện Người dùng (Presentation Layer):** Là điểm tương tác chính giữa nhân viên và hệ thống. Giao diện này giúp người dùng dễ dàng nhập dữ liệu, xem báo cáo và thực hiện các tác vụ liên quan đến payroll.

    **Lớp Logic Kinh doanh (Business Logic Layer):** Chứa tất cả các quy tắc và phép tính liên quan đến payroll, đảm bảo tính chính xác và nhất quán trong việc xử lý dữ liệu.

    **Lớp Truy cập Dữ liệu (Data Access Layer):** Quản lý việc lưu trữ và truy xuất dữ liệu từ các nguồn khác nhau, bao gồm cơ sở dữ liệu địa phương và các hệ thống bên ngoài như DB2.

    **Dịch vụ Lập Lịch (Scheduler Service):** Tự động hóa quy trình payroll để giảm thiểu sai sót và đảm bảo thanh toán đúng hạn cho nhân viên.

    **Mô-đun Quản trị (Administration Module):** Cung cấp công cụ quản lý thông tin nhân viên cho bộ phận nhân sự (HR), giúp họ duy trì tính chính xác của dữ liệu.

- Biểu đồ package mô tả kiến trúc.

![Diagram](https://www.planttext.com/api/plantuml/png/XD9DJW8n50Vm_PpYXJqN81C2XeZ6WQZW0MgdpZIK5lj19CQr2rUiYGjYZ8dHoCADJ8oBCToZ9_0ATeP4GPWuksdxVkdxltub7pMbaTIcppnFzIW7AHJnDDMCm9vDha77DXdp20xHI0hcJWqGxg68G6dRTWakFG_SztCgiCba04sA18JKLN1eHukPJMufXEaRZqg059me8lUv9l8COGA-lojOI6IrwhGCkzfg1YAY60ueZo4KYCUvj6CKvKIfvQRl7nEi4OyO-GVhIZC2REVF0sZOv0LOTbUJamsaKHrZXpel-pb5gfXprJSuXg5DxY78lI1VoQaEZabe6ELHXyWXNVOgKR-OQwMlvS-nuN1axFoEWvPEowrwsAUSAYsHfeAtX7CphYt23MqztdAv-YUc2ZHjyanXb3wQB8G70nTk0LZwdjTlNhlOOCl-jKoVt63McFM2Z5Y9jWBTnMmnTKz9frESvJTnB-Ht50MDR4sXiZhEyvNWF1T8ZV0mU-xV0000__y30000)

### 2 .Đề xuất cơ chế 

*Các cơ chế này bao gồm:*

- **Cơ chế quản lý thông tin nhân viên:** Quản lý dữ liệu nhân viên bao gồm tên, mã số, loại (giờ, lương, hoa hồng), tỷ lệ hoa hồng, phương thức thanh toán.

    **Lý do:** Để lưu trữ và truy cập thông tin cần thiết về nhân viên phục vụ tính toán lương và thực hiện báo cáo.

- **Cơ chế quản lý chấm công:** Ghi nhận giờ làm, quản lý giờ làm thêm và mã dự án mà nhân viên làm việc.

    **Lý do:** Đảm bảo rằng dữ liệu chấm công của nhân viên được ghi nhận chính xác, bao gồm giờ làm thêm để trả đúng lương.

- **Cơ chế quản lý đơn hàng bán hàng:** Ghi nhận các đơn hàng, ngày bán và doanh thu từ nhân viên bán hàng.

    **Lý do:** Giúp tính toán hoa hồng cho nhân viên bán hàng dựa trên doanh số, hỗ trợ tính toán lương chính xác.

- **Cơ chế tích hợp với cơ sở dữ liệu dự án (DB2):** Kết nối và truy xuất thông tin dự án từ hệ thống Project Management Database.

    **Lý do:** Đảm bảo dữ liệu về mã dự án và thông tin tính phí được đồng bộ, chính xác.

- **Cơ chế quản lý phương thức thanh toán:** Cho phép chọn phương thức thanh toán: gửi qua bưu điện, chuyển khoản, hoặc nhận trực tiếp.

    **Lý do:** Đảm bảo sự linh hoạt trong chi trả, đáp ứng yêu cầu của từng nhân viên.

- **Cơ chế tự động hóa tính lương và thanh toán:** Tự động xử lý thanh toán vào mỗi thứ Sáu và ngày làm việc cuối tháng.

    **Lý do:** Đảm bảo tính đúng hạn, giảm tải công việc thủ công, đảm bảo trả lương chính xác.

- **Cơ chế tạo và truy vấn báo cáo nhân viên:** Cung cấp báo cáo cho nhân viên về số giờ làm, thu nhập, và giờ nghỉ phép còn lại.

    **Lý do:** Tăng cường minh bạch, giúp nhân viên tự kiểm tra thông tin lương và giờ làm.

- **Cơ chế phân quyền và bảo mật dữ liệu:** Giới hạn quyền truy cập của nhân viên và quyền quản trị của Payroll Administrator.

    **Lý do:** Đảm bảo tính bảo mật của dữ liệu nhạy cảm và ngăn chặn truy cập trái phép vào thông tin nhân viên khác.

### 3. Phân tích Ca Sử Dụng "Maintain Timecard"

**Xác định các lớp phân tích**

- Employee (Nhân viên)

- Timecard (Phiếu chấm công)

- ChargeNumber (Mã số chi phí)

- ProjectManagementDatabase

- TimecardSystem

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/X5EnQjn04EttA-O7_0C75qniaoAn2TW_i5ejsasarKKQ2LIdC2bI61SfGeWlHmW4ZhX8TLkuMEF_s2_mBtXsxuZMYO9LI33pPkQzDwDxUxFV8c-mgqh61TOD75MBiXwa1Dw2P5dTcPmt0vpfIWhUvAT3YxA2aCMMYTfWKvVmkgdVI877tF12LjBW8KUUyLP6O9un2caSksph1MFpEPmezyr0hzrF0y9lrWimYZu8gDnlKm1gYbFaUmKY1kPpnYJiFIC2CpZszYjaVhEYH8fYl4Hu_cySqDjBG-_DKZEW1zlOIipW5Q46oBtz1QNszhnxt52M96UgurlrHECpYjLGUVjPJrAL9cTRT9xzeS6DWjOjXOBAhQ3rzc8thW_S1CipsDjvSFWKThJhH4M78wIWv1TYKl-dQXHmaAvbGW7qKTlODPdumjlrjEp48ANzvWQXtCuftDK0HQphtHLWG_u5WvKZQyUgbpJfVKLf3kZMP87oThMW9lQS3id-u2cXS0wde-h-xfh02EywjumXeg_2c6HrCkp2VjApj72tx77KzYuIH9Bwwxxkhhj98nx33bGta30pQNJBWn6f8I5lFy3jXRSVHJmbja_ly4C_0000__y30000)

**Nhiệm Vụ của Từng Lớp Phân Tích**

- *Employee:*

    Chịu trách nhiệm tương tác với hệ thống để nhập thông tin giờ làm.

    Chỉ có thể truy cập và chỉnh sửa phiếu chấm công của mình.

- *TimecardSystem:*

    Đảm bảo nhân viên chỉ có thể cập nhật phiếu chấm công cho kỳ lương hiện tại.    

    Quản lý việc lưu và xác thực phiếu chấm công, đảm bảo số giờ hợp lệ.

    Đảm bảo các yêu cầu về bảo mật và chỉ cho phép nhân viên chỉnh sửa phiếu chấm công của mình.

- *Timecard::*

    Đại diện cho phiếu chấm công, lưu trữ các thông tin về ngày làm, giờ làm cho từng mã số chi phí.
    
    Có thuộc tính startDate, endDate, status, và các giờ làm chi tiết.

    Liên kết với các mã chi phí để nhân viên có thể báo cáo giờ làm trên từng mã chi phí cụ thể.

- *ChargeNumber:*

    Lớp đại diện cho mã số chi phí hoặc dự án mà giờ làm của nhân viên được báo cáo.
    
    Thuộc tính chargeNumberID để định danh mã chi phí.

    Liên kết với Timecard để cung cấp các mã dự án mà nhân viên có thể chọn.

- *ProjectManagementDatabase::*

    Cung cấp mã số chi phí có thể chọn, dựa trên thông tin dự án của công ty.
    
    Đảm bảo rằng chỉ những mã số chi phí hợp lệ được chọn trong phiếu chấm công.

**Biểu Đồ Lớp (Class Diagram)**

![Diagram](https://www.planttext.com/api/plantuml/png/T5DDJyCm3BttLrWxROWTk5PeucD8J6A0DYJERcDrOKaw9Uwa2V7BEF2J-0kaQTUb1IwLOZy_Fp-xtvzVLuxHSgLLakGAdOCxlLFbWGZU4u0fKFjSp5DOivMc2663cde1p7DoRYMB3Rie0U2gJ4j-aPfoj68y2K4oJFQ-hAppWOzZwoDeVN1CEWW0iEIvQ4yTmqdH9ErA0dIFIWfaQeYvJPr07dzJbehGDCemOlq3_LjOwqcmREuRfL1_6v-C64GyYYlNCsbJ2tijxPPydoNkBcytQ0jwh7H6zXmMtfM2x2oeGo6QEV88aqA_8X2cnyB6MqUy3fxNIiQY4zLaDThjYb0y6NM8lOzvsp7ZneFr2tAvbJkMfUdY7TMpBTyevoKQB4ZxLVlkcA6ZTgC5yVKUfS9CKTpMtq8A3z9npvPPJTmTvNGw6vn9ChYQ6D7bO7Gn2fdHsQWtQlA_s1hUWoPNVidrd_83003__mC0)

### 4. Phân tích Ca Sử Dụng "Select Payment Method"

**Xác định các lớp phân tích**

- Employee (Nhân viên)

- PaymentMethod (Phương thức thanh toán)

- PaymentSystem

- BankAccount

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/f5G_IyD05D_lKpoS5EeNA5Ig8YvQ2ZheUBqUlT3a9IQNGcQd8WxEBgqYOa5GS6g63f5-Z_i4VWLVqfOsfOrLiuIxzzxlN-xo5O-gWUQ-3XsRSQ5T7uuSptOZAG5u098rt12Rt8-WpYD7eZwB0YsThEW5JBYeVTUU5K-bLcvpKdGORLWwWWEExNqX24TdbGPdh5A1caeU43fMCa0GoiIt29uQlutxs09DwnT1BuuAj9lq4IeLnYJixX5h6Gv_x6TUa3RBCbmcWn246Jw7cz1iepB3LmJjc_YTIfOPZhmIj4pyQi5LoC7XbbqYf30oyJL2Mxbc-8WxUMrT-BmpyGsX5adajePwWHOxwS7MAZrR3EYPEFISCfohT5k3JQrUeRqCihOIKjg1_5bEFeX58VceC_yyIxmxJIyToFhdKON4HFrFNc7_duqUvyL2nyJtLevgGzVBdtkzRvqUPsobHribFOBiq7nWuZkgzApP_DeOVZ4-OM_mCfoCtuXO9H-f0mjphOjW_mlpS3c3QPmBn8jS4fjiVWalahw0wL4M6L-sq8NtWrK99FqnVGC00F__0m00)

**Nhiệm Vụ của Từng Lớp Phân Tích**

- *Employee:*

    Chịu trách nhiệm chọn và cung cấp thông tin cho phương thức thanh toán mong muốn.

    Chỉ có thể chọn các phương thức thanh toán được cung cấp và chỉ được cập nhật phương thức thanh toán của chính mình.

- *PaymentSystem:*

    Đảm nhiệm việc xử lý các yêu cầu của nhân viên liên quan đến phương thức thanh toán.

    Gửi yêu cầu chọn phương thức thanh toán, lưu các thông tin cần thiết, và cập nhật thông tin thanh toán cho nhân viên.

    Xác nhận và lưu các thay đổi vào hệ thống.

- *PaymentMethod:*

    Lớp đại diện cho các loại phương thức thanh toán như “pick up”, “mail”, và “direct deposit”.
    
    Cung cấp các thuộc tính và thông tin cần thiết liên quan đến từng phương thức thanh toán (như địa chỉ gửi qua thư hoặc thông tin tài khoản ngân hàng).

- *BankAccount:*

    Lưu trữ thông tin ngân hàng của nhân viên cho phương thức thanh toán “direct deposit”.
    
    Bao gồm các thuộc tính như bankName và accountNumber.

**Biểu Đồ Lớp (Class Diagram)**

![Diagram](https://www.planttext.com/api/plantuml/png/X59Bhi8m3Dpd55uMYLwW2mG85Yn0I9mWDEQZ5wSbSHRLqpiP2ux45UWdeAP5UhjuFB77Op_lZxbZQTcJ5YBNqZbOKwcB2X5-1K0A6CBDAeC3swivjx2HX14WbRBeN8ILiY8ql4M-52g3VJ-i2G0EDUOSuGa5TbTd8lxUmWBjK3b6QjK1MBnvT8CARydPPvP9I_Qbaep_SQT0t_IEXNHui8chClQ3v5NNxyN8bcPgtaRPP61UhzTIcfz5dXVUSEXqh97ToFsEilDqH3jirjJOc5EH3BzEl_zhst_E84rdiVKYNaGl7pOR-zFaUrC8CKUZcdjx0G00__y30000)