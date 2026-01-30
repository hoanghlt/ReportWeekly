# 📁 ReportWeekly - Folder Structure

## Cấu Trúc Thư Mục Tổ Chức

```
ReportWeekLy/
├── 📂 Reports/
│   ├── Report_05-01_to_09-01.md
│   ├── Report_ver_1.5.md
│   ├── Report_30-1_next.md
│   └── [Các file báo cáo khác]
│
├── 📂 Tasks/
│   ├── Task.md
│   ├── Task0307-11.md
│   ├── Task1014-11.md
│   ├── Task1317-10.md
│   ├── Task1519-9.md
│   ├── Task1721-11.md
│   ├── Task2024-10.md
│   ├── Task2226-9.md
│   ├── Task2428-11.md
│   ├── Task2529-9.md
│   ├── Task2731-10.md
│   ├── Task2903-10.md
│   ├── TaskWsale.md
│   └── [Các file công việc khác]
│
├── 📂 Documentation/
│   ├── CONTEXT_HTML_GENERATION.md    (Hướng dẫn chi tiết cách tạo HTML)
│   └── RULES_DEFINED.md              (20 Rules + Validation + Checklist)
│
├── 📂 HTML_Output/
│   └── WSale.html                    (Dashboard HTML được generate)
│
├── 📂 Reference/
│   └── FlowWSaleOmnisellSOP.md       (Tài liệu tham khảo)
│
└── README.md                          (File này)
```

---

## 📋 Giải Thích Chi Tiết Mỗi Folder

### 📂 Reports/
**Mục đích:** Lưu trữ các file báo cáo hàng tuần/hàng tháng

- `Report_05-01_to_09-01.md` - Báo cáo từ 05/01 đến 09/01
- `Report_ver_1.5.md` - Báo cáo Version 1.5 (WSale)
- `Report_30-1_next.md` - Báo cáo tiếp theo từ 30/01

**Cấu trúc file:**
```markdown
1. Version hiện tại
2. Mục tiêu
3. Thời gian release
4. Tiến độ
5. Việc đã hoàn thành
6. Công việc 2 tuần tiếp
7. Vấn đề
```

**Khi cần:** Viết report mới, hãy tạo file ở đây theo naming convention `Report_[DATE].md`

---

### 📂 Tasks/
**Mục đích:** Lưu trữ các file chi tiết công việc/task hàng ngày

- `Task.md` - Template hoặc task chính
- `Task0307-11.md` - Task từ 03/07 đến 11
- `Task2903-10.md` - Task từ 29/03 đến 10/10
- `TaskWsale.md` - Task liên quan WSale

**Khi cần:** Chi tiết từng task/sprint, tạo file ở đây

---

### 📂 Documentation/
**Mục đích:** Tài liệu hướng dẫn và rule định sẵn

**Các file:**
1. **CONTEXT_HTML_GENERATION.md**
   - Phân tích chi tiết cách HTML dashboard hoạt động
   - Cấu trúc dữ liệu JavaScript
   - Hướng dẫn từng bước tạo report
   - Template tái sử dụng

2. **RULES_DEFINED.md**
   - 20 Rules chính
   - Validation Rules
   - Priority Rules
   - Common Pitfalls + cách tránh
   - Calculation Examples
   - Customization Checklist

**Khi cần:** 
- Viết report mới? → Tham khảo **RULES_DEFINED.md**
- Hiểu cách tạo HTML? → Đọc **CONTEXT_HTML_GENERATION.md**

---

### 📂 HTML_Output/
**Mục đích:** Lưu trữ file HTML được generate từ report markdown

- `WSale.html` - Dashboard HTML cho WSale project (Version 1.5)

**Khi cần:**
- Mở file `.html` trong browser để xem dashboard
- Có thể edit template này để generate HTML khác
- Lưu file HTML output mới ở đây

---

### 📂 Reference/
**Mục đích:** Tài liệu tham khảo, flow diagram, hướng dẫn

- `FlowWSaleOmnisellSOP.md` - Flow SOP cho Omni-Sell

**Khi cần:** Cần tham khảo quy trình hoặc flow tổng quan

---

## 🚀 Quick Start Guide

### Tạo Report Mới
1. Tạo file `Report_[DATE_RANGE].md` trong **Reports/** folder
2. Tuân thủ cấu trúc trong **RULES_DEFINED.md**
3. Sau khi viết, có thể generate HTML từ template WSale

### Thêm Task Mới
1. Tạo file `Task[DATE_RANGE].md` trong **Tasks/** folder
2. Chi tiết công việc, deadline, responsible

### Generate HTML Dashboard
1. Đọc **CONTEXT_HTML_GENERATION.md**
2. Chuẩn bị dữ liệu từ report markdown
3. Update config + projectData trong HTML template
4. Save HTML ở **HTML_Output/** folder

### Tìm Hiểu Rule
1. Mở **RULES_DEFINED.md**
2. Tìm rule cần thiết
3. Kiểm tra Validation Rules + Common Pitfalls

---

## 📊 Naming Convention

### Reports
```
Report_[START_DATE]-[END_DATE]_[VERSION].md
Ví dụ: Report_05-01_to_09-01.md, Report_30-1_next.md
```

### Tasks
```
Task[DATE_RANGE]-[CATEGORY].md
Ví dụ: Task0307-11.md, TaskWsale.md
```

### HTML Output
```
[PROJECT_NAME].html
Ví dụ: WSale.html
```

---

## 🔧 Maintenance

### Hàng tuần
- Cập nhật file Report mới trong **Reports/**
- Cập nhật Task mới trong **Tasks/**

### Hàng tháng
- Archive old reports/tasks (optional)
- Review RULES_DEFINED.md nếu cần update

### Hàng quý
- Update CONTEXT_HTML_GENERATION.md nếu có thay đổi cách làm
- Kiểm tra lại cấu trúc folder

---

## 💡 Tips

1. **Luôn tuân thủ RULES_DEFINED.md** - Đảm bảo consistent format
2. **Tham khảo file cũ** - Dùng report cũ làm template
3. **Check HTML output** - Xem HTML output để verify dữ liệu
4. **Đánh giá severity chính xác** - Tránh underestimate issues
5. **Cập nhật progress regularly** - Không chờ đến cuối report mới update

---

## 📝 File Count

- **Reports:** 3+ files
- **Tasks:** 13+ files
- **Documentation:** 2 files
- **HTML Output:** 1 file
- **Reference:** 1 file
- **Total:** 20+ files (organized & easy to find)

---

**Last Updated:** 30/01/2026
**Maintained by:** Team
**Version:** 1.0
