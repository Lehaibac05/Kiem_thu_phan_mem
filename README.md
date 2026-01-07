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

### 🧪 Mô tả Test Cases

Dự án bao gồm **23 test cases** được chia thành 3 nhóm chính:

#### **A. Test cho `countExcellentStudents()` - 11 test cases**

##### 1. **Trường hợp bình thường** (Normal Cases)
- `testCountExcellentStudents_MixedValidAndInvalid`
  - Input: `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - Expected: `2` (chỉ đếm 9.0 và 8.5)
  - Mục đích: Kiểm tra xử lý hỗn hợp điểm hợp lệ và không hợp lệ

- `testCountExcellentStudents_AllValid`
  - Input: `[9.5, 8.0, 7.5, 8.5, 6.0]`
  - Expected: `3` (đếm 9.5, 8.0, 8.5)
  - Mục đích: Kiểm tra với tất cả điểm hợp lệ

##### 2. **Trường hợp biên** (Boundary Cases)
- `testCountExcellentStudents_EmptyList`
  - Input: `[]` (danh sách trống)
  - Expected: `0`
  - Mục đích: Xử lý danh sách rỗng

- `testCountExcellentStudents_NullList`
  - Input: `null`
  - Expected: `0`
  - Mục đích: Xử lý danh sách null

- `testCountExcellentStudents_OnlyZeros`
  - Input: `[0.0, 0.0, 0.0]`
  - Expected: `0`
  - Mục đích: Kiểm tra điểm 0 (biên dưới)

- `testCountExcellentStudents_OnlyTens`
  - Input: `[10.0, 10.0, 10.0]`
  - Expected: `3`
  - Mục đích: Kiểm tra điểm 10 (biên trên)

- `testCountExcellentStudents_ExactlyEight`
  - Input: `[8.0, 7.9, 8.1]`
  - Expected: `2` (8.0 và 8.1 là giỏi, 7.9 không phải)
  - Mục đích: Kiểm tra ngưỡng điểm giỏi chính xác

##### 3. **Trường hợp ngoại lệ** (Exception Cases)
- `testCountExcellentStudents_WithNegativeScores`
  - Input: `[-5.0, 8.5, -1.0]`
  - Expected: `2`
  - Mục đích: Bỏ qua điểm âm

- `testCountExcellentStudents_WithScoresAboveTen`
  - Input: `[9.0, 15.0, 8.5, 100.0]`
  - Expected: `2`
  - Mục đích: Bỏ qua điểm > 10

- `testCountExcellentStudents_AllInvalid`
  - Input: `[-1.0, 11.0, -5.0, 20.0]`
  - Expected: `0`
  - Mục đích: Tất cả điểm không hợp lệ

- `testCountExcellentStudents_WithNullValues`
  - Input: `[9.0, null, 8.5, null]`
  - Expected: `2`
  - Mục đích: Bỏ qua giá trị null trong danh sách

#### **B. Test cho `calculateValidAverage()` - 12 test cases**

##### 1. **Trường hợp bình thường** (Normal Cases)
- `testCalculateValidAverage_MixedValidAndInvalid`
  - Input: `[9.0, 8.5, 7.0, 11.0, -1.0]`
  - Expected: `8.17` (trung bình của 9.0, 8.5, 7.0)
  - Mục đích: Tính trung bình chỉ với điểm hợp lệ

- `testCalculateValidAverage_AllValid`
  - Input: `[10.0, 8.0, 6.0]`
  - Expected: `8.0`
  - Mục đích: Tất cả điểm hợp lệ

##### 2. **Trường hợp biên** (Boundary Cases)
- `testCalculateValidAverage_EmptyList`
  - Input: `[]`
  - Expected: `0.0`
  - Mục đích: Danh sách rỗng

- `testCalculateValidAverage_NullList`
  - Input: `null`
  - Expected: `0.0`
  - Mục đích: Danh sách null

- `testCalculateValidAverage_OnlyZeros`
  - Input: `[0.0, 0.0, 0.0]`
  - Expected: `0.0`
  - Mục đích: Trung bình các số 0

- `testCalculateValidAverage_OnlyTens`
  - Input: `[10.0, 10.0, 10.0]`
  - Expected: `10.0`
  - Mục đích: Trung bình các số 10

- `testCalculateValidAverage_BoundaryValues`
  - Input: `[0.0, 10.0]`
  - Expected: `5.0`
  - Mục đích: Kiểm tra cả hai biên

##### 3. **Trường hợp ngoại lệ** (Exception Cases)
- `testCalculateValidAverage_WithNegativeScores`
  - Input: `[10.0, -5.0, 8.0, -1.0]`
  - Expected: `9.0` (trung bình của 10.0 và 8.0)
  - Mục đích: Bỏ qua điểm âm

- `testCalculateValidAverage_WithScoresAboveTen`
  - Input: `[10.0, 15.0, 8.0, 100.0]`
  - Expected: `9.0`
  - Mục đích: Bỏ qua điểm > 10

- `testCalculateValidAverage_AllInvalid`
  - Input: `[-1.0, 11.0, -5.0, 20.0]`
  - Expected: `0.0`
  - Mục đích: Không có điểm hợp lệ nào

- `testCalculateValidAverage_WithNullValues`
  - Input: `[10.0, null, 8.0, null]`
  - Expected: `9.0`
  - Mục đích: Bỏ qua null values

- `testCalculateValidAverage_SingleValidScore`
  - Input: `[7.5]`
  - Expected: `7.5`
  - Mục đích: Chỉ có một điểm hợp lệ

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

