# Họ và tên: Lương Văn Học - MSSV: K225480106025
# Bài tập 6: Hệ quản trị CSDL
# Chủ đề: Câu lệnh Select
# Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)
# Bài làm
## 1. Các bước để import dữ liệu trong sv_tnut.sql vào SQL Server
### 1. Tạo cơ sở dữ liệu trong SQL Server:
- Mở SQL Server Management Studio (SSMS).
- Tạo một cơ sở dữ liệu mới tên SinhVienDB
![image](https://github.com/user-attachments/assets/bad42a7b-0543-4548-898e-311c64c69f2d)
### 2. Import file sv_tnut.sql:
- Trong SSMS, chọn File > Open > File và chọn file sv_tnut.sql.
![image](https://github.com/user-attachments/assets/34222402-32a7-4b02-a59d-7eab0d3f8c8e)
![image](https://github.com/user-attachments/assets/d95e7dcb-cc11-4971-a8e9-5da9a84e22c5)
- Đảm bảo đã chọn đúng cơ sở dữ liệu (SinhVienDB) trong thanh công cụ.
![image](https://github.com/user-attachments/assets/338360ba-3259-447e-ba6a-eae1ebc04094)
- Nhấn Execute (F5) để chạy toàn bộ script. Script sẽ tạo bảng và chèn dữ liệu.
![image](https://github.com/user-attachments/assets/06b45e9b-6783-4483-91ab-b2055d0ad699)
### 3. Kiểm tra dữ liệu
- Dùng lệnh: SELECT * FROM SV;
![image](https://github.com/user-attachments/assets/65681ce2-9c83-44e5-9ae7-ddd53a29a15c)
## 2. Dữ liệu đầu vào 
- Tên: Lương Văn Học
- Sđt: 0329379387
- Ngày, tháng, năm sinh: 02/06/2004
## 3. Nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
Sử dụng lệnh:
```
SELECT *
FROM SV
WHERE ns = '2004-06-02';
```
![image](https://github.com/user-attachments/assets/1fb470d0-d576-4796-be8d-c7b565228540)
## 4. Nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
Sử dụng lệnh:
```
SELECT *
FROM SV
WHERE DAY(ns) = 2 AND MONTH(ns) = 6;
```
![image](https://github.com/user-attachments/assets/c1427a59-f059-4287-a693-95bca2e0e98d)
## 5. Nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
Sử dụng lệnh:
```
SELECT *
FROM SV
WHERE MONTH(ns) = 6 AND YEAR(ns) = 2004;
```
![image](https://github.com/user-attachments/assets/a4813c10-9d7d-4ef9-a608-0b38a04ba155)
## 6. Nhập sql để tìm xem có những sv nào trùng tên với em?
Sử dụng lệnh:
```
SELECT *
FROM SV
WHERE ten = N'Học';
```
![image](https://github.com/user-attachments/assets/f40d8584-cd22-4bcb-ac8c-d15e93182edc)
## 7. Nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
sử dụng lệnh:
```
SELECT *
FROM SV
WHERE hodem = N'Lương Văn';
```
![image](https://github.com/user-attachments/assets/a8c328f2-9d7e-46d7-a2e2-35efcc6ace49)
## 8. Nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
Sử dụng lệnh:
```
DECLARE @YourPhone NVARCHAR(26) = '0329379387';

SELECT *
FROM SV
WHERE LEN(sdt) = 10
AND (
    (SUBSTRING(sdt, 1, 1) <> SUBSTRING(@YourPhone, 1, 1) AND SUBSTRING(sdt, 2, 9) = SUBSTRING(@YourPhone, 2, 9)) OR
    (SUBSTRING(sdt, 1, 1) = SUBSTRING(@YourPhone, 1, 1) AND SUBSTRING(sdt, 2, 1) <> SUBSTRING(@YourPhone, 2, 1) AND SUBSTRING(sdt, 3, 8) = SUBSTRING(@YourPhone, 3, 8)) OR
    (SUBSTRING(sdt, 1, 2) = SUBSTRING(@YourPhone, 1, 2) AND SUBSTRING(sdt, 3, 1) <> SUBSTRING(@YourPhone, 3, 1) AND SUBSTRING(sdt, 4, 7) = SUBSTRING(@YourPhone, 4, 7)) OR
    (SUBSTRING(sdt, 1, 3) = SUBSTRING(@YourPhone, 1, 3) AND SUBSTRING(sdt, 4, 1) <> SUBSTRING(@YourPhone, 4, 1) AND SUBSTRING(sdt, 5, 6) = SUBSTRING(@YourPhone, 5, 6)) OR
    (SUBSTRING(sdt, 1, 4) = SUBSTRING(@YourPhone, 1, 4) AND SUBSTRING(sdt, 5, 1) <> SUBSTRING(@YourPhone, 5, 1) AND SUBSTRING(sdt, 6, 5) = SUBSTRING(@YourPhone, 6, 5)) OR
    (SUBSTRING(sdt, 1, 5) = SUBSTRING(@YourPhone, 1, 5) AND SUBSTRING(sdt, 6, 1) <> SUBSTRING(@YourPhone, 6, 1) AND SUBSTRING(sdt, 7, 4) = SUBSTRING(@YourPhone, 7, 4)) OR
    (SUBSTRING(sdt, 1, 6) = SUBSTRING(@YourPhone, 1, 6) AND SUBSTRING(sdt, 7, 1) <> SUBSTRING(@YourPhone, 7, 1) AND SUBSTRING(sdt, 8, 3) = SUBSTRING(@YourPhone, 8, 3)) OR
    (SUBSTRING(sdt, 1, 7) = SUBSTRING(@YourPhone, 1, 7) AND SUBSTRING(sdt, 8, 1) <> SUBSTRING(@YourPhone, 8, 1) AND SUBSTRING(sdt, 9, 2) = SUBSTRING(@YourPhone, 9, 2)) OR
    (SUBSTRING(sdt, 1, 8) = SUBSTRING(@YourPhone, 1, 8) AND SUBSTRING(sdt, 9, 1) <> SUBSTRING(@YourPhone, 9, 1) AND SUBSTRING(sdt, 10, 1) = SUBSTRING(@YourPhone, 10, 1)) OR
    (SUBSTRING(sdt, 1, 9) = SUBSTRING(@YourPhone, 1, 9) AND SUBSTRING(sdt, 10, 1) <> SUBSTRING(@YourPhone, 10, 1))
);
```
![image](https://github.com/user-attachments/assets/c0638be7-c7a2-4e8d-8b16-ca9deff44e07)
## 9.  Hãy liệt kê tất cả các sv ngành kmt, sắp xếp theo tên và họ đệm, kiểu tiếng  việt, giải thích.
Sử dụng lệnh:
```
SELECT *
FROM SV
WHERE lop LIKE N'%KMT%'
ORDER BY ten, hodem COLLATE Vietnamese_CI_AI;
```
![image](https://github.com/user-attachments/assets/bdabd743-8cfc-42ec-ba45-56ee8e449ffa)
## 10. Hãy nhập sql để liệt kê các sv nữ ngành kmt có trong bảng sv (trình bày quá trình suy nghĩ và giải những vướng mắc)
###  Quá trình suy nghĩ:
- Xác định yêu cầu:
Tìm sinh viên thuộc ngành KMT (giả định qua cột lop chứa KMT).
Chỉ lấy sinh viên nữ. Nhưng bảng không có cột GioiTinh, đây là một vướng mắc.
- Vướng mắc:
Không có cột GioiTinh: Bảng chỉ có masv, hodem, ten, ns, lop,sdt:
### Giải pháp:
Cách 1: Phân tích tên (ten) để suy ra giới tính (ví dụ: tên thường gặp ở nữ như Hương, Lan). Tuy nhiên, cách này có thể  không chính xác. 
Cách 2: Giả định có một cách khác để xác định giới tính (ví dụ: mã sinh viên chứa ký tự chỉ giới tính, hoặc dữ liệu từ bảng khác). Vì không có thông tin này, tôi sẽ bỏ điều kiện giới tính và chỉ lọc ngành KMT, đồng thời ghi chú vấn đề.
Cách 3: Yêu cầu xác nhận xem có bảng khác chứa thông tin giới tính hay không.
- Quyết định:
Vì không có cột GioiTinh, em sẽ viết câu lệnh chỉ lọc sinh viên ngành KMT.
```
SELECT *
FROM SV
WHERE lop LIKE N'%KMT%';
```
![image](https://github.com/user-attachments/assets/c5c1c790-ec3c-4051-8b8e-45584502e973)


