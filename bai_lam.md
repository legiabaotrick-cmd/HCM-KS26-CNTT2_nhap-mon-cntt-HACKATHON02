# BÀI LÀM – HACKATHON 02

- **Mã đề:** 08
- **Họ tên:**Lê Gia Bảo
- **Lớp:**HCM-KS26-CNTT2
- **Link repository:**https://github.com/legiabaotrick-cmd/HCM-KS26-CNTT2_nhap-mon-cntt-HACKATHON02
- **Hệ điều hành (Windows/macOS):**Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -force
mv quy_trinh_thu_am.txt docs
mkdir backup
cp .\data\lich_thu_thang_8.xlsx backup
rm *.tmp
cd logs
ls
cd ..

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:41 PM                backup
d-----        11/11/2026   1:37 PM                data
d-----        11/11/2026   1:40 PM                docs
d-----        11/11/2026   1:35 PM                evidence
d-----        11/11/2026   1:38 PM                logs
d-----        11/11/2026   1:34 PM                web
------         11/3/2026   7:08 AM             74 .env
-a----         11/3/2026   7:08 AM           2409 bai_lam.md


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6136 lich_thu_thang_8.xlsx


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM           6136 lich_thu_thang_8.xlsx


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            157 quy_trinh_thu_am.txt


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:08 AM            992 Studio.log


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   1:34 PM                images
------         11/3/2026   7:08 AM            586 app.js
------         11/3/2026   7:08 AM            514 index.html
------         11/3/2026   7:08 AM            460 style.css


    Directory: C:\Users\User\Downloads\New folder\starter-kit\starter-kit\phong-thu-am-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:08 AM           3097 logo-soundlab.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
get-childitem .\logs\Studio.log | select-string "status=500" > logs/loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\Studio.log:8:2026-08-28 08:25:34 POST /api/dat-lich status=500
logs\Studio.log:11:2026-08-28 08:34:07 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(get-childitem .\logs\Studio.log | select-string "status=404").count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
./tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU SO WEBSITE ===

2026-08-28 08:16:01 GET /tin-tuc status=404
2026-08-28 08:47:51 GET /san-pham-cu status=404
2026-08-28 08:58:24 GET /images/phong-thu-2.jpg status=404
2026-08-28 09:00:35 GET /images/phong-thu-2.jpg status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 



```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [ ] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [ ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [ ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | console | ERR_FILE_NOT_FOUND | đổi thành <img src="images/logo-soundlab.png"  trong index.html dòng số 10|
| 2 | console | Uncaught ReferenceError: hienThiGoiThuAm is not defined | hienThiGoiThuAm(); đổi thành hienThiGoiThu(); trong dòng số 18 |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Mở web/index.html bằng Chrome, trang Soundlab-Phòng thu âm; đã sửa logo nhưng bảng giá thu âm vẫn trống.
- **Expected:** Bảng giá hiển thị 3 dòng dữ liệu (mã gói, gói thu, giá/giờ).
- **Actual:** Bảng chỉ có dòng tiêu đề; Console báo lỗi đỏ.
- **Log:** Uncaught ReferenceError: hienThiGoiThuAm is not defined at app.js:18

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError: hienThiGoiThuAm is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/lich_thu_thang_8.xlsx`, không cần ghi vào đây.
