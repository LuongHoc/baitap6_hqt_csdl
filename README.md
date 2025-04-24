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
