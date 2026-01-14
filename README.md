# Kiem_thu_phan_mem
Repository này dùng để lưu trữ bài tập, tài liệu và project của môn Kiểm thử phần mềm.

## Thông tin môn học
- Môn học: Kiểm thử phần mềm
- Giảng viên: Trương Anh Hoàng
- Học kỳ: HK2 2025–2026
- Trường/Khoa: Trường Đại Học CMC - Khoa Công Nghệ Thông Tin

## Cấu trúc repository
- `assignments`: Chứa các bài tập 
- `videos`: Chứa các video minh chứng cho các bài tập
- `README.md`: File dùng để mô tả các bài tập, bài toán, cách chạy chương trình, kết quả test, ...

## Các bài tập
## Bài tập 1 (ex_1): Trải nghiệm kiểm thử giao diện với CantUnsee
  - Mô tả: Kết quả sau khi làm bài tập thực hành với https://cantunsee.space/
  - Tổng điểm: 8130
  - Rank: Master
  - Hình ảnh minh chứng:
    ![Can't_Unsee_Image](assignments/ex_1/cantunsee.png)

## Bài tập 2 (ex_2): Phân tích dữ liệu điểm số học sinh với JUnit

### Mô tả bài toán

Xây dựng hệ thống phân tích điểm số học sinh với hai chức năng chính:

1. **Đếm số học sinh đạt loại Giỏi** (`countExcellentStudents`)
   - Nhận vào: Danh sách điểm số (List<Double>)
   - Điều kiện: Điểm hợp lệ từ 0-10, học sinh Giỏi có điểm >= 8.0
   - Trả về: Số lượng học sinh đạt loại Giỏi

2. **Tính điểm trung bình hợp lệ** (`calculateValidAverage`)
   - Nhận vào: Danh sách điểm số (List<Double>)
   - Điều kiện: Chỉ tính các điểm hợp lệ từ 0-10
   - Trả về: Điểm trung bình của các điểm hợp lệ

### Công nghệ sử dụng

- **Ngôn ngữ**: Java 11
- **Build Tool**: Maven 3.x
- **Testing Framework**: JUnit 5 (Jupiter) version 5.10.1
- **IDE**: IntelliJ IDEA / Eclipse / VS Code

### Cấu trúc dự án

```
assignments/ex_2/
├── pom.xml                          # Maven configuration
├── src/
│   └── StudentAnalyzer.java         # Source code chính
└── test/
    └── StudentAnalyzerTest.java     # Test cases
```

### Cách chạy chương trình

#### 1. Yêu cầu hệ thống
- Java JDK 11 trở lên
- Maven 3.6 trở lên

#### 2. Chạy test
```bash
# Di chuyển vào thư mục dự án
cd assignments/ex_2

# Chạy tất cả test cases
mvn test

# Hoặc clean và chạy test
mvn clean test
```
#### 3. Compile code
```bash
# Compile source code
mvn compile

# Compile cả source và test
mvn test-compile
```
### Kết quả Test

```
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running StudentAnalyzerTest
[INFO] Tests run: 23, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] Results:
[INFO] Tests run: 23, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] BUILD SUCCESS
```
## Bài tập 3 (ex_3): Kiểm thử tự động End-to-End với Cypress

### Mục tiêu
- Hiểu và thực hành các kịch bản kiểm thử tự động end-to-end phổ biến bằng cách sử dụng Cypress để kiểm tra một trang web mẫu.

### Công nghệ sử dụng
- **Ngôn ngữ**: JavaScript
- **Framework**: Cypress
- **IDE**: Visual Studio Code
- **Trang web**: https://www.saucedemo.com/ (trang web bán hàng giả)

### Cấu trúc dự án
```
assignments/ex_3/
├── cypress-exercise/                # Dự án Cypress
│   ├── cypress/                     # Chứa các file test
│   │   ├── fixtures/                # Chứa các file dữ liệu
│   │   ├── integration/             # Chứa các file test
│   │   ├── plugins/                 # Chứa các file plugin

```
### Kịch bản kiểm thử

#### **Kịch bản 1: Kiểm tra đăng nhập thành công** 

**Mục tiêu:** Kiểm tra xem người dùng có thể đăng nhập thành công với thông tin hợp lệ.

**Các bước thực hiện:**
1. Truy cập trang https://www.saucedemo.com
2. Nhập tên người dùng: `standard_user`
3. Nhập mật khẩu: `secret_sauce`
4. Nhấn nút **"Login"**
5. **Xác minh:** Trang được chuyển hướng đến trang danh sách sản phẩm (URL chứa `/inventory.html`)

---

#### **Kịch bản 2: Kiểm tra đăng nhập thất bại** 

**Mục tiêu:** Kiểm tra xem hệ thống hiển thị thông báo lỗi khi đăng nhập với thông tin không hợp lệ.

**Các bước thực hiện:**
1. Truy cập trang https://www.saucedemo.com
2. Nhập tên người dùng: `invalid_user`
3. Nhập mật khẩu: `wrong_password`
4. Nhấn nút **"Login"**
5. **Xác minh:** Thông báo lỗi được hiển thị với nội dung: *"Username and password do not match"*

---

#### **Kịch bản 3: Kiểm tra chức năng thêm sản phẩm vào giỏ hàng** 

**Mục tiêu:** Kiểm tra xem người dùng có thể thêm một sản phẩm vào giỏ hàng sau khi đăng nhập.

**Các bước thực hiện:**
1. Đăng nhập với thông tin hợp lệ (`standard_user` / `secret_sauce`)
2. Nhấn nút **"Add to cart"** của sản phẩm đầu tiên trong danh sách
3. **Xác minh:** Số lượng sản phẩm trong giỏ hàng hiển thị là **1**

---

#### **Kịch bản 4: Kiểm tra chức năng lọc sản phẩm** 

**Mục tiêu:** Kiểm tra xem bộ lọc sản phẩm hoạt động đúng khi chọn "Price (low to high)".

**Các bước thực hiện:**
1. Đăng nhập với thông tin hợp lệ
2. Chọn bộ lọc **"Price (low to high)"** từ dropdown
3. **Xác minh:** Sản phẩm đầu tiên trong danh sách có giá thấp nhất

---

