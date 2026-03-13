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
- HotRequest_Bổ sung check trùng đơn hàng Online (24/2-02/3): 100% [DONE] - Backend
- HotRequest_Bổ sung nhận diện KHTN từ bán thêm dịch vụ CAM nguồn Hi-FPT (Upgrade ghi nhận thông tin Order_Type)  26/02/2026 - 04/03/2026: 100% [DONE] - Backend
- HotRequest_Bổ sung nhận diện KHTN từ app FPT Play (Upgrade ghi nhận thông tin Order_SA) : 26/02/2026 - 04/03/2026: 80% [IN PROGRESS] - Backend
- Tổ chức lại bộ KQTV chung giữa các kênh SOP-WSale-OmniSell (29/1-11/2): 100% [DONE] - Backend
- Bổ sung API báo cáo cho SOP (12/2-13/2): 100% [DONE] - Backend
- Bổ sung TrackingId nhận diện chiến dịch từ bóng chat SOP (27/2-4/3): 100% [DONE] - Backend
- Điều chỉnh API AM mới thay thế cụm API Access Trade: 100% [DONE] - Backend
- Cung cấp API KHTN cho FoxOne (23/2-4/3): 10% [IN PROGRESS] - API, Backend
- Tiếp nhận KHTN từ SR ghi nhận vào SR nonSHD (KHTN) (4/3-17/3): 0% [IN PROGRESS] - Backend, Database
- Thay đổi thông tin địa chỉ HCQG (18/3-31/3): 0% [IN PROGRESS] - Backend, Database
- Refactor cụm BE (nghiệp vụ & kiến trúc): [PENDING] - Infrastructure
- Bổ sung mã màu + mess chi tiết theo template nhận KHTN: [PENDING]
- Custom lại phần lưu các utm cho MKT: [PENDING]
- Chuẩn hóa event schema & logging: [PENDING]
- Auto tạo KHTN kênh Social: Zalo Mini app, Facebook: [PENDING]
- Bổ sung check trùng Checklist tư vấn Telesales: [PENDING]
5. Việc đã hoàn thành 
- Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA) [DONE]
- Bổ sung TrackingId nhận diện chiến dịch từ bóng chat SOP [DONE]
- HotRequest_Bổ sung check trùng đơn hàng Online [DONE]
- HotRequest_Bổ sung nhận diện KHTN từ bán thêm dịch vụ CAM nguồn Hi-FPT (Upgrade ghi nhận thông tin Order_Type) [DONE]
- Tổ chức lại bộ KQTV chung giữa các kênh SOP-WSale-OmniSell (29/1-11/2) [DONE]
- Bổ sung API báo cáo cho SOP (12/2-13/2) [DONE]
- Điều chỉnh API AM mới thay thế cụm API Access Trade [DONE]
6. Công việc 2 tuần tiếp (16/3 - 27/3)
- Tuần 3 (16/3 - 20/3):
    - Phân tích Custom lại phần lưu các utm cho MKT - bắt đầu
    - Nghiên cứu giải pháp cho bài toán Auto tạo KHTN kênh Social: Zalo Mini app, Facebook
    - Hoàn thành nhận diện KHTN từ app FPT Play (80% → 100%)
    - Triển khai API KHTN cho FoxOne (10% → 50%)
    - Hoàn thành tiếp nhận KHTN từ SR ghi nhận vào SR nonSHD
- Tuần 4 (23/3 - 27/3):
    - Hoàn thành cung cấp API KHTN cho FoxOne (50% → 100%)
    - Refactor cụm BE (bắt đầu triển khai giai đoạn 1)    
    - Chuẩn bị hoàn thành thay đổi thông tin địa chỉ HCQG (target: 31/3 release)    
    - Bổ sung check trùng Checklist tư vấn Telesales
    - Chuẩn hóa event schema & logging - bắt đầu triển khai
7. Vấn đề
- Resource dev chưa đáp ứng đủ với số lượng task hiện tại
