Hệ thống quản lý đặt vé xe khách
1. Giới thiệu
   Đây là dự án Java mô phỏng hệ thống quản lý đặt vé xe khách tuyến Hà Nội – Hải Phòng. Hệ thống hỗ trợ quản lý khách hàng, chuyến xe, ghế ngồi, đặt vé và thanh toán; đồng thời cho phép nhân viên xem danh sách vé đã bán trong ngày.

Dự án được xây dựng nhằm vận dụng các kiến thức lập trình hướng đối tượng và tổ chức chương trình theo package rõ ràng.

2. Chức năng chính
   Quản lý khách hàng
- Lưu thông tin khách hàng: mã khách hàng, họ tên, số điện thoại, email và loại khách hàng.
- Hỗ trợ ba loại khách hàng: khách thường, khách thành viên và khách VIP.
- Áp dụng chính sách giá/ưu đãi tương ứng với loại khách hàng theo thiết kế của chương trình.
  Quản lý chuyến xe
- Hiển thị danh sách chuyến xe.
- Tìm chuyến theo điểm đi và điểm đến.
- Quản lý thông tin chuyến xe: mã chuyến, điểm đi, điểm đến, thời gian khởi hành, biển số xe, tổng số ghế và danh sách ghế.
- Xem các ghế còn trống của chuyến xe.
  Quản lý ghế
- Theo dõi mã ghế, số ghế, loại ghế và trạng thái ghế.
- Hỗ trợ ghế thường và ghế VIP.
- Theo dõi trạng thái ghế: còn trống hoặc đã đặt.
- Tính phụ phí cho ghế VIP theo quy tắc giá của chương trình.
  Đặt vé
- Kiểm tra chuyến xe và ghế được chọn có tồn tại hay không.
- Kiểm tra ghế còn trống trước khi đặt.
- Tính giá vé cuối cùng theo loại ghế và chính sách ưu đãi.
- Sinh mã vé, lưu thông tin vé và cập nhật trạng thái ghế sau khi đặt thành công.
  Thanh toán
- Hỗ trợ các hình thức: tiền mặt, chuyển khoản và ví điện tử.
- Cập nhật trạng thái vé thành Đã thanh toán khi thanh toán thành công.
- Khi thanh toán thất bại, vé giữ trạng thái Chưa thanh toán. Cách giữ hoặc hủy ghế cần tuân theo thiết kế thực tế của nhóm.
  Quản lý vé đã bán
- Hỗ trợ nhân viên xem danh sách vé đã bán trong ngày.

3. Công nghệ và kiến thức áp dụng
- Java – ngôn ngữ lập trình.
- Lập trình hướng đối tượng (OOP):
    - Encapsulation (đóng gói).
    - Inheritance (kế thừa).
    - Polymorphism (đa hình).
    - Abstraction (trừu tượng).
- Interface hoặc abstract class.
- Java Collections để quản lý tập hợp dữ liệu.
- Exception Handling để xử lý lỗi và thông báo nguyên nhân.
- File I/O để đọc/ghi dữ liệu.

4. Cấu trúc dự án


5. Quy tắc nghiệp vụ
   Hệ thống cần bảo đảm các quy tắc sau:
- Không cho phép đặt ghế đã được đặt.
- Không cho phép đặt ghế không tồn tại trong chuyến xe.
- Không cho phép đặt vé cho chuyến xe không tồn tại.
- Không chấp nhận giá vé nhỏ hơn hoặc bằng 0.
- Ghế VIP có phụ phí so với ghế thường.
- Khách thành viên hoặc khách VIP có thể được giảm giá theo chính sách được cài đặt.
- Không cho phép thanh toán vé không tồn tại.
- Thông báo rõ nguyên nhân khi phát sinh lỗi nghiệp vụ.

6. Cài đặt và chạy chương trình
   
7. Kiểm thử
   
8. Yêu cầu chất lượng mã nguồn
- Không đặt toàn bộ logic trong hàm main.
- Các thuộc tính của lớp được khai báo private.
- Sử dụng constructor phù hợp và cung cấp getter/setter khi cần.
- Có chú thích cho những phần logic quan trọng.
- Xử lý ngoại lệ và đưa ra thông báo lỗi nghiệp vụ rõ ràng.
- Tổ chức mã nguồn thành các package có trách nhiệm riêng biệt.
9. Tài liệu bàn giao
- Source code.
- Slide báo cáo.
- Sơ đồ class diagram.
- Bảng phân công công việc của từng thành viên.
- Mô tả ít nhất 3 tình huống kiểm thử.

10. Nhóm thực hiện
- Tên nhóm: Nhóm 03
- Thành viên:
- Môn học/lớp: