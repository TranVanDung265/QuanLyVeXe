# Đọc để hiểu cách tổ chức cho đẹp

# HỆ THỐNG QUẢN LÝ ĐẶT VÉ XE KHÁCH

**Đề tài nhóm 03 — Dự án Java cuối kỳ**

## 1. Giới thiệu dự án

Dự án xây dựng chương trình quản lý đặt vé xe khách tuyến **Hà Nội – Hải Phòng**.

Hệ thống hỗ trợ khách hàng tra cứu chuyến xe, xem ghế còn trống, đặt vé và thanh toán. Nhân viên nhà xe có thể xem danh sách vé đã bán trong ngày.

Dự án được phát triển theo mô hình hướng đối tượng, phân chia thành các package riêng biệt để thuận tiện cho việc phát triển, kiểm thử, bảo trì và làm việc nhóm trên GitHub.

### Chức năng chính

- **Quản lý khách hàng:** lưu thông tin khách hàng và phân loại khách thường, khách thành viên, khách VIP.
- **Quản lý chuyến xe:** hiển thị và tìm kiếm chuyến xe theo điểm đi, điểm đến.
- **Quản lý ghế:** xem ghế còn trống, phân biệt ghế thường và ghế VIP.
- **Đặt vé:** kiểm tra chuyến xe, ghế, tính giá vé, sinh mã vé và lưu thông tin đặt vé.
- **Thanh toán:** mô phỏng thanh toán bằng tiền mặt, chuyển khoản và ví điện tử.
- **Tra cứu vé:** xem thông tin vé và danh sách vé đã bán trong ngày.

## 2. Công nghệ sử dụng

| Công nghệ | Mục đích |
|---|---|
| Java JDK 25 | Ngôn ngữ và môi trường chạy chương trình |
| Maven | Quản lý cấu hình, biên dịch và thư viện |
| IntelliJ IDEA | IDE phát triển Java |
| Git | Quản lý phiên bản mã nguồn |
| GitHub | Lưu trữ mã nguồn và phối hợp nhóm |
| File TXT | Lưu dữ liệu cục bộ bằng File I/O |
| Java Collections | Quản lý danh sách đối tượng trong bộ nhớ |

Giao diện ban đầu có thể sử dụng menu console để hoàn thiện nghiệp vụ trước. Nếu nhóm triển khai giao diện desktop, có thể sử dụng Java Swing mà không cần thay đổi toàn bộ cấu trúc service và repository.

**Lưu ý:** Maven là công cụ quản lý và xây dựng dự án, không phải thư viện thiết kế giao diện.

## 3. Yêu cầu môi trường

Trước khi chạy dự án, mỗi thành viên cần chuẩn bị:

- JDK 25.
- IntelliJ IDEA.
- Git.
- Maven được cài đặt riêng hoặc Maven Wrapper nếu nhóm bổ sung vào repository.
- Tài khoản GitHub và quyền truy cập repository của nhóm.

Kiểm tra môi trường bằng Terminal:

```bash
java -version
javac -version
mvn -version
git --version
```

Đảm bảo `java`, `javac` và Maven đang sử dụng JDK 25.

## 4. Cách tải và chạy dự án

### Bước 1: Clone repository

Thay `<URL-repository>` bằng URL GitHub thực tế của nhóm.

```bash
git clone <URL-repository>
cd quan-ly-dat-ve-xe-khach
```

### Bước 2: Mở dự án bằng IntelliJ IDEA

1. Mở IntelliJ IDEA.
2. Chọn **Open** và chọn thư mục dự án có file `pom.xml`.
3. Chờ IntelliJ tải và đồng bộ cấu hình Maven.
4. Vào Project Structure và chọn Project SDK là JDK 25.
5. Kiểm tra Maven đang sử dụng đúng JDK.

### Bước 3: Biên dịch dự án

Tại thư mục gốc, chạy:

```bash
mvn clean compile
```

Nếu biên dịch thành công, Maven sẽ tạo thư mục `target/`.

### Bước 4: Chạy chương trình

Nếu `pom.xml` đã cấu hình `exec-maven-plugin` với lớp chính `vn.edu.team03.main.Main`, chạy:

```bash
mvn exec:java
```

Hoặc mở file:

```text
src/main/java/vn/edu/team03/main/Main.java
```

Sau đó nhấn **Run** trong IntelliJ IDEA.

> Lưu ý: Bộ khung khởi tạo class có thể chưa chạy được cho đến khi các thành viên hoàn thành phần triển khai tương ứng. Không được xem việc biên dịch thành công là bằng chứng rằng tất cả chức năng đã hoàn thiện.

## 5. Cấu trúc thư mục

```text
quan-ly-dat-ve-xe-khach/
├── pom.xml
├── README.md
├── .gitignore
├── data/
│   ├── customers.txt
│   ├── trips.txt
│   ├── tickets.txt
│   └── payments.txt
├── docs/
│   ├── PHAN-CONG.md
│   ├── FILE-SCHEMA.md
│   ├── class-diagram/
│   └── report/
└── src/
    ├── main/
    │   └── java/
    │       └── vn/edu/team03/
    │           ├── main/
    │           ├── model/
    │           ├── service/
    │           ├── repository/
    │           ├── utils/
    │           └── exception/
    └── test/
        └── java/
            └── vn/edu/team03/
```

### Trách nhiệm của từng package

| Package | Trách nhiệm |
|---|---|
| `model` | Các đối tượng dữ liệu như User, Customer, BusTrip, Seat, Ticket, Payment |
| `service` | Xử lý nghiệp vụ khách hàng, chuyến xe, đặt vé, tính giá và thanh toán |
| `repository` | Đọc, ghi, tìm kiếm dữ liệu trong các file TXT |
| `utils` | Các tiện ích dùng chung như sinh mã và kiểm tra dữ liệu nhập |
| `exception` | Các ngoại lệ nghiệp vụ và thông báo lỗi |
| `main` | Khởi tạo chương trình và điều phối giao diện |
| `src/test` | Chứa các bài kiểm thử |

Không viết toàn bộ nghiệp vụ trong `Main.java`. Giao diện chỉ nhận dữ liệu, gọi service và hiển thị kết quả.

## 6. Phân công 6 thành viên

Tỷ lệ đóng góp kế hoạch của mỗi thành viên là **16,67%**, tổng cộng 100%.

| Thành viên | Phạm vi công việc |
|---|---|
| Thành viên 1 | Model dùng chung, lớp User/Staff, FileStorage, IdGenerator và quy ước dữ liệu |
| Thành viên 2 | Quản lý khách hàng, CustomerRepository, PricingService và chính sách giảm giá |
| Thành viên 3 | Quản lý chuyến xe, ghế và TripRepository |
| Thành viên 4 | BookingService, TicketService, TicketRepository và kiểm soát đặt trùng ghế |
| Thành viên 5 | PaymentService, PaymentRepository và các phương thức thanh toán |
| Thành viên 6 | Main, giao diện, tích hợp các service, kiểm thử tích hợp và tài liệu báo cáo |

### Nguyên tắc phối hợp

- Mỗi thành viên chịu trách nhiệm triển khai, kiểm thử và giải thích phần việc của mình.
- Thành viên 1 phối hợp với các thành viên còn lại để thống nhất model, tên thuộc tính và định dạng file.
- Thành viên 2–5 phải thống nhất chữ ký các phương thức public trước khi tích hợp.
- Thành viên 6 phụ trách điều phối tích hợp, nhưng không thay thế trách nhiệm kiểm thử của các thành viên khác.
- Tỷ lệ 16,67% là kế hoạch ban đầu. Báo cáo cuối kỳ phải phản ánh đóng góp thực tế của từng người.

## 7. Quy tắc viết code

### 7.1. Quy tắc hướng đối tượng

Dự án phải áp dụng các nội dung sau:

- **Encapsulation:** thuộc tính thường được khai báo `private`; cung cấp constructor, getter/setter phù hợp.
- **Inheritance:** sử dụng kế thừa khi có quan hệ phù hợp, ví dụ `Customer extends User`.
- **Polymorphism:** xử lý nhiều chính sách giảm giá hoặc phương thức thanh toán qua interface chung.
- **Abstraction:** sử dụng abstract class hoặc interface.
- **Collections:** sử dụng `List`, `Map` hoặc collection phù hợp.
- **Exception Handling:** xử lý lỗi và thông báo rõ nguyên nhân.
- **File I/O:** đọc và ghi dữ liệu bằng Java I/O hoặc NIO.

### 7.2. Quy tắc đặt tên

- Class và interface: `PascalCase`, ví dụ `BookingService`.
- Method và biến: `camelCase`, ví dụ `findAvailableSeats`.
- Hằng số: `UPPER_SNAKE_CASE` khi phù hợp.
- Package: chữ thường, ví dụ `vn.edu.team03.service`.

### 7.3. Quy tắc comment

Mỗi class được phân công nên có comment ghi rõ:

1. Thành viên chịu trách nhiệm.
2. Mục đích của class.
3. Các phần cần triển khai.
4. Những class mà nó phụ thuộc hoặc liên kết.
5. Các quy tắc nghiệp vụ liên quan.

Comment phải được cập nhật khi thiết kế thay đổi. Không giữ comment mô tả chức năng mà code thực tế không còn thực hiện.

### 7.4. Quy tắc phân tầng

- `model` không chứa menu hoặc logic đọc/ghi file.
- `service` không đọc/ghi TXT trực tiếp.
- `repository` không quyết định quy tắc giảm giá hay đặt vé.
- `main` không xử lý toàn bộ nghiệp vụ.
- Giao diện không tự thay đổi trạng thái ghế hoặc trạng thái thanh toán; phải gọi service tương ứng.

## 8. Quy ước lưu dữ liệu TXT

Dữ liệu được lưu cục bộ trong thư mục `data/` ở thư mục gốc dự án.

| File | Nội dung |
|---|---|
| `customers.txt` | Thông tin khách hàng |
| `trips.txt` | Chuyến xe và trạng thái ghế |
| `tickets.txt` | Thông tin vé đã đặt |
| `payments.txt` | Lịch sử thanh toán |

Tên file trên là quy ước đề xuất; nhóm phải thống nhất schema thực tế trong `docs/FILE-SCHEMA.md`.

### Quy tắc bắt buộc

- Sử dụng UTF-8 để hỗ trợ tiếng Việt.
- Không sử dụng đường dẫn tuyệt đối gắn với máy cá nhân.
- Không ghi dữ liệu trực tiếp trong package `model`, `service` hoặc `main`.
- Không dùng `toString()` làm định dạng lưu dữ liệu lâu dài.
- Thống nhất thứ tự trường và cách xử lý dữ liệu có ký tự phân cách.
- Xử lý trường hợp file chưa tồn tại, file rỗng hoặc dữ liệu không hợp lệ.
- Không commit dữ liệu khách hàng thực tế lên GitHub.

Các file dữ liệu runtime có thể được loại trừ khỏi Git bằng `.gitignore`. Nếu cần dữ liệu demo, hãy dùng file mẫu riêng và không đưa dữ liệu cá nhân vào đó.

## 9. Các quy tắc nghiệp vụ bắt buộc

### Đặt vé

1. Chuyến xe phải tồn tại.
2. Ghế phải tồn tại và thuộc chuyến xe đã chọn.
3. Ghế phải còn trống.
4. Không được đặt trùng ghế.
5. Giá vé cuối cùng phải lớn hơn 0.
6. Ghế VIP phải có phụ phí so với ghế thường.
7. Khách thành viên và khách VIP có thể được hưởng ưu đãi theo chính sách đã thống nhất.
8. Khi đặt vé thành công, phải tạo mã vé, cập nhật trạng thái ghế và lưu dữ liệu.

### Thanh toán

1. Vé phải tồn tại trước khi thanh toán.
2. Hỗ trợ mô phỏng tiền mặt, chuyển khoản và ví điện tử.
3. Chỉ cập nhật trạng thái thành `PAID` khi thanh toán thành công.
4. Nếu thanh toán thất bại, vé vẫn `UNPAID`.
5. Thiết kế mặc định của nhóm là giữ ghế đã đặt nếu thanh toán thất bại; phải nêu rõ quyết định này trong báo cáo.

### Tính nhất quán dữ liệu

Đối với đặt vé, cần kiểm tra trạng thái ghế, tạo vé và lưu trạng thái một cách nhất quán. Nếu thao tác ghi file thất bại, không được để chương trình âm thầm tiếp tục với dữ liệu mâu thuẫn.

File TXT không tự cung cấp transaction hoặc cơ chế đồng bộ giữa nhiều máy. Phạm vi đồ án nên thống nhất một ứng dụng chạy đơn tiến trình, trừ khi nhóm chủ động triển khai cơ chế bảo vệ bổ sung.

## 10. Quy trình làm việc với Git và GitHub

### 10.1. Tạo nhánh riêng

Không nên nhiều thành viên cùng sửa trực tiếp trên nhánh `main`.

```bash
git switch main
git pull origin main
git switch -c feature/customer-management
```

Đặt tên nhánh phù hợp với chức năng được giao, ví dụ:

- `feature/customer-management`
- `feature/trip-management`
- `feature/booking`
- `feature/payment`
- `feature/console-ui`
- `test/integration-tests`

### 10.2. Commit code

Trước khi commit:

```bash
git status
mvn clean compile
git diff
```

Sau đó:

```bash
git add .
git commit -m "feat: add customer management"
git push -u origin feature/customer-management
```

Một số tiền tố commit nên thống nhất:

- `feat:` thêm chức năng.
- `fix:` sửa lỗi.
- `refactor:` cải thiện cấu trúc code.
- `test:` thêm hoặc sửa kiểm thử.
- `docs:` cập nhật tài liệu.
- `build:` cập nhật cấu hình Maven.

### 10.3. Pull Request và merge

1. Push nhánh cá nhân lên GitHub.
2. Tạo Pull Request vào `main`.
3. Mô tả chức năng đã làm và các file thay đổi.
4. Nhờ thành viên khác review.
5. Sửa lỗi nếu có.
6. Chỉ merge khi thay đổi đã được kiểm tra.

### 10.4. Đồng bộ code mới

Trước khi bắt đầu công việc mới:

```bash
git switch main
git pull origin main
```

Sau đó chuyển sang nhánh đang làm và cập nhật theo quy trình nhóm đã thống nhất.

### 10.5. Tránh xung đột Git

- Không tự ý đổi tên class, method hoặc thuộc tính dùng chung.
- Báo cho các thành viên khác trước khi thay đổi interface.
- Không commit thư mục `target/`, `.idea/` hoặc dữ liệu runtime không cần thiết.
- Không dùng `git push --force` lên nhánh dùng chung nếu chưa thống nhất.
- Không sửa cùng một file quan trọng ở nhiều nhánh mà không phối hợp.

## 11. Kiểm thử

Tối thiểu cần kiểm thử các tình huống:

| STT | Tình huống | Kết quả mong đợi |
|---|---|---|
| 1 | Đặt ghế còn trống | Đặt vé thành công, ghế chuyển sang đã đặt |
| 2 | Đặt lại ghế đã được đặt | Từ chối đặt vé và thông báo rõ nguyên nhân |
| 3 | Chọn ghế không tồn tại | Từ chối đặt vé |
| 4 | Chọn chuyến xe không tồn tại | Từ chối đặt vé |
| 5 | Khách VIP đặt ghế VIP | Tính đúng phụ phí và ưu đãi |
| 6 | Giá vé cuối cùng nhỏ hơn hoặc bằng 0 | Từ chối tạo vé |
| 7 | Thanh toán vé hợp lệ thành công | Vé chuyển sang `PAID` |
| 8 | Thanh toán vé không tồn tại | Báo lỗi, không tạo thanh toán hợp lệ |
| 9 | Thanh toán thất bại | Vé vẫn `UNPAID`; ghế được xử lý theo quy định nhóm |
| 10 | Khởi động lại chương trình | Dữ liệu đã lưu được đọc lại đúng |

Trước khi bàn giao, chạy:

```bash
mvn clean compile
mvn test
```

Lệnh `mvn test` chỉ chạy các bài kiểm thử đã được cấu hình; nếu nhóm chưa viết test tự động, cần bổ sung chúng trước khi đánh giá kết quả kiểm thử đầy đủ.

## 12. Sản phẩm bàn giao cuối kỳ

Nhóm cần chuẩn bị:

- Source code hoàn chỉnh trên GitHub.
- File README hướng dẫn cài đặt và chạy.
- Class diagram thể hiện các quan hệ kế thừa, interface và phụ thuộc.
- Báo cáo mô tả thiết kế, nghiệp vụ, lưu trữ file và cách xử lý lỗi.
- Bảng phân công và đóng góp thực tế của từng thành viên.
- Slide báo cáo.
- Kết quả kiểm thử với ít nhất ba tình huống.
- Hướng dẫn chạy lại chương trình trên máy khác.

## 13. Nguyên tắc chung của nhóm

1. Thống nhất thiết kế trước khi triển khai.
2. Chia chức năng rõ ràng, hạn chế sửa chéo phần việc.
3. Mỗi thay đổi đều phải có commit dễ hiểu.
4. Kiểm thử trước khi tạo Pull Request.
5. Không đưa thông tin cá nhân hoặc dữ liệu nhạy cảm lên repository.
6. Không merge code chưa biên dịch được vào `main`.
7. Ưu tiên code dễ đọc, dễ bảo trì và đúng yêu cầu đề bài hơn việc viết code quá phức tạp.

**Mục tiêu chung:** Cả 6 thành viên có thể clone repository, cấu hình JDK 25, mở bằng IntelliJ IDEA, biên dịch và chạy dự án theo cùng