# Kiem_thu_phan_mem
Repository này dùng để lưu trữ bài tập, tài liệu và project của môn Kiểm thử phần mềm.

## Thông tin môn học
- Môn học: Kiểm thử phần mềm
- Giảng viên: Trương Anh Hoàng
- Học kỳ: Học kỳ
- Trường/Khoa: Trường Đại Học CMC - Khoa Công Nghệ Thông Tin

## Cấu trúc repository
- `assignments`: Chứa các bài tập 
- `videos`: Chứa các video minh chứng cho các bài tập
- `README.md`: File dùng để mô tả các bài tập, bài toán, cách chạy chương trình, kết quả test, ...

## Các bài tập

---

## Bài tập 1 (ex_1): Trải nghiệm kiểm thử giao diện với CantUnsee

### Mô tả
Thực hành kiểm thử giao diện người dùng (UI Testing) thông qua các bài tập trực quan tại https://cantunsee.space/

### Kết quả đạt được
- **Tổng điểm:** 8130
- **Xếp hạng:** Master

### Bài học rút ra
Qua bài tập này, tôi đã rèn luyện khả năng:
- **Spacing (Khoảng cách):** Nhận biết sự khác biệt nhỏ trong khoảng cách giữa các phần tử UI
- **Alignment (Căn chỉnh):** Phát hiện các lỗi căn chỉnh không đồng nhất
- **Typography (Kiểu chữ):** Phân biệt font-size, font-weight, line-height
- **Color (Màu sắc):** Nhận diện sự khác biệt tinh tế về màu sắc và độ tương phản

### Hình ảnh minh chứng
<img width="1920" height="1080" alt="Screenshot (201)" src="https://github.com/user-attachments/assets/951e74a4-68b1-469f-9934-abf6825be4ff" />

---


## Bài tập 2 (ex_2): Phân tích dữ liệu điểm số học sinh với JUnit

###  Mô tả bài toán

Xây dựng hệ thống phân tích điểm số học sinh với hai chức năng chính:

1. **Đếm số học sinh đạt loại Giỏi** (`countExcellentStudents`)
   - **Đầu vào:** Danh sách điểm số (List<Double>)
   - **Điều kiện:** Điểm hợp lệ từ 0-10, học sinh Giỏi có điểm >= 8.0
   - **Đầu ra:** Số lượng học sinh đạt loại Giỏi

2. **Tính điểm trung bình hợp lệ** (`calculateValidAverage`)
   - **Đầu vào:** Danh sách điểm số (List<Double>)
   - **Điều kiện:** Chỉ tính các điểm hợp lệ từ 0-10
   - **Đầu ra:** Điểm trung bình của các điểm hợp lệ

### Công nghệ sử dụng

- **Ngôn ngữ:** Java 11
- **Công cụ build:** Maven 3.x
- **Framework kiểm thử:** JUnit 5 (Jupiter) phiên bản 5.10.1
- **IDE:** IntelliJ IDEA / Eclipse / VS Code

### Cấu trúc dự án

```
assignments/ex_2/
├── pom.xml                          # Cấu hình Maven
├── src/
│   └── StudentAnalyzer.java         # Mã nguồn chính
└── test/
    └── StudentAnalyzerTest.java     # Các test case
```
### Hướng dẫn cài đặt và chạy

#### Bước 1: Kiểm tra yêu cầu hệ thống
Đảm bảo đã cài đặt:
- **Java JDK 11** trở lên
- **Maven 3.6** trở lên

#### Bước 2: Clone repository
```bash
git clone <repository-url>
cd Kiem_thu_phan_mem
```

#### Bước 3: Di chuyển vào thư mục dự án
```bash
cd assignments/ex_2
```

#### Bước 4: Chạy test
```bash
# Cách 1: Chạy test trực tiếp
mvn test

# Cách 2: Clean và chạy test (khuyến nghị)
mvn clean test

# Cách 3: Chạy một test cụ thể
mvn test -Dtest=StudentAnalyzerTest#testCountExcellentStudents_MixedValidAndInvalid
```

### Kết quả kiểm thử

```
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running StudentAnalyzerTest
[INFO] Tests run: 31, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] Results:
[INFO] Tests run: 31, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] BUILD SUCCESS
```

**Tổng kết:**
-  **Tổng số test:** 31 (23 test cơ bản + 8 test BVA nâng cao)
-  **Thành công:** 31
-  **Thất bại:** 0
-  **Lỗi:** 0
-  **Bỏ qua:** 0
-  **Tỷ lệ thành công:** 100%

### Mô tả một số Test Cases tiêu biểu

Dự án bao gồm **31 test cases** được chia thành 4 nhóm chính:
- **Normal Cases** (Trường hợp bình thường)
- **Boundary Cases** (Trường hợp biên)
- **Exception Cases** (Trường hợp ngoại lệ)
- **BVA Advanced** (Boundary Value Analysis nâng cao - 8 test cases mới)

#### **A. Test cho `countExcellentStudents()` - 15 test cases (11 cơ bản + 4 BVA nâng cao)**

##### 1. Trường hợp bình thường (Normal Cases)
  - `testCountExcellentStudents_MixedValidAndInvalid`
  - **Đầu vào:** `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - **Kết quả mong đợi:** `2` (chỉ đếm 9.0 và 8.5)
  - **Mục đích:** Kiểm tra xử lý hỗn hợp điểm hợp lệ và không hợp lệ

##### 2. Trường hợp biên (Boundary Cases)
  - `testCountExcellentStudents_EmptyList`
  - **Đầu vào:** `[]` (danh sách trống)
  - **Kết quả mong đợi:** `0`
  - **Mục đích:** Xử lý danh sách rỗng

  - `testCountExcellentStudents_ExactlyEight`
  - **Đầu vào:** `[8.0, 7.9, 8.1]`
  - **Kết quả mong đợi:** `2` (8.0 và 8.1 là giỏi, 7.9 không phải)
  - **Mục đích:** Kiểm tra ngưỡng điểm giỏi chính xác tại 8.0

##### 3. Trường hợp ngoại lệ (Exception Cases)
  - `testCountExcellentStudents_WithNullValues`
  - **Đầu vào:** `[9.0, null, 8.5, null]`
  - **Kết quả mong đợi:** `2`
  - **Mục đích:** Bỏ qua giá trị null trong danh sách

  - `testCountExcellentStudents_AllInvalid`
  - **Đầu vào:** `[-1.0, 11.0, -5.0, 20.0]`
  - **Kết quả mong đợi:** `0`
  - **Mục đích:** Tất cả điểm không hợp lệ

#### **B. Test cho `calculateValidAverage()` - 16 test cases (12 cơ bản + 4 BVA nâng cao)**

##### 1. Trường hợp bình thường (Normal Cases)
  - `testCalculateValidAverage_MixedValidAndInvalid`
  - **Đầu vào:** `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - **Kết quả mong đợi:** `8.17` (trung bình của 9.0, 8.5, 7.0)
  - **Mục đích:** Tính trung bình chỉ với điểm hợp lệ

##### 2. Trường hợp biên (Boundary Cases)
  - `testCalculateValidAverage_NullList`
  - **Đầu vào:** `null`
  - **Kết quả mong đợi:** `0.0`
  - **Mục đích:** Xử lý danh sách null

  - `testCalculateValidAverage_BoundaryValues`
  - **Đầu vào:** `[0.0, 10.0]`
  - **Kết quả mong đợi:** `5.0`
  - **Mục đích:** Kiểm tra cả hai giá trị biên (0 và 10)

##### 3. Trường hợp ngoại lệ (Exception Cases)
  - `testCalculateValidAverage_AllInvalid`
  - **Đầu vào:** `[-1.0, 11.0, -5.0, 20.0]`
  - **Kết quả mong đợi:** `0.0`
  - **Mục đích:** Không có điểm hợp lệ nào, tránh chia cho 0

  - `testCalculateValidAverage_WithNullValues`
  - **Đầu vào:** `[10.0, null, 8.0, null]`
  - **Kết quả mong đợi:** `9.0`
  - **Mục đích:** Bỏ qua null values khi tính trung bình

#### **C. Test BVA Nâng Cao - 8 test cases mới** 

Để đạt mức **Boundary Value Analysis nâng cao**, đã bổ sung thêm các test với **giá trị sát biên** (near-boundary values):

##### 1. Giá trị sát biên cho ngưỡng giỏi (8.0)
  - `testCountExcellentStudents_NearBoundary_7_99`
  - **Đầu vào:** `[7.99, 8.0, 8.01]`
  - **Kết quả mong đợi:** `2` (7.99 không giỏi, 8.0 và 8.01 là giỏi)
  - **Mục đích:** Kiểm tra so sánh số thực tại ngưỡng 8.0

##### 2. Giá trị sát biên cho điểm hợp lệ (0 và 10)
  - `testCountExcellentStudents_NearBoundary_Zero`
  - **Đầu vào:** `[-0.01, 0.0, 0.01, 8.5]`
  - **Kết quả mong đợi:** `1` (chỉ 8.5 là giỏi)

  - `testCountExcellentStudents_NearBoundary_Ten`
  - **Đầu vào:** `[9.99, 10.0, 10.01]`
  - **Kết quả mong đợi:** `2` (10.01 không hợp lệ)

##### 3. Độ chính xác số thực
  - `testCalculateValidAverage_FloatingPointPrecision`
  - **Đầu vào:** `[7.999999, 8.000000, 8.000001]`
  - **Kết quả mong đợi:** `8.0` (với delta = 0.000001)
  - **Mục đích:** Kiểm tra độ chính xác cao của số thực


---
## Bài tập 3 (ex_3): Kiểm thử tự động End-to-End với Cypress

### Mục tiêu
Hiểu và thực hành các kịch bản kiểm thử tự động end-to-end (E2E) phổ biến bằng cách sử dụng Cypress để kiểm tra một trang web mẫu.

### Công nghệ sử dụng
- **Ngôn ngữ:** JavaScript
- **Framework kiểm thử:** Cypress 15.8.2
- **Môi trường chạy:** Node.js
- **IDE:** Visual Studio Code
- **Trang web kiểm thử:** https://www.saucedemo.com/ (trang web bán hàng demo)

### Cấu trúc dự án
```
assignments/ex_3/
└── cypress-exercise/                # Thư mục dự án Cypress
    ├── package.json                 # Cấu hình Node.js và dependencies
    ├── package-lock.json            # Lock file cho dependencies
    ├── cypress.config.js            # Cấu hình Cypress
    ├── node_modules/                # Thư viện đã cài đặt
    └── cypress/                     # Thư mục chứa test
        ├── fixtures/                # Dữ liệu test (JSON, CSV, ...)
        ├── e2e/                     # Các file test E2E
        ├── support/                 # Commands và helpers tùy chỉnh
        └── videos/                  # Video ghi lại quá trình test (tự động tạo)
```

### Hướng dẫn cài đặt và chạy

#### Bước 1: Kiểm tra yêu cầu hệ thống
Đảm bảo đã cài đặt:
- **Node.js** phiên bản 18.x trở lên
- **npm** phiên bản 8.x trở lên

#### Bước 2: Clone repository
```bash
git clone <repository-url>
cd Kiem_thu_phan_mem
```

#### Bước 3: Di chuyển vào thư mục dự án
```bash
cd assignments/ex_3/cypress-exercise
```

#### Bước 4: Cài đặt dependencies
```bash
# Cài đặt tất cả dependencies (bao gồm Cypress)
npm install

# Hoặc cài đặt Cypress riêng lẻ
npm install cypress --save-dev
```

#### Bước 5: Chạy Cypress

**Cách 1: Mở Cypress Test Runner (GUI Mode - Khuyến nghị cho người mới)**
```bash
npx cypress open
```
Sau đó:
1. Chọn **E2E Testing**
2. Chọn trình duyệt (Chrome, Firefox, Edge, ...)
3. Click vào file test để chạy

**Cách 2: Chạy test ở chế độ Headless (CLI Mode)**
```bash
# Chạy tất cả test
npx cypress run

# Chạy test trên trình duyệt cụ thể
npx cypress run --browser chrome

# Chạy một file test cụ thể
npx cypress run --spec "cypress/e2e/login.cy.js"
```

**Cách 3: Sử dụng npm scripts (sau khi cấu hình trong package.json)**
```bash
# Thêm vào package.json:
# "scripts": {
#   "cy:open": "cypress open",
#   "cy:run": "cypress run"
# }

npm run cy:open   # Mở GUI
npm run cy:run    # Chạy headless
```

### Kịch bản kiểm thử

#### **Kịch bản 1: Kiểm tra đăng nhập thành công** 

**Mục tiêu:** Kiểm tra người dùng có thể đăng nhập thành công với thông tin hợp lệ.

**Các bước thực hiện:**
1. Truy cập trang https://www.saucedemo.com
2. Nhập tên người dùng: `standard_user`
3. Nhập mật khẩu: `secret_sauce`
4. Nhấn nút **"Login"**
5. **Xác minh:** Trang được chuyển hướng đến `/inventory.html`

---

#### **Kịch bản 2: Kiểm tra đăng nhập thất bại** 

**Mục tiêu:** Kiểm tra hệ thống hiển thị thông báo lỗi khi đăng nhập với thông tin không hợp lệ.

**Các bước thực hiện:**
1. Truy cập trang https://www.saucedemo.com
2. Nhập tên người dùng: `invalid_user`
3. Nhập mật khẩu: `wrong_password`
4. Nhấn nút **"Login"**
5. **Xác minh:** Thông báo lỗi hiển thị: *"Username and password do not match"*

---

#### **Kịch bản 3: Kiểm tra chức năng thêm sản phẩm vào giỏ hàng** 

**Mục tiêu:** Kiểm tra người dùng có thể thêm sản phẩm vào giỏ hàng sau khi đăng nhập.

**Các bước thực hiện:**
1. Đăng nhập với thông tin hợp lệ (`standard_user` / `secret_sauce`)
2. Nhấn nút **"Add to cart"** của sản phẩm đầu tiên
3. **Xác minh:** Badge giỏ hàng hiển thị số **1**

---

#### **Kịch bản 4: Kiểm tra chức năng lọc sản phẩm** 

**Mục tiêu:** Kiểm tra bộ lọc sản phẩm hoạt động đúng khi chọn "Price (low to high)".

**Các bước thực hiện:**
1. Đăng nhập với thông tin hợp lệ
2. Chọn bộ lọc **"Price (low to high)"** từ dropdown
3. **Xác minh:** Sản phẩm đầu tiên có giá thấp nhất

---

### Tổng kết
- **Tổng số kịch bản:** 4
- **Loại kiểm thử:** End-to-End (E2E) Testing
- **Phạm vi:** Đăng nhập, Giỏ hàng, Lọc sản phẩm
- **Công cụ:** Cypress 15.8.2

---