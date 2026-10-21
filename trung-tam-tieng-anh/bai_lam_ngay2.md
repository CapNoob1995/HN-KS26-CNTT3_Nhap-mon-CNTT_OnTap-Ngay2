# BÀI LÀM – ÔN TẬP NGÀY 2

* **Họ tên:Bùi Quang Huy**
* **Lớp:HN-KS26-CNTT3**
* **Link repository:**
* **Hệ điều hành (Windows/macOS):Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
Get-Content .\\logs\\access.log | Select-String "ERROR" > .\\logs\\error\\\_report.txt
Get-Content .\\logs\\error\\\_report.txt
```

### 2 dòng lỗi đầu tiên trong error\_report.txt

```text
2025-10-18 08:17:59 \\\[ERROR] Khong tim thay trang /lich-thi (404)

2025-10-18 08:25:55 \\\[ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
(cat .\\logs\\access.log | select-string "WARNING").count
(cat .\\logs\\payment.log | select-string "ERROR").count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3
```

## Bài 3. Chạy script auto\_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\\auto\\\_warning.ps1

```

### Nội dung file logs/warning\_report.txt

```text
2025-10-18 09:19:13 \[WARNING] Cong thanh toan phan hoi cham

2025-10-18 09:28:16 \[WARNING] Nhieu lan nhap sai ma OTP

2025-10-18 09:43:01 \[WARNING] So du vi gan bang hoc phi

2025-10-18 09:46:22 \[WARNING] So du vi gan bang hoc phi

2025-10-18 09:49:43 \[WARNING] So du vi gan bang hoc phi
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
New-Item .\\logs\\tong\_hop\_ngay\_2.txt
"=== TONG HOP ACCESS LOG ===" > .\\logs\\tong\_hop\_ngay\_2.txt
Get-Content .\\logs\\access.log | Select-String "ERROR" >> .\\logs\\tong\_hop\_ngay\_2.txt
Get-Content .\\logs\\payment.log | Select-String "WARNING" >> .\\logs\\tong\_hop\_ngay\_2.txt

```

### Nội dung file logs/tong\_hop\_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===



2025-10-18 08:17:59 \[ERROR] Khong tim thay trang /lich-thi (404)

2025-10-18 08:25:55 \[ERROR] Het thoi gian cho (timeout)

2025-10-18 08:33:51 \[ERROR] Ket noi may chu du lieu that bai

2025-10-18 08:37:19 \[ERROR] Ket noi may chu du lieu that bai

2025-10-18 08:49:43 \[ERROR] Het thoi gian cho (timeout)

2025-10-18 08:53:11 \[ERROR] Het thoi gian cho (timeout)











2025-10-18 09:19:13 \[WARNING] Cong thanh toan phan hoi cham

2025-10-18 09:28:16 \[WARNING] Nhieu lan nhap sai ma OTP

2025-10-18 09:43:01 \[WARNING] So du vi gan bang hoc phi

2025-10-18 09:46:22 \[WARNING] So du vi gan bang hoc phi

2025-10-18 09:49:43 \[WARNING] So du vi gan bang hoc phi

```

## Bài 5. Câu hỏi ngắn

* **a)Trong PowerShell, dấu > (ghi đè) dùng để ghi kết quả lệnh vào tệp và xóa toàn bộ nội dung cũ nếu tệp đã tồn tại.
                    dấu >> (ghi nối) dùng để ghi thêm kết quả vào cuối tệp mà không làm mất dữ liệu cũ.**
* **b)Nội dung tiêu đề === TONG HOP ACCESS LOG === ở dòng đầu tiên sẽ bị bị ghi đè. File tong\_hop\_ngay2.txt sẽ chỉ còn chứa các dòng ERROR của access.log.**
* **c)Nếu dùng đường dẫn tuyệt đối, script sẽ bị lỗi File Not Found khi gửi cho người khác chạy hoặc khi chuyển dự án sang thư mục/máy tính khác do cấu trúc đường dẫn thư mục người dùng không giống nhau.**

## Tự chấm (điền sau khi có đáp án)

* **Điểm tự chấm:** ..../100
* **Lỗi mình đã mắc và cách sửa:**

