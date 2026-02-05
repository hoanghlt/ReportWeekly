OmniSell
1. Version hiện tại: 2.2
2. Mục tiêu 
- Refactor cụm BE (nghiệp vụ & kiến trúc)
- Tổ chức lại bộ KQTV chung giữa các kênh SOP-WSale-OmniSell
- Bổ sung mã màu + mess chi tiết theo template nhận KHTN
- Custom lại phần lưu các utm cho MKT
- Chuẩn hóa event schema & logging
- Auto tạo KHTN kênh Social: Zalo Mini app, Facebook
- Bổ sung check trùng Đơn hàng Online
- Bổ sung check trùng Checklist tư vấn Telesales
- Cung cấp API KHTN cho FoxOne
- Tiếp nhận KHTN từ SR ghi nhận vào SR nonSHD (KHTN)
- Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA)
- Thay đổi thông tin địa chỉ HCQG
- Bổ sung API báo cáo data phân phối cho SOP và thêm TrackingId nhận biết chiến dịch
3. Thời gian release
- Staging - 2.2: 31/03/2026
4. Tiến độ
- Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA) (26/1-28/1): 100% [DONE] - Backend
- Tổ chức lại bộ KQTV chung giữa các kênh SOP-WSale-OmniSell (29/1-11/2): 70% [IN PROGRESS] - Backend
- Bổ sung API báo cáo data phân phối cho SOP và thêm TrackingId nhận biết chiến dịch (12/2-13/2): 0% [IN PROGRESS] - Backend
- Cung cấp API KHTN cho FoxOne (23/2-4/3): 10% [IN PROGRESS] - API, Backend
- Tiếp nhận KHTN từ SR ghi nhận vào SR nonSHD (KHTN) (4/3-17/3): 0% [IN PROGRESS] - Backend, Database
- Thay đổi thông tin địa chỉ HCQG (18/3-31/3): 0% [IN PROGRESS] - Backend, Database
- Refactor cụm BE (nghiệp vụ & kiến trúc): [PENDING] - Infrastructure
- Bổ sung mã màu + mess chi tiết theo template nhận KHTN: [PENDING]
- Custom lại phần lưu các utm cho MKT: [PENDING]
- Chuẩn hóa event schema & logging: [PENDING]
- Auto tạo KHTN kênh Social: Zalo Mini app, Facebook: [PENDING]
- Bổ sung check trùng Đơn hàng Online: [PENDING]
- Bổ sung check trùng Checklist tư vấn Telesales: [PENDING]
5. Việc đã hoàn thành 
- Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA) [DONE]
6. Công việc 2 tuần tiếp (1/2 - 7/2)
- Tuần 1 (1/2 - 7/2):
    - Tổ chức lại bộ KQTV chung: Phân tích yêu cầu, thiết kế database, chuẩn hóa schema
    - Định nghĩa cấu trúc dữ liệu KQTV cho các kênh SOP-WSale-OmniSell
    - Chuẩn bị phương án integration giữa các kênh
    - Hỗ trợ bổ sung luồng xử lý phân phối cho FMI
- Tuần 2 (8/2 - 14/2):
    - Bổ sung ghi nhận TrackingID đơn hàng từ SOP, Bóng chat
    - Viết API báo cáo data phân phối cho SOP
    - Tổ chức lại bộ KQTV chung: Tiếp tục phát triển logic xử lý
    - Chuẩn bị kế hoạch chi tiết cho API KHTN FoxOne (deadline 4/3)
    - Review & test các thay đổi KQTV
7. Vấn đề
- Resource dev chưa đáp ứng đủ với số lượng task hiện tại
- Chưa được hỗ trợ tích hợp từ một số service external
