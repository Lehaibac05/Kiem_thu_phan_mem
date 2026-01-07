# Kiem_thu_phan_mem
Repository này dùng để lưu trữ bài tập, tài liệu và project của môn Kiểm thử phần mềm.

## Thông tin môn học
- Môn học: Kiểm thử phần mềm
- Giảng viên: Trương Anh Hoàng
- Học kỳ: HK2 2025–2026
- Trường/Khoa: Trường Đại Học CMC - Khoa Công Nghệ Thông Tin

## Cấu trúc repository
- `assignments`: Chứa các bài tập 
- `README.md`: File dùng để mô tả các bài tập, bài toán, cách chạy chương trình, kết quả test, ...

## Các bài tập
## Bài tập 1 (ex_1):
    - Mô tả: Kết quả sau khi làm bài tập thực hành với https://cantunsee.space/
    - Tổng điểm: 8130
    - Rank: Master

## Bài tập 2 (ex_2): Student Analyzer

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

**Yêu cầu xử lý:**
- Bỏ qua các điểm không hợp lệ (< 0 hoặc > 10)
- Bỏ qua các giá trị null
- Xử lý danh sách rỗng hoặc null
- Tránh lỗi chia cho 0

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
###  Mô tả một số Test Cases

Dự án bao gồm **23 test cases** được chia thành 3 nhóm chính: **Normal Cases** (trường hợp bình thường), **Boundary Cases** (trường hợp biên), và **Exception Cases** (trường hợp ngoại lệ).

#### **A. Test cho `countExcellentStudents()` - 11 test cases**

##### 1. **Trường hợp bình thường** (Normal Cases)
- `testCountExcellentStudents_MixedValidAndInvalid`
  - Input: `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - Expected: `2` (chỉ đếm 9.0 và 8.5)
  - Mục đích: Kiểm tra xử lý hỗn hợp điểm hợp lệ và không hợp lệ

##### 2. **Trường hợp biên** (Boundary Cases)
- `testCountExcellentStudents_EmptyList`
  - Input: `[]` (danh sách trống)
  - Expected: `0`
  - Mục đích: Xử lý danh sách rỗng

- `testCountExcellentStudents_ExactlyEight`
  - Input: `[8.0, 7.9, 8.1]`
  - Expected: `2` (8.0 và 8.1 là giỏi, 7.9 không phải)
  - Mục đích: Kiểm tra ngưỡng điểm giỏi chính xác tại 8.0

##### 3. **Trường hợp ngoại lệ** (Exception Cases)
- `testCountExcellentStudents_WithNullValues`
  - Input: `[9.0, null, 8.5, null]`
  - Expected: `2`
  - Mục đích: Bỏ qua giá trị null trong danh sách

- `testCountExcellentStudents_AllInvalid`
  - Input: `[-1.0, 11.0, -5.0, 20.0]`
  - Expected: `0`
  - Mục đích: Tất cả điểm không hợp lệ

#### **B. Test cho `calculateValidAverage()` - 12 test cases**

##### 1. **Trường hợp bình thường** (Normal Cases)
- `testCalculateValidAverage_MixedValidAndInvalid`
  - Input: `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - Expected: `8.17` (trung bình của 9.0, 8.5, 7.0)
  - Mục đích: Tính trung bình chỉ với điểm hợp lệ

##### 2. **Trường hợp biên** (Boundary Cases)
- `testCalculateValidAverage_NullList`
  - Input: `null`
  - Expected: `0.0`
  - Mục đích: Xử lý danh sách null

- `testCalculateValidAverage_BoundaryValues`
  - Input: `[0.0, 10.0]`
  - Expected: `5.0`
  - Mục đích: Kiểm tra cả hai giá trị biên (0 và 10)

##### 3. **Trường hợp ngoại lệ** (Exception Cases)
- `testCalculateValidAverage_AllInvalid`
  - Input: `[-1.0, 11.0, -5.0, 20.0]`
  - Expected: `0.0`
  - Mục đích: Không có điểm hợp lệ nào, tránh chia cho 0

- `testCalculateValidAverage_WithNullValues`
  - Input: `[10.0, null, 8.0, null]`
  - Expected: `9.0`
  - Mục đích: Bỏ qua null values khi tính trung bình

**Lưu ý:** Đây chỉ là một số test cases tiêu biểu. Xem file `StudentAnalyzerTest.java` để biết đầy đủ 23 test cases.

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

