# BÀI LÀM – HACKATHON 02

- **Mã đề:** 09
- **Họ tên: Nguyễn Quang Thành**
- **Lớp: CNTT2**
- **Link repository: https://github.com/Nhap-Mon-CNTT/HCM-KS26-CNTT2_Nhap-mon-CNTT_Hackathon02.git**
- **Hệ điều hành (Windows/macOS): Windows 11**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
# Ghi lần lượt các lệnh đã chạy, mỗi lệnh một dòng
pwd
Get-ChildItem -Force
Move-Item .\noi_quy_thanh_vien.txt .\docs
mkdir .\backup
cp .\data\thue_cho_thang_9.xlsx .\backup\
rm *.tmp
cd .\logs; Get-ChildItem
cd ..
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory:
    C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:44 PM                backup
d-----        11/11/2026   1:38 PM                data
d-----        11/11/2026   1:42 PM                docs
d-----        11/11/2026   1:36 PM                evidence
d-----        11/11/2026   1:38 PM                logs
d-----        11/11/2026   1:30 PM                web
------         11/3/2026   7:08 AM             72 .env
-a----         11/3/2026   7:08 AM           2409 bai_lam.md


    Directory: C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-w
    ebsite\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6162 thue_cho_thang_9.xlsx


    Directory:
    C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6162 thue_cho_thang_9.xlsx


    Directory:
    C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            146 noi_quy_thanh_vien.txt


    Directory:
    C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            991 member.log


    Directory:
    C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:30 PM                images
------         11/3/2026   7:08 AM            605 app.js
------         11/3/2026   7:08 AM            543 index.html
------         11/3/2026   7:08 AM            460 style.css


    Directory: C:\Users\quang\Downloads\starter-kit\starter-kit\coworking-w
    ebsite\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:08 AM           3069 logo-coworkhub.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Select-String "status=500" logs/member.log > logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\member.log:3:2026-09-28 08:10:39 POST /api/dat-cho status=500
logs\member.log:4:2026-09-28 08:12:50 POST /api/dat-cho status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
Select-String "status=404" logs\member.log | Measure-Object -Line

```

```text
Lines Words Characters Property
----- ----- ---------- --------
    4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-09-28 08:28:45 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:41:40 GET /goi-cu status=404
2026-09-28 08:49:13 GET /images/phong-hop-3.jpg status=404
2026-09-28 08:59:46 GET /images/phong-hop-3.jpg status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 




```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 |Network  |  Failed to load resource: net::ERR_UNEXPECTED| Tại dòng số 10 của file web\index.htlm sửa đoạn `src="images/logo.png` thành `src="images/logo-coworkhub.png`|
| 2 |Console  |  app.js:18 Uncaught ReferenceError: hienThiBangThue is not defined
    at app.js:18:1| Chưa biết cách sửa |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** 
  + Hệ điều hành: Windows 11
  + IDE: VS Code
  + Trình duyệt: Firefox
- **Expected:** 
  + Trang web hiển thị được bảng giá thuê chỗ bao gồm: Mã gói; Gói thuê; Giá\ngày (VND)
- **Actual:** 
  + Thực tế trang web không hiển thị được bảng giá và báo lỗi ở dòng 18 của file `web\app.js`
- **Log:** 
  + Uncaught ReferenceError: hienThiBangThue is not defined at app.js:18:1

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError: is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/thue_cho_thang_9.xlsx`, không cần ghi vào đây.
