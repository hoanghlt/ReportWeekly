
# Flow Toàn Trình: DKOL → Omnisell → WSale → SOP

###### Link tài liệu:
---- Link tài liệu Wsale: https://docs.google.com/document/d/1Cd8DZVT-RDFRur14Ry172Lm0HYuoOYX5/edit
---- API đẩy NOTI SOP Cung cấp: https://docs.google.com/spreadsheets/d/1pSn18ec0o4OiFwtCdJdcuOpT1Ye3bd8vL3EdmR1OA98/edit?gid=0#gid=0
---- Plan luồng đơn hàng toàn trinhg ECOM: https://docs.google.com/spreadsheets/d/1blJ51wgxnshPjFf3xXvNgYHXn1Gcz8Pgzgw-cMqZyOc/edit?gid=0#gid=0
---- Luồng xử lý và API prototype giữa Omnisell và Wsale: 
        https://docs.google.com/spreadsheets/d/1a59Rs9Dqphu4clu7_XSDzOKKQF1f_ta9/edit?gid=1711683772#gid=1711683772
---- Model thông tin đơn hàng Omnisell: https://jsonblob.com/1398127655328604160#google_vignette
---- Thông tin quyền HRIS: https://docs.google.com/spreadsheets/d/1Q-dWykrLZADAR6-7k-7-Amlx6BDXzPAf/edit?gid=147017012#gid=147017012
---- Thông tin quyền HRIS: https://docs.google.com/spreadsheets/d/1pyl2BjbbtR5RsnB2TfE9oV5zd2nBlgAA4RBbRP0tIlc/edit?gid=0#gid=0
---- Thông tin source Omnisell: 
        https://docs.google.com/spreadsheets/d/1dSLZv-Ohm1mLLaBP5rIsMMnFOtAqK7Zk4ecpU5rYdFE/edit?gid=1505094238#gid=1505094238

## 1. Tạo Đơn Hàng & Phân Công

1. User đăng ký trên hệ thống DKOL.
2. DKOL tạo đơn hàng và gửi thông tin đơn hàng sang Omnisell.
3. Omnisell thực hiện phân công nhân viên tư vấn cho đơn hàng.
4. Omnisell gọi **API B1** để đẩy thông tin khách hàng sang WSale, tạo checklist bán.
5. Khi checklist được tạo thành công, Omnisell gọi **API B2** để cập nhật nhân viên được phân công vào checklist trên WSale.
6. WSale ghi nhận nhân viên tư vấn và gửi notification lên SOP kèm link redirect.

## 2. Luồng Notification & Tư Vấn Trên SOP

SOP chia làm 2 luồng xử lý:

### Luồng 1: Notification trực tiếp
1. User nhận được notification trên SOP.
2. User click vào message notification và được chuyển sang màn hình chi tiết trên Wsale.

### Luồng 2: Vào từ màn hình Khách hàng phân phối
1. User vào màn hình Khách hàng được phân phối trên SOP để tìm kiếm khách hàng.
2. User tìm kiếm danh sách hợp đồng được phân công và click số HĐ hoặc Phone được chuyển vào màn hình chi tiết trên WSale.

3. Ở màn hình chi tiết Wsale, Khi thực hiện load thông tin InfoPortal, WSale gọi **API A1** để báo về Omnisell rằng user đã vào tư vấn (tắt tính năng unicast).
 **⚠️ Lưu ý: Bước này sẽ chỉ thực hiện cho các checklist có source = 22 (Omnisell) và target=0**
4. Nếu **API A1** trả về `false`, user không được phép vào màn hình tư vấn.
    **⚠️ Lưu ý: Nếu user không đủ quyền, hệ thống sẽ hiển thị thông báo "Không hợp lệ" và không cho phép vào màn hình tư vấn.**

## 3. Tư Vấn & Cập Nhật Kết Quả

1. Tại màn hình tư vấn trên WSale, khi vào trang, hệ thống gọi **API A2** để lấy thông tin chi tiết đơn hàng, load chính sách và hiển thị toàn bộ đơn hàng cho user.
2. User kiểm tra đơn hàng và thực hiện cập nhật kết quả tư vấn (Giữ nguyên luồng cập nhật bán mới).
3. Khi cập nhật kết quả tư vấn, WSale gọi **API A4** để cập nhật kết quả tư vấn về Omnisell.
4. Sau đó, WSale thực hiện tick hẹn triển khai PTC.
5. Kết thúc luồng xử lý.

## 4. Kiểm Tra Trạng Thái Checklist

WSale cung cấp cho Omnisell **API B3** để kiểm tra trạng thái checklist. Khi Omnisell cần xác minh checklist trên WSale đã được nhân viên tiếp nhận tư vấn hay chưa, sẽ gọi API này.

## 5. Danh Sách API & Chức Năng

| API      | Chức năng                                                               | Đã hoàn thành |
|----------|-------------------------------------------------------------------------|:-------------:|
| **B1**   | Omnisell gửi thông tin khách hàng sang WSale để tạo checklist bán       | [V]           |
| **B2**   | Omnisell cập nhật nhân viên được phân công vào checklist trên WSale     | [V]           |
| **B3**   | Omnisell kiểm tra trạng thái checklist trên WSale (đã nhận tư vấn chưa) | [V]           |
| **A1**   | WSale báo về Omnisell khi user vào tư vấn, tắt tính năng unicast        | [V]           |
| **A2**   | WSale lấy thông tin chi tiết đơn hàng, load chính sách, show cho user   | [V]           |
| **A4**   | WSale cập nhật kết quả tư vấn về Omnisell                               | [V]           |
| **SOP**  | API SOP cung cấp cho Wsale gửi Noti                                     | [V]           |

## 6. Mapping API với Chức Năng & Function Code

| API   | Chức năng liên quan                              | Ghi chú |
|-------|--------------------------------------------------|---------------------------------------------------------------------------|
| B1    | Tạo checklist bán từ Omnisell                    | Omnisell gọi                                                              |
| B2    | Cập nhật nhân viên phân công vào checklist       | Omnisell gọi                                                              |
| B3    | Kiểm tra trạng thái checklist                    | Omnisell gọi                                                              |
| A1    | Báo user vào tư vấn, tắt unicast                 | Gọi trực tiếp từ Client thông qua công API Wsale                          |
| A2    | Lấy thông tin chi tiết đơn hàng, load chính sách | Tick hợp vào API GetServicePortal để đồng bộ về 1 luồng trên Client       |
| A4    | Cập nhật kết quả tư vấn về Omnisell              | Check và cập nhật trong API UpdatePortal để đồng bộ về 1 luồng trên client|

## Các Task Triển Khai Theo Flow

### 1. Nhận data về WSale
- [V] WSale ghi nhận nhân viên tư vấn và gửi notification lên SOP kèm link redirect

### 2. Notification & Tư Vấn Trên SOP
- [V] Tích hợp API A1: WSale gọi Omnisell báo user vào tư vấn, tắt tính năng unicast
- [V] Xử lý trường hợp API A1 trả về false: hiển thị thông báo "Không hợp lệ"
- [V] Kiểm tra checklist source = 22 (Omnisell) và target = 0 khi vào từ màn hình Khách hàng phân phối

### 3. Tư Vấn & Cập Nhật Kết Quả
- [V] Tích hợp API A2: WSale lấy thông tin chi tiết đơn hàng, load chính sách, show cho user
- [V] Edit chức năng cập nhật kết quả tư vấn trên WSale
- [V] Tích hợp API A4: WSale cập nhật kết quả tư vấn về Omnisell
- [V] Recheck phần tick hẹn triển khai PTC
- [V] Kiểm tra luồng đã có đơn hàng thì hiển thị hết các tab để qua tick hẹn triển khai được

### 4. Kiểm Tra Trạng Thái Checklist
- [V] Cung cấp API B3: Omnisell kiểm tra trạng thái checklist trên WSale