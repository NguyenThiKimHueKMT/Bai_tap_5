# Bai_tap_5
Bài tập về nhà 05 của SV: K225480106026-Nguyễn Thị kim Huệ- Môn Hệ quản trị CSDL
A.Trình bày lại đầu bài của đồ án PT&TKHT:
Mô tả bài toán của đồ án PT&TKHT, đưa ra yêu cầu của bài toán đó: -Tên đề tài:  Quản lý khách sạn -Khái quát nội dung đề tài: Hệ thống cho phép quản lý sách, sinh viên và các phiếu mượn trả. Sinh viên mượn sách qua phiếu, hệ thống tự động cập nhật số lượt mượn, kiểm tra số lượng tồn và hỗ trợ thống kê nhanh. Mục tiêu là tin học hóa quy trình quản lý thư viện, giảm sai sót, tăng hiệu quả tra cứu và thống kê.
Cơ sở dữ liệu của Đồ án PT&TKHT : Có database với các bảng dữ liệu cần thiết (3nf), Các bảng này đã có PK, FK,CK cần thiết.  
![Ảnh chụp màn hình 2025-04-23 203054](https://github.com/user-attachments/assets/585f265f-a332-468f-9f42-0ec86b1cafd1)  
B. Nội dung Bài tập 05:

Dựa trên cơ sở là csdl của Đồ án
Tìm cách bổ xung thêm 1 (hoặc vài) trường phi chuẩn (là trường tính toán đc, nhưng thêm vào thì ok hơn, ok hơn theo 1 logic nào đó, vd ok hơn về speed) => Nêu rõ logic này!
Viết trigger cho 1 bảng nào đó, mà có sử dụng trường phi chuẩn này, nhằm đạt được 1 vài mục tiêu nào đó. => Nêu rõ các mục tiêu
Nhập dữ liệu có kiểm soát, nhằm để test sự hiệu quả của việc trigger auto run.
Kết luận về Trigger đã giúp gì cho đồ án của em.
DEADLINE: 23H59:59 NGÀY 23/04/2025  
BÀI LÀM
ĐỀ TÀI: QUẢN LÝ QUÁN MƯƠN TRẢ SÁCH THƯ VIỆN
A. Trình bày lại đầu bài của đồ án PT&TKHT:
1. Mô tả bài toán của đồ án PT&TKHT, đưa ra yêu cầu của bài toán đó
2. Thư viện trường học cần xây dựng một hệ thống phần mềm nhằm hỗ trợ quản lý việc mượn và trả sách của sinh viên một cách hiệu quả, chính xác và nhanh chóng. Hệ thống giúp cán bộ thư viện quản lý thông tin sinh viên, sách, phiếu mượn, chi tiết từng lần mượn-trả sách và thống kê số lượt mượn để phục vụ công tác quản lý và báo cáo
Hiện nay, việc quản lý hoạt động mượn – trả sách tại thư viện chủ yếu được thực hiện thủ công (ghi chép sổ tay) hoặc bằng các phần mềm đơn giản như Excel. Cách làm này tồn tại nhiều hạn chế như:
-khó kiểm soát số lượng sách còn – đã mượn, việc thống kê tồn kho không chính xác, dễ nhầm lẫn khi cập nhật thủ công
-tốn thời gian và dễ sai sót trong việc nhập liệu, tra cứu thông tin
-không có cảnh báo hoặc ghi log tự động, không thể biết sách nào được mượn nhiều hoặc ai thường xuyên trả muộn
-thiếu khả năng thống kê, báo cáo theo sinh viên, đầu sách hoặc thời gian
-không có phân quyền người dùng, gây khó khăn trong việc kiểm soát và bảo mật dữ liệu
2. Yêu cầu của bài toán
 Quản lý Sinh viên:Lưu trữ thông tin sinh viên như mã sinh viên, họ tên, lớp, khoa.
 Quản lý Sách:Quản lý các đầu sách với thông tin như mã sách, tên sách, tác giả, nhà xuất bản, số lượng tồn, số lượt mượn.
 Lập phiếu mượn:Cho phép sinh viên mượn một hoặc nhiều cuốn sách.
 Mỗi phiếu mượn ghi lại ngày mượn, ngày hẹn trả.
 Trả sách:Ghi nhận ngày trả thực tế, tự động cập nhật số lượng tồn kho và số lượt mượn của sách.
 Ghi log lịch sử cập nhật:Hệ thống ghi lại lịch sử các lần tăng số lượt mượn của sách phục vụ thống kê và truy vết.
3. Cơ sở dữ liệu của Đồ án PT&TKHT : Có database với các bảng dữ liệu cần thiết (3nf), Các bảng này đã có PK, FK, CK cần thiết
3.1. Tạo Database QuanLyMuonTraSachThuVien
   ![image](https://github.com/user-attachments/assets/e1fbbb2d-9a07-4b9d-b8bd-8765d181c0c2)
3.2. Tạo bảng
   Bảng Sinhvien
   Gồm các trường:
    MaSV NVARCHAR(10)
    HoTen NVARCHAR(100)
    Khoa NVARCHAR(50)
    Lop NVARCHAR(20)
![image](https://github.com/user-attachments/assets/a530ed24-7e1a-4b30-9c87-818840df8e61)

Bảng Sach
     Gồm các trường:  
     MaSach NVARCHAR(10) 
    TenSach NVARCHAR(100)
    TacGia NVARCHAR(100)
    NhaXuatBan NVARCHAR(100)
    SoLuongTon INT
    SoLuotMuon INT
![image](https://github.com/user-attachments/assets/79cf29bb-6865-411c-af82-97a8904a5590)    
Bảng PhieuMuon
   Gồm các trường:  
    MaPhieu NVARCHAR(10) PRIMARY KEY
    MaSV NVARCHAR(10)
    NgayMuon DATE
    NgayHenTra DATE
![image](https://github.com/user-attachments/assets/80aae5f7-a466-497c-9cf8-2fb285555d0e)   
Bảng ChiTietPhieuMuon
    Gồm các trường: 
    MaPhieu NVARCHAR(10)
    MaSach NVARCHAR(10)
    NgayTraThucTe DATE 
Bảng PhieuTra
     Gồm các trường:  
    MaPhieuTra NVARCHAR(10)
    MaSV NVARCHAR(10)
    NgayTra DATE
![image](https://github.com/user-attachments/assets/2aa1ec60-337b-4c4f-92cf-6080525c96e8)  
Ảnh này để thầy giáo thấy rõ khóa chính, khóa ngoại và kiểu dữ liệu  
![image](https://github.com/user-attachments/assets/e588538c-f788-408a-a1a6-a5b9d99d2c4b)
![image](https://github.com/user-attachments/assets/8adafda1-8096-4231-bcf3-c17c56c66adc)   
![image](https://github.com/user-attachments/assets/91720aa6-f79b-451e-87f7-904179a97b47)  
![image](https://github.com/user-attachments/assets/073d679b-87f8-4c8d-9ff8-196947c9478c)  
![image](https://github.com/user-attachments/assets/21fa7046-87ce-4b82-990a-9b6be47907c8)
B. Nội dung Bài tập 05:
Dựa trên cơ sở là csdl của Đồ án
Tìm cách bổ xung thêm 1 (hoặc vài) trường phi chuẩn (là trường tính toán đc, nhưng thêm vào thì ok hơn, ok hơn theo 1 logic nào đó, vd ok hơn về speed) => Nêu rõ logic này!
Viết trigger cho 1 bảng nào đó, mà có sử dụng trường phi chuẩn này, nhằm đạt được 1 vài mục tiêu nào đó. => Nêu rõ các mục tiêu
Nhập dữ liệu có kiểm soát, nhằm để test sự hiệu quả của việc trigger auto run.
Kết luận về Trigger đã giúp gì cho đồ án của em.
1. Nhập dữ liệu cho các bảng
   1.1 Bảng SinhVien
   ![image](https://github.com/user-attachments/assets/e7f55d6c-7872-4f08-9bc5-4469e3736ae6)
   1.2 Bảng sách
   ![image](https://github.com/user-attachments/assets/b922128e-57c7-4d76-9481-d68542ad0371)
    1.3 Bảng PhieuMuon
   ![image](https://github.com/user-attachments/assets/4be837e3-04ae-4477-86fe-0db826da100b)
   1.4. bảng Chitietmuon
   ![image](https://github.com/user-attachments/assets/7c02d5b3-e075-4852-a7ea-5cba12847067)
   1.4 Bảng PhieuTra
   ![image](https://github.com/user-attachments/assets/6c709ab0-1efb-4c5a-b24a-bf4c35d2ff9f)
3. Bổ sung 1 trường phi chuẩn
Trường phi chuẩn (denormalized field) là trường không cần thiết phải có trong mô hình chuẩn hóa dữ liệu (3NF trở lên), vì giá trị của nó có thể được tính toán từ các trường khác trong hệ thống. Tuy nhiên, người ta chủ động thêm vào để tăng hiệu năng hoặc phục vụ mục tiêu quản lý cụ thể nào đó.
Bổ sung 1 trường phi chuẩn TongsoDanhSachMuon vào bảng PhieuMuon
![image](https://github.com/user-attachments/assets/ad17f985-1c82-493f-842a-727b49bbbf53)
3. Viết Trigger cho bảng PhieuMuon
![image](https://github.com/user-attachments/assets/eda17cf8-702a-493c-95ef-d65803be7003)
Kết quả sau khi chạy Tegger thì TongSoLuongMuon sẽ tự động tích cho mình:
![image](https://github.com/user-attachments/assets/b1011239-04a4-452c-8e3a-0108ccbea772)
Trigger đã giúp hệ thống thư viện tự động cập nhật tổng số sách đã mượn (TongSoLuongMuon) sau mỗi lượt mượn. Nhờ đó, dữ liệu luôn chính xác, hỗ trợ thống kê, phân tích và theo dõi nhu cầu mượn sách hiệu quả hơn. Việc sử dụng trigger với trường phi chuẩn giúp hệ thống giảm thao tác thủ công, tăng hiệu suất và vận hành ổn định hơn.










