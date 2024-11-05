# **LAP 2**
## **Phân tích ca sử dụng còn lại của hệ thống "Payroll System"**

>Nguyễn Ngọc Trình
>MSV: 4451051154

### 1. Phân tích Ca Sử Dụng "Create Administrative Report".

**Xác định các lớp phân tích**

- Người Dùng

- Quản Trị Viên Tiền Lương

- Báo cáo

- Hệ thống báo cáo

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/d5J1Ji904BtlLqmuQO8_mC4GlNZmeXBlfJIqeSoITaliqNZmO3pm1rHYI4Y873njOpWiwN_i5_WBpb8CHHe4cdJJsPrvCs_URB_JUJqKLY2YhiyiM_00RY8jHzW8TFfoxwa9DZoTFk9rDiiIRBCcZx1b1J5KhdJwt71rEi3sXKhu9RqLi4AuYqFXT9dDKGJSXyh6uQtJuu5WR6SIE3jVeTGWLfC8R2t74GWj4mvDWWAR5fQx6EUTQ9iOtlBRLTCr49pudA2zAc1R3MDeQlaXO34m0Rzx7Itd0eIhf5q5GIa0NVM6q3VfJlUdOqTaKodlFGFsIORmi9HJtgdQ5kjyluYv9h8Og54Ui7zpN3AVaAgXyq8QPlbY5Gh2nEPKgNKwVKNmirbKy0PwZf6q1EOeLKrbVJM4lYbK1AIkGJwihA8qE_2s5IeXiItIWqficXajfwlcaVn3T2c4Xk0muaMefU9_2d3yq2cJhfCFN0cJVnAk1opKyelk1q7I68nZvc2BrMcXlySF0000__y30000)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Người dùng:*
    Lớp cơ sở cho các loại người dùng, quản lý thông tin đăng nhập.

- *Quản Trị Viên Tiền Lương:*
    Xử lý yêu cầu tạo báo cáo, cung cấp thông tin cần thiết và quản lý việc lưu báo cáo.

- *Báo Cáo:*
    Chứa thông tin chi tiết về báo cáo (loại, thời gian, nhân viên liên quan) và phương thức để tạo và lưu báo cáo.

- *Hệ Thống Báo Cáo:*
    Tương tác với quản trị viên để thu thập thông tin, tạo báo cáo và lưu báo cáo khi được yêu cầu.

**Thuộc tính và quan hệ giữa các lớp**

- *NgườiDùng* là lớp cha cho *QuảnTrịViênTiềnLương*.

- *HệThốngBáoCáo* tương tác với *BáoCáo* để tạo và lưu báo cáo.

- *BáoCáo* chứa thông tin cần thiết để tạo báo cáo và được tạo ra bởi *HệThốngBáoCáo*.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/d9CnJiCm58RtdC8Z3Bb0L5LLsm6fLIH4n5xQoh6KlbI9ZLG10s9WO6b71YHA1qGbH0SMxA63ezp39-0Ak3Hk4WWTYEJb_Nxl-t_R-HJhHanx4MMZmEe7lJX6BavNIZoGjlm0Z2uijFceN48oJMu0kxxYhsC7dT280Dwg8rsY7IsyiBAGpFAMWqC7dOTaO5rP6UcOARu0BrBYxfHeW4UKk8PkkahdENaa5p_tEOW0pNmfFW-RSXwszDeHlgKWNR5Voevj58C9GZs9c6ev1M3vE6ag_aQJgUBFEcExHuS5hQFucdg-vFsYj3aprvTFa9dkafZMjdFhMRCIzwJD05Tp_ntkI8bRprTYbaysEITooLgR4DhkEs2FG3MWp8RYct3sNvmUO_egl9xjaffImNtvwTKkRNi_ogeAQjlrtC1V6_QFRGnXe7-8Bm000F__0m00)

**Giải thích các lớp và quan hệ**

- *NgườiDùng* 

    **Mô tả**

    Lớp cơ sở cho người dùng trong hệ thống, chứa thông tin chung như tên đăng nhập và mật khẩu.

    **Phương thức**

    Phương thức đăngNhập() cho phép người dùng đăng nhập vào hệ thống.

- *QuảnTrịViênTiềnLương* 

    **Kế thừa**

    Kế thừa từ lớp NgườiDùng, đại diện cho người dùng có vai trò quản trị viên tiền lương.

    **Thuộc tính**

    mãQuảnTrịViên để xác định duy nhất quản trị viên.

    **Phương thức**

    - tạoBáoCáo(): Gọi hệ thống để tạo báo cáo.

    - lưuBáoCáo(): Gọi hệ thống để lưu báo cáo.

- *BáoCáo* 

    **Mô tả**

    Đại diện cho báo cáo được tạo ra, chứa thông tin chi tiết về loại báo cáo, thời gian và nhân viên liên quan.

    **Thuộc tính**

    - loạiBáoCáo: Loại báo cáo (Tổng số giờ làm việc, Tổng tiền lương năm).

    - ngàyBắtĐầu và ngàyKếtThúc: Thời gian cho báo cáo.

    - tênNhânViên: Danh sách tên nhân viên liên quan.

    - nộiDungBáoCáo: Nội dung chi tiết của báo cáo.

    **Phương thức**

    - tạoBáoCáo(): Phương thức để tạo nội dung báo cáo dựa trên thông tin đã cung cấp.

    - lưuBáoCáo(): Phương thức để lưu báo cáo vào hệ thống.

- *HệThốngBáoCáo* 

    **Mô tả**

    Lớp điều phối chính, xử lý các yêu cầu từ quản trị viên và tương tác với lớp báo cáo.

    **Phương thức**

    - yêuCầuThôngTinBáoCáo(): Yêu cầu quản trị viên cung cấp thông tin để tạo báo cáo.

    - tạoBáoCáo(ngườiDùng: QuảnTrịViênTiềnLương): Tạo báo cáo dựa trên thông tin từ quản trị viên.

    - lưuBáoCáo(báoCáo: BáoCáo): Lưu báo cáo vào hệ thống.

**Quan hệ giữa các lớp**

- **Kế thừa:** Lớp *QuảnTrịViênTiềnLương* kế thừa từ lớp *NgườiDùng*, có nghĩa là tất cả các thuộc tính và phương thức của *NgườiDùng* đều có sẵn cho *QuảnTrịViênTiềnLương*.

- **Tương tác:** *HệThốngBáoCáo* tương tác với cả *BáoCáo* và *QuảnTrịViênTiềnLương* để thực hiện chức năng tạo và lưu báo cáo.

### 2. Phân tích Ca Sử Dụng "Create Employee Report".

**Xác định các lớp phân tích**

- NgườiDùng

- NhânViên

- Báocáo

- Hệthốngbáocáo

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/X5J1Qi904BtlLmmvARG_uA58ww6d7ghq7jUG3OsxacoaEPOUF9GUFFHOC2qY2D8MUaee7bRw7_i5_OLE4YLHemrasMpclPdtPfBVPDdqfUd9eEyIaqhXmHLJh_p6KNDEkYBWFTCBmRZKoQZ3T3BczhcAn0NU1fW-j4DVMdr21PUUSC7OUdbj3OGd2IaOuVHi3Mb0gEO1K1tF0f0wZWHq4GSK5vA7fC45T1lWP7kc5WKAQgv07kS4kAqc8NHr_2vXDKu1cxDR7IybIAPYMYV4T2KO7PqySnjyr0QsevCNSDMa3qFSZYYc4D3JoIUeY1i4y2fgsmXnTJmDMoPdRHLHraQY5YBKFQ_LTn1bDGmJF72iHIUFUVPDdWnKxHd5w2U-4sxntY6FQO3IqBBf81NzXG_IuPL6vxrgxBKYFozp5eQlnkej1npes9R6WZCpFej3czEArxBSdu-W57ROXj8aL63-dvwKRgWcC4phaXvEKKfppFUIZqV0-tPMbBVlw1tE3N2cuyNQ0-pLX3E4OCUEI2hZibxiPBDStzho-JQVWOfwoxH5WtqTV-DtX3gnGRCmcxGcBlYp-0C00F__0m00)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Người dùng:*
    Lớp cơ sở cho người dùng trong hệ thống, quản lý thông tin đăng nhập.

- *Nhân viên:*
    Đại diện cho nhân viên trong hệ thống, có khả năng tạo và lưu báo cáo.

- *Báo Cáo:*
    Chứa thông tin chi tiết về báo cáo được tạo, bao gồm loại báo cáo, thời gian và nội dung báo cáo.

- *Hệ Thống Báo Cáo:*
    Điều phối toàn bộ quy trình tạo báo cáo, tương tác với nhân viên để thu thập thông tin và tạo báo cáo.

**Thuộc tính và quan hệ giữa các lớp**

- *NgườiDùng* là lớp cha cho *NhânViên*, nghĩa là lớp *NhânViên* kế thừa các thuộc tính và phương thức từ lớp *NgườiDùng*.

- *HệThốngBáoCáo* tương tác với cả *BáoCáo* và *NhânViên* để thực hiện chức năng tạo và lưu báo cáo.

- *BáoCáo* chứa thông tin cần thiết để tạo báo cáo và được tạo ra bởi *HệThốngBáoCáo*.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/d9AnIiD07CRtF4L67V82ePJIPX0gNHBSOrek1-a_fRa8GHt4mRKT7GIZY5WGAxXuDtIuqFUu9_0Ll5WlkMXS36JvVtVVx_lkxeDjUWdnvoITHaOG-KbYZj1sBTWDTlWx8FFKCCkFy1KKY-8Iq2WKz7bccowPOq0xTIf7P2Y5fxGf5Cjwozw-RPx4U6oS6ueKyZiumj9QOQRylXxQ9WRoZHSqZ_iyZmVohuo-f6YxJdyf5K8f2X35qWchQJCi87wRzGLz8SL2q4TPnV79HDE6Wcw85t8Qw58YsD8Hx9LVm0y_mQwnam9gn_sxqu5WLruegRMpgfVnLJeeiykKRu0y3Es09Xlq6xUrQv5xrAAMOCTLBJLgbX3q8NDy25sU1w5Rdr8PvH0dfBCxZMxPhFdeEcUMfSKmsXfRLhSEzzS2pQCtWR5yv9y0003__mC0)

**Giải thích các lớp và quan hệ**

- *NgườiDùng* 

    **Mô tả**

    Lớp cơ sở cho các loại người dùng trong hệ thống. Chứa thông tin cơ bản như tên đăng nhập và mật khẩu, cùng với phương thức đăng nhập.

    **Phương thức**

    - đăngNhập(): Cho phép người dùng đăng nhập vào hệ thống.

- *NhânViên* 

    **Kế thừa**

    Kế thừa từ lớp NgườiDùng, đại diện cho nhân viên trong hệ thống.

    **Thuộc tính**

    - mãNhânViên: Định danh duy nhất cho nhân viên.

    **Phương thức**

    - tạoBáoCáo(): Gọi hệ thống để tạo báo cáo dựa trên các tiêu chí đã được cung cấp.  

    - lưuBáoCáo(): Gọi hệ thống để lưu báo cáo vào một vị trí xác định.

- *BáoCáo* 

    **Mô tả**

    Đại diện cho báo cáo mà nhân viên tạo ra, chứa thông tin chi tiết về báo cáo đó.

    **Thuộc tính**

    - loạiBáoCáo: Loại báo cáo (như Tổng số giờ làm việc, Tổng số giờ cho dự án, Nghỉ phép/ốm, Tổng tiền lương năm).

    - ngàyBắtĐầu và ngàyKếtThúc: Thời gian cho báo cáo.

    - sốDựÁn: Chỉ áp dụng cho báo cáo "Tổng số giờ làm việc cho dự án".

    - nộiDungBáoCáo: Nội dung chi tiết của báo cáo.

    **Phương thức**

    - tạoBáoCáo(): Phương thức để tạo nội dung báo cáo dựa trên thông tin đã cung cấp.

    - lưuBáoCáo(): Phương thức để lưu báo cáo vào hệ thống.

- *HệThốngBáoCáo* 

    **Mô tả**

    Lớp điều phối chính, xử lý các yêu cầu từ quản trị viên và tương tác với lớp báo cáo.

    **Phương thức**

    - yêuCầuThôngTinBáoCáo(): Yêu cầu nhân viên cung cấp thông tin để tạo báo cáo.

    - tạoBáoCáo(ngườiDùng: NhânViên): Thực hiện quy trình tạo báo cáo dựa trên thông tin từ nhân viên.

    - lưuBáoCáo(báoCáo: BáoCáo): Thực hiện lưu báo cáo vào vị trí đã chỉ định.

    - lấyDanhSáchSốDựÁn(): Truy vấn cơ sở dữ liệu để lấy danh sách số dự án cho báo cáo.

**Quan hệ giữa các lớp**

- **Kế thừa:** Lớp *NhânViên* kế thừa từ lớp *NgườiDùng*, có nghĩa là tất cả các thuộc tính và phương thức của *NgườiDùng* đều có sẵn cho *NhânViên*.

- **Tương tác:** 
    *HệThốngBáoCáo* tương tác với cả *BáoCáo* và *NhânViên* để thực hiện chức năng tạo và lưu báo cáo.

    *BáoCáo* chứa thông tin cần thiết để tạo báo cáo và được tạo ra bởi *HệThốngBáoCáo*.

### 3. Phân tích Ca Sử Dụng "Login".

**Xác định các lớp phân tích**

- NgườiDùng

- HệThống

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9V-h4D3tVFpNGvl3CldIiflpGl9R6eKa51oUFXxlQGZ8Ux9-QbAoaa5Yi4LnQNfEPoSQ5eKD2rWqfOAUHbFDorja2XvF2gF8KZ4uyq0sMXGcM75oZa0bab2jb0WPMbN10jo9eh3YzC1jcsCHd5V0sGQKScW0pp0vkb0p786soE9XTNOaw9Wb88XfNwoDOf0CrTNA2G0_IG4fS2422iHx7C2itP9Hc75-HbA2GVtW8CcTISubJ2DcLdW1GJRs56viFTpNb0cnxkxWRP1zAST7XXFaZlz4okrBmKBWSW0Omk00000F__0m00)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Người dùng:*
    Đại diện cho người dùng trong hệ thống. Lớp này chứa thông tin về tên đăng nhập và mật khẩu của người dùng.

- *Hệ Thống:*
    Lớp điều phối chính của hệ thống, chịu trách nhiệm xác thực người dùng và quản lý quy trình đăng nhập.

**Thuộc tính và quan hệ giữa các lớp**

- *NgườiDùng* không có quan hệ kế thừa với lớp nào khác trong trường hợp này, vì đây là một lớp độc lập, đại diện cho thông tin người dùng.

- *HệThống* tương tác với lớp *NgườiDùng* để thực hiện xác thực và quản lý quy trình đăng nhập.

- Mối quan hệ chính giữa hai lớp này là tương tác, nơi *HệThống* cần thông tin từ *NgườiDùng* để thực hiện xác thực.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niO9V-h4D3tVFpNGvl3ClNQ6QIm44IWwloZiouKXpNhfVniDTQmki589BYZBpqY6okK2X4c-WnCfIL8aZ4n5QD3Ij5ChoCrEuQhcWDdaytDqUal5mzqI4FHM75oQ3X3OcepX30vVzEjZi1bgKb9-VavgOX-aAL6Fpa7bMg5v7SYvgaEZgsg4utKgXyl2gKeNaXxkMbu8ze502zW4NiYAG9bHZh1HAYXxkMgoG_N3N_XA5mb8G6-9IXJomKxaSKlDIWF420000__y30000)

**Giải thích các lớp và quan hệ**

- *NgườiDùng* 

    **Mô tả**

    Lớp này đại diện cho người dùng trong hệ thống. Nó chứa các thông tin cần thiết để thực hiện đăng nhập, bao gồm tên đăng nhập và mật khẩu.

    **Thuộc tính**

    - tênĐăngNhập: Chuỗi chứa tên đăng nhập của người dùng.

    - mậtKhẩu: Chuỗi chứa mật khẩu của người dùng.

    **Phương thức**

    - đăngNhập(): Phương thức này sẽ được gọi khi người dùng muốn thực hiện quy trình đăng nhập, bao gồm việc nhập thông tin và xử lý kết quả.

- *HệThống* 

    **Mô tả**

    Lớp này đại diện cho hệ thống quản lý đăng nhập. Nó chịu trách nhiệm xác thực người dùng và quản lý quy trình đăng nhập.

    **Phương thức**

    - xácThựcNgườiDùng(tênĐăngNhập: String, mậtKhẩu: String): Phương thức này sẽ kiểm tra tính hợp lệ của tên đăng nhập và mật khẩu. Nó trả về true nếu thông tin hợp lệ và false nếu không.

    - đăngNhậpNgườiDùng(ngườiDùng: NgườiDùng): Phương thức này được gọi khi thông tin người dùng hợp lệ để thực hiện quy trình đăng nhập.

**Quan hệ giữa các lớp**

- **Kế thừa:** Lớp *NhânViên* kế thừa từ lớp *NgườiDùng*, có nghĩa là tất cả các thuộc tính và phương thức của *NgườiDùng* đều có sẵn cho *NhânViên*.

- **Tương tác:** 
    *NgườiDùng* gửi yêu cầu xác thực đến HệThống bằng cách cung cấp tên đăng nhập và mật khẩu.

    *HệThống* xử lý yêu cầu và trả về kết quả đăng nhập cho *NgườiDùng*.

### 4. Phân tích Ca Sử Dụng "Maintain Purchase Order".

**Xác định các lớp phân tích**

- NgườiDùng

- NhânViênĐượcHoaHồng

- ĐơnĐặtHàng

- HệThốngQuảnLýĐơnĐặtHàng

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/v5J1IiD04BtlLmmvwK6yzo05BmMb8XRn6hUX2IIJacoWFVVWGGIBFs0j8XO5GK58a1ws-1_x1Vw2ivk2gKr3fKTps6IJcVVclPdiLpQjnyAEH1BupEOYZA3foZiyzUG4PzUVBoeRyqPeDrHsWnrs7YROjgC-W4LlBbgkoeROEKvKEiP3-K498yfIwRjeo5liM637SDAFXHCm7gA8GfyoIwEEehOJCLP13ZjxSwmQzEKa0QxIXmI4AoV1BZq_Tm5TkedTddorOJOa5ber3RYQX-NP6gU2PW6Say0hDBT73ZWR40gpVG5MIwMZ48mKoBL0BeO1NMlAu0djYUc-gsMyqKPuEAyyBrc3_PHjJAg1qDo_NTpQDi4cfCWX8ceE179SviWYVAKhXLfNW3b-x82rRphHD9tOr1_JpvLyvTx8f-30K-aqM3A8O2ezMgi5bHwvdie6I40gkop0RJuInV4krsqYSjTB9iF1zdnkpyo_yR_QqfCZdXUDeC-6lsWjpLsIfx-iiBrE2nsktm000F__0m00)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Người dùng:*
    Lớp này đại diện cho người dùng trong hệ thống, có thể là nhân viên hoặc quản lý. Nó định nghĩa những thuộc tính cơ bản cần thiết để người dùng đăng nhập vào hệ thống.

- *Nhân Viên Được Hoa Hồng:*
    Lớp này kế thừa từ lớp NgườiDùng và đại diện cho các nhân viên có hoa hồng, cho phép họ thực hiện các thao tác liên quan đến đơn đặt hàng.

- *Đơn Đặt Hàng:*
    Lớp này đại diện cho đơn đặt hàng, chứa tất cả các thông tin liên quan đến đơn hàng mà nhân viên ghi nhận.

- *Hệ Thống Quản Lý Đơn Đặt Hàng:*
    Lớp này là lớp điều phối chính của hệ thống, chịu trách nhiệm xử lý tất cả các yêu cầu liên quan đến đơn đặt hàng từ nhân viên.

**Thuộc tính và quan hệ giữa các lớp**

- Lớp *NhânViênĐượcHoaHồng* kế thừa từ *NgườiDùng*.

- *NhânViênĐượcHoaHồng* tương tác với *HệThốngQuảnLýĐơnĐặtHàng* để thực hiện các thao tác với đơn đặt hàng.

- *HệThốngQuảnLýĐơnĐặtHàng* tương tác với *ĐơnĐặtHàng* để thực hiện các thao tác tạo, cập nhật và xóa đơn hàng.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/l5H1Ji905Dtt5BFKHI_G64822nAGQ6pSDuNCJAI_IgT6egvS6ED6ujg4oi98D27HnDY6i1Z2FUO4Ni6PWa0B55Ps-Vzx_x_tPgO_qJ3lCQl9VAUXsGtByr0LZ_iYUg95_WqONMf8VOptOFGmkW5S9I9yFpNG4MjIm9Ek8qkiB1klVh8nQiyfExi6EdTfJRlM_ZOH_Wp7D1wjTdRjackLHFGut-lmxXnb80figeVmdYDPWQIAy8kLU0VmR4CCiTNIU3NB1bxm3sijOYOsZLXGc6ujw3mXFB19NAqe2zBTRJeY4TrR1IAYEvDOG4oN1v24U2Bime6ArzdtBGDLgCVs9e3S106OTre6AbgiFisdAS80i2dNq-Gm9XlkloQdF9lINnlmeQ-iLFXWNPejtlCB8dpnfV9FgPz2jeBLRc3n2XjPzqmEIxCtPx3ko3TdinMJyJUdJ4KuNBxW6Vmb6pB_v5FUkzBrh2oqhFUewxdj3j90RDoNDInz1BQs5KSDNp7eB2QW1Xze-JhKv2_g5m00__y30000)

**Giải thích các lớp và quan hệ**

- *NgườiDùng* 

    **Mô tả**

    Lớp cơ sở đại diện cho người dùng trong hệ thống. Nó chứa các thông tin cần thiết để thực hiện đăng nhập, bao gồm tên đăng nhập và mật khẩu.

    **Thuộc tính** 

    - tênĐăngNhập: Chuỗi chứa tên đăng nhập của người dùng.

    - mậtKhẩu: Chuỗi chứa mật khẩu của người dùng.

    **Phương thức**

    - đăngNhập(): Phương thức cho phép người dùng đăng nhập vào hệ thống.

- *NhânViênĐượcHoaHồng* 

    **Kế thừa**

    Kế thừa từ lớp NgườiDùng, đại diện cho nhân viên có hoa hồng.

    **Thuộc tính**

    - mãNhânViên: Định danh duy nhất cho nhân viên.

    **Phương thức**

    - thêmĐơnĐặtHàng(): Thực hiện việc thêm một đơn đặt hàng mới vào hệ thống.

    - cậpNhậtĐơnĐặtHàng(): Cập nhật thông tin đơn đặt hàng hiện có.

    - xóaĐơnĐặtHàng(): Xóa một đơn đặt hàng khỏi hệ thống.

- *ĐơnĐặtHàng* 

    **Mô tả**

    Lớp đại diện cho đơn đặt hàng, chứa thông tin liên quan đến đơn hàng được ghi nhận bởi nhân viên.

    **Thuộc tính**

    - mãĐơnĐặtHàng: Định danh duy nhất cho đơn đặt hàng.

    - kháchHàngLiênHệ: Tên của người liên hệ từ khách hàng.

    - địaChỉThanhToán: Địa chỉ thanh toán của khách hàng.

    - sảnPhẩmMua: Danh sách các sản phẩm đã mua.

    - ngày: Ngày lập đơn đặt hàng.

    - trạngThái: Trạng thái của đơn hàng (Mở, Đóng).

    **Phương thức**

    - tạoĐơnĐặtHàng(): Tạo mới một đơn đặt hàng.

    - cậpNhậtĐơnĐặtHàng(): Cập nhật thông tin cho một đơn đặt hàng.

    - xóaĐơnĐặtHàng(): Xóa một đơn đặt hàng khỏi hệ thống.

- *HệThốngQuảnLýĐơnĐặtHàng* 

    **Mô tả**

    Lớp điều phối chính cho quản lý đơn đặt hàng, xử lý các yêu cầu từ nhân viên và quản lý thông tin đơn đặt hàng.

    **Phương thức**

    - yêuCầuThôngTinĐơnĐặtHàng(): Yêu cầu nhân viên cung cấp thông tin để thao tác với đơn hàng.

    - tạoĐơnĐặtHàng(ngườiDùng: NhânViênĐượcHoaHồng): Tạo một đơn đặt hàng mới từ thông tin của nhân viên.

    - cậpNhậtĐơnĐặtHàng(mãĐơnĐặtHàng: int): Cập nhật thông tin cho đơn hàng đã tồn tại.

    - xóaĐơnĐặtHàng(mãĐơnĐặtHàng: int): Xóa một đơn hàng dựa trên mã.

    - tìmKiếmĐơnĐặtHàng(mãĐơnĐặtHàng: int): Tìm kiếm đơn đặt hàng dựa trên mã.

**Quan hệ giữa các lớp**

- **Kế thừa:** Lớp *NhânViênĐượcHoaHồng * kế thừa từ lớp *NgườiDùng*, có nghĩa là tất cả các thuộc tính và phương thức của *NgườiDùng* đều có sẵn cho *NhânViênĐượcHoaHồng*.

- **Tương tác:** 
    *NhânViênĐượcHoaHồng* tương tác với *HệThốngQuảnLýĐơnĐặtHàng* để thực hiện các thao tác với đơn đặt hàng.

    *HệThốngQuảnLýĐơnĐặtHàng* tương tác với *ĐơnĐặtHàng để quản* lý và thao tác với thông tin đơn hàng.

### 5. Phân tích Ca Sử Dụng "Maintain Employee Information".

**Xác định các lớp phân tích**

- NgườiDùng

- QuảnTrịViênLương 

- NhânViên

- HệThốngQuảnLýNhânViên

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/t5JDIiD04BxlKmmvwK5wxq4A8WYMWbZ4Qzo69f1CIhAHvjo31_7W8zGYOb4Gz9GWFQpqFVO9V0LdDorDVw95R-QGtMLcllc-RoVvp2UDMDYHI0AVsLo44PmaAXjXErBvzPadnzYSlao7s6KNOO8TEqe1h2ELNxLTbTzYjyXkolUMA-_G55XWnt2Qni8960zHHA5FDIlnmw3dXwdZC5RH3_RsPo1rIEKu0QwoXmI4AyT1ZVRFFK2N5b7horURzWGFbng05MKQe09x2P6Ja1iqooC7_1YGLcRx0gosxWM6E1JC6T2p1M6Uq9dWxtkQy1iTX8TB73NGWkVSZJe8bGt3XLSxkoPp7Y_t417HW42Eli6jr5yYk8hW-B43re5nk6KS_fK5vdBMqIjrowVWs5FP92Y9f-AVz6zbRwKDhgVo0H88HKfGVxlcyd1MwZL9XRrBj-rWPpPzvtgi_wtpVJda1LC4_G5lAsvZtIPPEhZcR8DUzAVx0W00__y30000)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Người dùng:*
    Lớp này đại diện cho người dùng trong hệ thống, có thể là nhân viên hoặc quản lý. Nó định nghĩa những thuộc tính cơ bản cần thiết để người dùng đăng nhập vào hệ thống.

- *Quản Trị Viên Lương:*
    Ghi nhận và quản lý thông tin nhân viên trong hệ thống. Cung cấp các phương thức để thêm, cập nhật, và xóa thông tin nhân viên.

- *Nhân Viên:*
    Lớp đại diện cho thông tin chi tiết của nhân viên trong hệ thống. Dùng để lưu trữ thông tin chi tiết của nhân viên. Cung cấp các phương thức để tạo, cập nhật, và xóa thông tin nhân viên.

- *Hệ Thống Quản Nhân Viên:*
     Lớp điều phối chính của hệ thống, chịu trách nhiệm xử lý tất cả các yêu cầu liên quan đến thông tin nhân viên. Dùng để cung cấp các phương thức để thêm, cập nhật, xóa và tìm kiếm thông tin nhân viên. Đảm bảo rằng các thao tác trên thông tin nhân viên được thực hiện một cách chính xác và phù hợp với quyền hạn của quản trị viên.

**Thuộc tính và quan hệ giữa các lớp**

- Lớp *QuảnTrịViênLương* kế thừa từ *NgườiDùng*.

- *QuảnTrịViênLương* tương tác với *HệThốngQuảnLýNhânViên* để thực hiện các thao tác quản lý thông tin nhân viên.

- *HệThốngQuảnLýNhânViên* tương tác với *NhânViên* để thực hiện các thao tác tạo, cập nhật, và xóa thông tin nhân viên.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/j5JDIkj05DxdASwoWds1SX6b5ooq5CGWRaFLp60okRQJegWh5t9nOt5r4S5QHAmAmXNaDeYBANsFUG9VmJEJQ3ADiQlRHQ7pdNE-dvwPj-XriSETDWzzpsfvJgS3JNVoAACB-bFyOoxiMw0-N0pP-7HynDmcaQE7NnLOvMtAt1ZryOZN4RWDJM3SIrjASnNe1dJ3EhGIffLGZWRCRileP8qYGMFoEEcddBuOJ5TKW3AUA29Yw3U9k68Q-PokmPOYrBIyg6HN_7M-m3x5fLX6JtgOLQ9_PcrxWHprQROuHg6qJ37QUKYSpaCjS838w8ovSn-9eLUdYcU_pPaT6VMMs2fbP5qCQZBwGqry6zrUXoggEvjWRAzLzNsBt5jUuF1SKPs8Vii05SFu50KUCvje1oO3bz5p0r7j8Uc4Kei4m9HJwEgmEDaCm5KbYIClzbhOaE3G5PT0fkFuuCISQlgyS4okLMaufpNqmHB5-8z1oSVekFPgj6yJyOGYE8uu0azS-l626KuupWh-uygXmsCR1VIO6oz-Gxpart1F3CEg7Ds4jfPiKrR4Dtr5TdAtgU06ufIqxJjx-IlndU4PrLpS-tMAc-lFwic8m_3C1-l7GRbSvCigUd7AvOLPwLU09yKSBuurereDD9hZx76pNgp5JRQ1p-qx0000__y30000)

**Giải thích các lớp và quan hệ**

- *NgườiDùng* 

    **Mô tả**

    Lớp này đại diện cho người dùng trong hệ thống, cung cấp thông tin cần thiết để thực hiện đăng nhập.

    **Thuộc tính** 

    - tênĐăngNhập: Chuỗi chứa tên đăng nhập của người dùng.

    - mậtKhẩu: Chuỗi chứa mật khẩu của người dùng.

    **Phương thức**

    - đăngNhập(): Phương thức cho phép người dùng đăng nhập vào hệ thống.

- *QuảnTrịViênLương* 

    **Kế thừa**

    Kế thừa từ lớp NgườiDùng, đại diện cho quản trị viên có quyền quản lý thông tin nhân viên.

    **Mô tả**
    
    Lớp này chứa các phương thức và thuộc tính liên quan đến quản trị viên lương.

    **Thuộc tính**

    - mãQuảnTrịViên: Định danh duy nhất cho quản trị viên.

    **Phương thức**

    - thêmNhânViên(): Thực hiện việc thêm một nhân viên mới vào hệ thống.

    - cậpNhậtNhânViên(): Cập nhật thông tin của nhân viên hiện có.

    - xóaNhânViên(): Xóa thông tin nhân viên khỏi hệ thống.

- *NhânViên* 

    **Mô tả**

    Lớp này đại diện cho thông tin chi tiết của nhân viên trong hệ thống, chứa các thuộc tính và phương thức liên quan đến nhân viên.

    **Thuộc tính**

    - mãNhânViên: Định danh duy nhất cho nhân viên.

    - tên: Tên của nhân viên.

    - loạiNhânViên: Loại nhân viên (Giờ, Lương, Hoa hồng).

    - địaChỉ: Địa chỉ của nhân viên.

    - sốAnSinhXãHội: Số an sinh xã hội của nhân viên.

    - khấuTrừThuếChuẩn, khấuTrừKhác: Các khoản khấu trừ liên quan đến thuế hoặc lợi ích khác.

    - sốĐiệnThoại: Số điện thoại của nhân viên.

    - tỷLệGiờ, lương, tỷLệHoaHồng, giớiHạnGiờ: Các thông tin tài chính khác liên quan đến nhân viên.

    **Phương thức**

    - tạoNhânViên(): Tạo mới một bản ghi nhân viên.

    - cậpNhậtNhânViên(): Cập nhật thông tin cho một nhân viên.

    - xóaNhânViên(): Xóa thông tin của nhân viên khỏi hệ thống.

- *HệThốngQuảnLýNhânViên* 

    **Mô tả**

    Lớp này là lớp điều phối chính trong hệ thống, xử lý các yêu cầu liên quan đến thông tin nhân viên.

    **Phương thức**

    - yêuCầuThôngTinNhânViên(): Yêu cầu quản trị viên cung cấp thông tin để thao tác với nhân viên.

    - thêmNhânViên(quảnTrịViên: QuảnTrịViênLương): Thêm một nhân viên mới vào hệ thống.

    - cậpNhậtNhânViên(mãNhânViên: int): Cập nhật thông tin cho nhân viên dựa trên mã nhân viên.

    - xóaNhânViên(mãNhânViên: int): Xóa một nhân viên dựa trên mã.

    - tìmKiếmNhânViên(mãNhânViên: int): Tìm kiếm thông tin của nhân viên dựa trên mã nhân viên.

**Quan hệ giữa các lớp**

- **Kế thừa:** Lớp *QuảnTrịViênLương* kế thừa từ lớp *NgườiDùng*, có nghĩa là tất cả các thuộc tính và phương thức của *NgườiDùng* đều có sẵn cho *QuảnTrịViênLương*.

- **Tương tác:** 
    *QuảnTrịViênLương* tương tác với *HệThốngQuảnLýNhânViên* để thực hiện các thao tác quản lý thông tin nhân viên.

    *HệThốngQuảnLýNhânViên* tương tác với *NhânViên* để thực hiện các thao tác tạo, cập nhật, và xóa thông tin nhân viên.

### 6. Phân tích Ca Sử Dụng "Run Payroll".

**Xác định các lớp phân tích**

- NhânViên

- BảngLương 

- HệThốngNgânHàng

- GiaoDịch

**Sequence Diagram (Biểu đồ trình tự)**

![Diagram](https://www.planttext.com/api/plantuml/png/X9CnJiD044NxFSN85HHS80MA8X0fK1GKYtxZMDuLcrcmruLFG455HHk3KWGf4WLLN52ib7lu15o1MJkEdIWIbYpRcZSp_t_RlyLFFp4yDkbSCHuO7SDTMcu-q8_BukLUsazaKvtYZCSPW3TmfUXs-xNDCVA09p3cMQoLwa8ZOT-nQgs8w_cZqbaOia2Z8PQ8OLay-w8iNZ4QHGGFxM8tRi3nOP8b9fop48qqD0-y6ydr5Sa9HCNuCSU4j4gDZ1shXOlBHbCF0b5kykn0zDavsvKFI6FNA7njSpp9DHvsOCiqXSDXCMq4LKECAmFUMDHFOCZsAg0BHm76BGHb5o0H4hiAF4P-uPH0YHEgqyPG9U7_ywAoM4juIZcW2nX4bV3nz4wIf9goqctKjChH7SHrjE-dL-_eD4JxsxgrCZvgryE3iD_LnSKpAujb8yaTxUG3trERQr1byIRtPCT0LuvBOate9g_H46VCdHty-6FfWT2ap5bV6jOdcdw3Fm000F__0m00)

**Mô tả hành vi và nhiệm vụ của từng lớp**

- *Nhân Viên:*
    Lớp này đại diện cho thông tin chi tiết của nhân viên trong hệ thống, bao gồm các thuộc tính liên quan đến lương và thanh toán. Dùng để cung cấp thông tin cần thiết để tính lương. Phương thức tínhLương() tính toán lương cho nhân viên dựa trên số giờ làm việc và các yếu tố khác.

- *Bảng Lương:*
    Lớp này quản lý quy trình chạy bảng lương, bao gồm việc tính toán lương cho tất cả nhân viên.

    Dùng để Thực hiện phương thức chạyBảngLương() để bắt đầu quy trình chạy bảng lương. Sử dụng phương thức tínhToánLương() để thu thập dữ liệu từ tất cả nhân viên và tính toán tổng lương. In séc nếu phương thức thanh toán là qua bưu điện. Tạo giao dịch ngân hàng nếu phương thức thanh toán là gửi qua ngân hàng.

- *Hệ Thống Ngân Hàng:*
    Lớp này quản lý các giao dịch ngân hàng liên quan đến việc thanh toán lương cho nhân viên. Thực hiện phương thức gửiGiaoDịch(giaoDịch) để gửi thông tin giao dịch đến ngân hàng cho việc thanh toán.

- *Giao Dịch:*
     Lớp này đại diện cho một giao dịch ngân hàng liên quan đến việc thanh toán lương. Cung cấp thông tin cần thiết cho giao dịch ngân hàng.

**Thuộc tính và quan hệ giữa các lớp**

- Lớp *BảngLương* tương tác với lớp *NhânViên* để lấy thông tin và tính lương.

- Nếu phương thức thanh toán là gửi qua ngân hàng, *BảngLương* sẽ tạo một đối tượng *GiaoDịch* và tương tác với *HệThốngNgânHàng* để gửi giao dịch.

**Biểu Đồ Lớp (Class Diagram)** 

![Diagram](https://www.planttext.com/api/plantuml/png/T5AnQiCm4Dtz5I9JMd2WguOIIY61XYmnsOtJIgBEgTXAePGEdJfqoWSKueOEQGbqZeOEWlo7lY2_KDcERIbDlLYwftjtxztjv4yt5M4YPjFOY-8mJT6GgdSOC_K9wD53-JTLooQ84GDHnaLn7Oc40IaZCTURZDcF7NJxlSs0O7GJyt3FaMevxp4jtmPgCHsRmqlauBTKRpvcGQBbbnE_eoLPGBLSHG4DWGPSPGSLXLe37PGlsoSLmPEtbtgXDqiWUxnI6vcAsOC3vQdtd4qiqgBOKPZ1IAqYDqQqNBCU2_cbbgyH7H9ZK5yjhDIwfxwn81Sr1z8ygtexu6cJ-eXH4_x3sK3MI7jMRZtIV1o1cS8pE6uBjM1NbEUUr0ORTcjLMcSjvFlcr-cSjWwCnGYCfske5i1pOTy__qSrBWMZN2QQ5BqUoRNKOIJCyBYJqBs6YTdkNm000F__0m00)

**Giải thích các lớp và quan hệ**

- *NhânViên* 

    **Mô tả**

    Lớp này đại diện cho thông tin chi tiết của nhân viên trong hệ thống, bao gồm các thuộc tính liên quan đến lương và thanh toán.

    **Thuộc tính** 

    - mãNhânViên: Định danh duy nhất cho nhân viên.

    - tên: Tên của nhân viên.

    - loạiNhânViên: Loại nhân viên (Giờ, Lương, Hoa hồng).

    - lương: Mức lương của nhân viên.

    - sốGiờLàmViệc: Số giờ làm việc của nhân viên trong kỳ thanh toán.

    - khấuTrừ: Các khoản khấu trừ liên quan đến lương.

    - phươngThứcThanhToán: Phương thức thanh toán (Gửi qua bưu điện, Gửi qua ngân hàng, Nhận trực tiếp).

    **Phương thức**

    - tínhLương(): Tính toán lương cho nhân viên dựa trên số giờ làm việc và các yếu tố khác.

- *BảngLương* 

    **Mô tả**
    
    Lớp này quản lý quy trình chạy bảng lương, bao gồm việc tính toán lương cho tất cả nhân viên.

    **Phương thức**

    - chạyBảngLương(): Bắt đầu quy trình chạy bảng lương.

    - tínhToánLương(): Tính toán tổng lương cho tất cả nhân viên.

    - inSéc(): In séc nếu phương thức thanh toán là qua bưu điện.

    - gửiGiaoDịchNgânHàng(): Tạo và gửi giao dịch ngân hàng nếu phương thức thanh toán là gửi qua ngân hàng.

- *HệThốngNgânHàng* 

    **Mô tả**

    Lớp này quản lý các giao dịch ngân hàng liên quan đến việc thanh toán lương cho nhân viên.

    **Phương thức**

    - gửiGiaoDịch(giaoDịch: GiaoDịch): Gửi thông tin giao dịch đến ngân hàng để thực hiện thanh toán.

- *GiaoDịch* 

    **Mô tả**

    Lớp này đại diện cho một giao dịch ngân hàng liên quan đến việc thanh toán lương.

    **Thuộc tính**

    - mãGiaoDịch: Định danh duy nhất cho giao dịch.

    - sốTiền: Số tiền cần thanh toán cho nhân viên.

    - tàiKhoản: Tài khoản nhận tiền cho giao dịch.

**Quan hệ giữa các lớp**

- **NhânViên và BảngLương** Mỗi nhân viên có thể nhận lương từ bảng lương. Mối quan hệ này thể hiện rằng một bảng lương có thể tính lương cho nhiều nhân viên.

- **BảngLương và HệThốngNgânHàng:** Bảng lương gửi giao dịch đến hệ thống ngân hàng để xử lý thanh toán cho nhân viên.

- **BảngLương và GiaoDịch:** Bảng lương tạo ra giao dịch để gửi đến hệ thống ngân hàng, thể hiện rằng bảng lương quản lý các giao dịch ngân hàng liên quan đến thanh toán lương.

## **Code Java mô phỏng ca sử dụng "Maintain Timecard".**