# BÀI LÀM – THI THỬ HACKATHON 01

- **Mã đề:** Thi thử
- **Họ tên:** Phạm Quốc Đạt
- **Lớp:** CNTT1-K26
- **Link repository:** 
- **Hệ điều hành (Windows/macOS):** Windowns
- 

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
# Ghi lần lượt các lệnh đã chạy, mỗi lệnh một dòng
pwd
get-childitem -Force -Recurse
mv nhap_hang.txt D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\docs
mv logo_van_phong_pham.png  D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\backup
cp logo_van_phong_pham.png ../backup  
rm   "*.tmp"   
cd ..
cd logs
get-childitem 
cd ..






```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text

    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        10/23/2026   6:17 PM                backup
d-----        10/23/2026   5:59 PM                data
d-----        10/23/2026   6:10 PM                docs
d-----        10/23/2026   6:00 PM                logs
d-----        10/23/2026   6:16 PM                media
-a----        10/19/2026   9:41 AM             78 .env
-a----        10/19/2026  10:00 AM           2253 bai_lam.md


    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/19/2026   9:41 AM           6053 logo_van_phong_pham.png


    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/19/2026   9:41 AM           6105 don_ban_hang_thang_10.xlsx


    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/19/2026   9:41 AM             51 nhap_hang.txt


    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/19/2026   9:41 AM           1053 shop.log


    Directory: D:\Ôn_thi_giữa-kì\starter-kit\starter-kit\van-phong-pham-website\media


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/19/2026   9:41 AM           6053 logo_van_phong_pham.png


```

## 4.3. Lọc log thủ công

### Lệnh đã chạy

```shell
#  select-string "ERROR" logs/shop.log

```

### 2 dòng lỗi đầu tiên trong daily_report.txt

```text
logs\shop.log:3:2025-10-28 08:24:28 [ERROR] Thanh toan bi tu choi
logs\shop.log:5:2025-10-28 08:30:28 [ERROR] Thanh toan bi tu choi



```

## 4.4. Thao tác với tài liệu Markdown (README.md)

> README.md được chấm trực tiếp trên file `README.md` ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] Heading 1: tên dự án
- [x] Mô tả ngắn có cả **in đậm** và *in nghiêng*
- [x] Bảng `Thư mục | Nội dung`, ít nhất 3 dòng dữ liệu
- [x] Code block chứa lệnh PowerShell/Terminal liệt kê nội dung dự án
- [x] Task list ít nhất 2 công việc, có ít nhất 1 mục đã hoàn thành
- [x] Blockquote nhắc không upload `.env`

## 4.5. Chạy script auto_report (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
gc logs/shop.log
select-string "ERROR" logs/shop.log | out-file logs/auto_report.txt


```

### Nội dung file logs/auto_report.txt

```text

logs\shop.log:3:2025-10-28 08:24:28 [ERROR] Thanh toan bi tu choi
logs\shop.log:5:2025-10-28 08:30:28 [ERROR] Thanh toan bi tu choi
logs\shop.log:6:2025-10-28 08:33:28 [ERROR] Ket noi kho du lieu that bai
logs\shop.log:8:2025-10-28 08:39:28 [ERROR] Ket noi kho du lieu that bai
logs\shop.log:9:2025-10-28 08:42:28 [ERROR] Ket noi kho du lieu that bai
logs\shop.log:19:2025-10-28 09:12:28 [ERROR] Thanh toan bi tu choi



```

## 4.6. Đếm số dòng lỗi

### Lệnh

```shell
#  select-string "ERROR" logs/shop.log | Measure-Object

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
van-phong-pham-website> select-string "ERROR" logs/shop.log | Measure-Object


Count    : 6
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

```

## 4.7. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
new-item logs/tong_hop.txt 
cd logs 
" === TONG HOP LOG ===" > tong_hop.txt    
select-string "WARNING" shop.log | Out-file tong_hop.txt -Append
select-string "ERROR" shop.log | Measure-Object | out-file tong_hop.txt -Append

```

### Nội dung file logs/tong_hop.txt

```
 === TONG HOP LOG ===

shop.log:12:2025-10-28 08:51:28 [WARNING] Thoi gian tai trang cham
shop.log:13:2025-10-28 08:54:28 [WARNING] Anh san pham dung luong lon
shop.log:14:2025-10-28 08:57:28 [WARNING] Thoi gian tai trang cham





Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 





```

## 4.8. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_ban_thang_10.xlsx`, không cần ghi vào đây.
