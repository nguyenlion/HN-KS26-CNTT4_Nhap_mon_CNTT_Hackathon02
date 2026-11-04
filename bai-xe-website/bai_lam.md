# bai_lam

# BÀI LÀM – HACKATHON 02

- **Mã đề:** 02
- **Họ tên: Nguyen Khac Hieu**
- **Lớp: CNTT4**
- **Link repository:**
- **Hệ điều hành (Windows/macOS): Windows**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```bash
+ pwd
+ ls -force
+ Move-Item .\huong_dan_van_hanh.txt .\docs\
+ mkdir backup
+ Copy-Item .\data\luot_gui_xe_thang_2.xlsx .\backup\
+ rm .\temp_202.tmp
+ cd .\logs\
 ls
 cd ..
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         4/11/2026   7:41 am                data
d-----         4/11/2026   7:39 am                docs
d-----         4/11/2026   7:39 am                evidence
d-----         4/11/2026   7:41 am                logs
d-----         4/11/2026   7:38 am                web
------         3/11/2026   7:06 am             73 .env
-a----         3/11/2026   7:06 am           2412 bai_lam.md
-a----         3/11/2026   7:06 am            155 huong_dan_van_hanh.txt
------         3/11/2026   7:06 am             22 temp_202.tmp
```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```bash
Get-Content .\logs\gate.log | Select-String "status=500" > .\logs\loi_500.txt
```

### 2 dòng đầu tiên trong logs/loi_500.txt

```

2026-02-28 08:08:39 POST /api/cho-trong status=500
```

### b) Lệnh đếm số dòng status=404 và kết quả

```bash
 (Get-Content .\logs\gate.log | Select-String "status=400").count
```

```
0
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```bash
.\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```
=== BAO CAO SU CO WEBSITE === 

2026-02-28 08:12:50 GET /tin-tuc status=404
2026-02-28 08:31:56 GET /images/so-do-bai.jpg status=404
2026-02-28 08:36:18 GET /images/so-do-bai.jpg status=404
2026-02-28 08:47:02 GET /tin-tuc status=404

Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.
> 
- [x]  README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x]  .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x]  .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | network | logo.jpg (failed) | đổi lại đường link của ảnh |
| 2 | console | Uncaught ReferenceError: hienThiGiaGui is not defined
at app.js:18:1 | sửa lại tên hàm khi khai báo hàm |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).
> 

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Khi mở file `web/index.html` bằng trình duyệt để kiểm tra giao diện trang web ParkEasy-Bãi giữ xe thông minh
- **Expected:** Trang web tải đầy đủ hình ảnh logo và bảng giá gửi xe hiển thị dữ liệu chính xác.
- **Actual:** Logo không hiển thị (lỗi 404 Not Found) và bảng giá bị trống hoàn toàn không có dữ liệu.
- **Log: app.js:18 Uncaught ReferenceError: hienThiGiaGui is not defined**

### Câu tìm kiếm Google

```
site:stackoverflow.com "app.js:18 Uncaught ReferenceError: hienThiGiaGui is not defined"
```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/luot_gui_xe_thang_2.xlsx`, không cần ghi vào đây.
>