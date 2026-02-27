# RULES TỔNG HỢP TỪ PHÂN TÍCH HTML DASHBOARD

## 📋 RULES CHÍNH

### Rule 1: Cấu Trúc File Markdown Bắt Buộc
```
1. Version hiện tại: [VERSION]
2. Mục tiêu
   - Mục tiêu 1
   - Mục tiêu 2
   ...
3. Thời gian release
   - Stage/Environment: [DATE]
4. Tiến độ
   - Task 1: [STATUS hoặc %]
   - Task 2: [STATUS hoặc %]
5. Việc đã hoàn thành
   - Hoàn thành 1
6. Công việc 2 tuần tiếp
   [Danh mục 1]
       - Item 1
       - Item 2
   [Danh mục 2]
       - Item 1
7. Vấn đề
   - Vấn đề 1
   - Vấn đề 2
```

---

### Rule 2: Status Mapping
| Markdown | JavaScript | Color | Icon |
|----------|-----------|-------|------|
| [DONE] | "DONE" | #10b981 (Green) | ✓ Checkmark |
| [IN PROGRESS] | "IN PROGRESS" | #f59e0b (Orange) | ⏱ Clock |
| Không có status | "PENDING" | #6b7280 (Gray) | - |

---

### Rule 3: Task Grouping (5 Nhóm Chuẩn)
```javascript
{
  "Infrastructure": { bg: "#3b82f620", color: "#3b82f6" },   // Blue
  "Marketing": { bg: "#10b98120", color: "#10b981" },         // Green
  "Features": { bg: "#f59e0b20", color: "#f59e0b" },          // Orange
  "Automation": { bg: "#8b5cf620", color: "#8b5cf6" },        // Purple
  "Development": { bg: "#ec489920", color: "#ec4899" }        // Pink
}
```

**Rule 3a: Cách Gán Group**
- Từ tên task hoặc context, xác định group phù hợp
- Nếu không phù hợp, có thể thêm group mới với cặp màu (bg, color)

---

### Rule 4: Version Configuration
```javascript
defaultConfig = {
  project_name: "Tên dự án",              // Bắt buộc
  project_id: "Mã viết tắt",              // Bắt buộc (2-3 ký tự)
  version: "X.Y",                         // Từ mục 1
  release_date: "DD/MM/YYYY",             // Từ mục 3
  iteration_goal: "Mô tả mục tiêu",       // Tóm tắt từ mục 2
  progress_label: "Tiến độ tổng thể",
  version_label: "Version",
  deadline_label: "Ngày Release",
  issues_label: "Vấn đề"
}
```

---

### Rule 5: Overall Progress Calculation
```javascript
// Công thức tính
overallProgress = Math.round((doneTasks / totalTasks) * 100)

// Quy tắc đếm
- doneTasks = Số mainTasks có status === "DONE"
- totalTasks = Số mainTasks tổng cộng
- Làm tròn đến số nguyên gần nhất
```

---

### Rule 6: Task Progress Field
```javascript
// Có 3 định dạng cho task.progress:
1. Phần trăm: "80%"           // Số thực hiện theo %
2. Mô tả: "Phân tích"         // Mô tả giai đoạn
3. Trạng thái: "100%" (DONE) / "0%" (PENDING)

// Lưu ý: Progress field KHÔNG nhất thiết là % của overall
// Mỗi task có progress riêng biệt
```

---

### Rule 7: Issue Severity Levels
```javascript
{
  severity: "High",           // Color: #ef4444 (Red)
  severity: "Medium",         // Color: #f59e0b (Orange)
  severity: "Low"             // Color: #10b981 (Green)
}

// Rule 7a: Gán Severity
- High: Blocking, critical, yêu cầu hỗ trợ ngay
- Medium: Important, ảnh hưởng đến timeline
- Low: Minor, không gây chặn công việc
```

---

### Rule 8: Cấu Trúc nextTwoWeeks
```javascript
// Phải là array của objects
nextTwoWeeks: [
  {
    category: "Tên danh mục",    // Tiêu đề nhóm
    items: [                      // Array string
      "Chi tiết 1",
      "Chi tiết 2",
      "Chi tiết 3"
    ]
  },
  {
    category: "Danh mục 2",
    items: [...]
  }
]

// Rule 8a: Số lượng category
- Tối thiểu 1, tối đa 4 category
- Mỗi category nên có 2-5 items
```

---

### Rule 9: mainTasks Structure
```javascript
mainTasks: [
  {
    title: "Tên task (bắt buộc)",
    status: "DONE|IN PROGRESS|PENDING",  // (bắt buộc)
    progress: "80%|Mô tả|etc",           // (bắt buộc)
    group: "Infrastructure|...|Custom"   // (bắt buộc)
  }
]

// Rule 9a: Số lượng task
- Tối thiểu 3, tối đa 10 tasks
- Tính toán: totalTasks = length của array này
```

---

### Rule 10: Issues Structure
```javascript
issues: [
  {
    title: "Tiêu đề vấn đề",              // (bắt buộc)
    desc: "Mô tả chi tiết, nguyên nhân",  // (bắt buộc)
    severity: "High|Medium|Low",          // (bắt buộc)
    icon: "alert"                         // Fixed value
  }
]

// Rule 10a: Số lượng issue
- Tối thiểu 1, tối đa 5 issues
- Mô tả nên chi tiết (2-3 câu)
```

---

### Rule 11: Color Customization
```javascript
// Có thể tùy chỉnh
background_color: "#ffffff",
surface_color: "#f8fafc",
text_color: "#1e293b",
primary_action: "#6366f1",        // Gradient start
secondary_action: "#8b5cf6",      // Gradient end

// Rule 11a: Color Rules
- Đủ contrast với background (WCAG AA)
- Gradient colors nên là shade của nhau
- Text color nên dark trên light background
```

---

### Rule 12: Font & Typography
```javascript
font_family: "Space Grotesk",    // Default, có thể thay
font_size: 16                    // Base size in px

// Rule 12a: Font Size Multipliers
- Heading: baseSize * 1.5 = 24px
- Subheading: baseSize * 1.25 = 20px
- Body: baseSize * 1 = 16px
- Small: baseSize * 0.85 = 13px
- Tiny: baseSize * 0.65 = 10px
```

---

### Rule 13: Tab Navigation Structure
```javascript
// 4 tabs cố định
1. Dashboard    - Home view (Stats + Progress)
2. Tasks        - Task list view
3. Next Plan    - Roadmap view (nextTwoWeeks)
4. Issues       - Issues view
```

---

### Rule 14: Dashboard Stats Cards
```javascript
// 4 thẻ thống kê bắt buộc (trong renderDashboard)
1. Progress: [overallProgress]%
2. Version: [version]
3. Deadline: [release_date]
4. Status: On Track / At Risk / Blocked (auto-calculated)
```

---

### Rule 15: Responsive Breakpoints
```css
/* Mobile First */
xs: < 640px   - 1 column layout
md: ≥ 768px   - 2-4 columns

/* Grid Rules */
Stats cards:    grid-cols-1 md:grid-cols-4
Activity grid:  grid-cols-1 md:grid-cols-2
Task list:      grid-cols-1 (single column)
```

---

### Rule 16: Animation & Transitions
```css
/* FadeIn animation */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
duration: 0.5s
easing: ease-out

/* SlideIn animation */
@keyframes slideIn {
  from { opacity: 0; transform: translateX(-20px); }
  to { opacity: 1; transform: translateX(0); }
}
duration: 0.4s

/* Hover effects */
card-hover: translateY(-4px) với box-shadow
tab-button: translateY(-2px)
group-badge: scale(1.05)
```

---

### Rule 17: Progress Bar Styling
```css
/* Background */
background: #f3f4f6 (light gray)
height: 16px
border-radius: 9999px

/* Fill */
background: linear-gradient(90deg, primary_action → secondary_action)
width: overallProgress%
transition: width 0.8s cubic-bezier(0.4, 0, 0.2, 1)
```

---

### Rule 18: Data Mapping từ Markdown
```
Mục 1 (Version) → config.version
Mục 2 (Mục tiêu) → mainTasks[].title + iteration_goal
Mục 3 (Thời gian) → config.release_date
Mục 4 (Tiến độ) → mainTasks[].progress + overallProgress
Mục 5 (Hoàn thành) → Determine status = "DONE"
Mục 6 (2 tuần) → nextTwoWeeks[].category/items
Mục 7 (Vấn đề) → issues[].title/desc/severity
```

---

### Rule 19: Icon Usage
```javascript
// Tất cả icons là SVG inline
// Không dùng image files
// Icon sizing:
- Stats cards: 24x24
- Tab buttons: 16-18x18
- Status badges: 18x18
- Section headers: 32x32
```

---

### Rule 20: Label Customization
```javascript
// 4 label có thể tùy chỉnh
progress_label: "Tiến độ tổng thể"      // Stats card
version_label: "Version"                 // Stats card
deadline_label: "Ngày Release"           // Stats card
issues_label: "Vấn đề"                   // Issues tab

// Các label khác là fixed trong code
```

---

### Rule 21: Last Updated Field (Mandatory for public/index.html)
```
**Mục đích:** Hiển thị ngày cập nhật cuối cùng của dashboard chính
**Vị trí:** Footer của public/index.html (file chính công khai)
**Format:** 📅 Last Updated: Month DD, YYYY (tiếng Anh)
**Quy tắc:**
- PHẢI cập nhật LIÊN TỤC khi có thay đổi dữ liệu từ Report files
- Sử dụng định dạng ngày: Month DD, YYYY (ví dụ: February 27, 2026)
- Luôn sử dụng thời gian hiện tại (today/now) khi update dữ liệu
- Phù hợp cho tất cả các dự án (WSale, OmniSell, v.v.)
- **KHÔNG** thêm rule này vào file Agents.md

**Ví dụ cập nhật:**
- Report WSale được update → Cập nhật Last Updated thành hôm nay
- Report OmniSell được update → Cập nhật Last Updated thành hôm nay
- Nếu cả 2 report được update → Vẫn là 1 Last Updated chung (ngày gần nhất)

**Implementation:**
```html
<p>📅 Last Updated: February 27, 2026</p>
```

**Nguyên nhân:** Giúp user biết thông tin dashboard có mới hay không, tránh dùng dữ liệu cũ.
```

---

## 🔍 VALIDATION RULES

### Validation Rule 1: Task Title
- ✅ Không quá 120 ký tự
- ✅ Phải có nội dung có ý nghĩa
- ✅ Không được để trống

### Validation Rule 2: Group Name
- ✅ Phải match một trong 5 group hoặc custom
- ✅ Phải có cặp màu định sẵn (bg, color)

### Validation Rule 3: Date Format
- ✅ Luôn DD/MM/YYYY
- ✅ Phải là ngày hợp lệ

### Validation Rule 4: Percentage
- ✅ Nếu dùng %, phải là 0-100
- ✅ Format: "XX%"

### Validation Rule 5: Array Length
- ✅ mainTasks: 3-10 items
- ✅ nextTwoWeeks: 1-4 categories
- ✅ issues: 1-5 items

---

## 🎯 PRIORITY RULES

### Priority Rule 1: Dữ Liệu > Giao Diện
- Ưu tiên chính xác dữ liệu trước
- Giao diện là phụ

### Priority Rule 2: Overall Progress
- Nếu có conflict, doneTasks/totalTasks quyết định

### Priority Rule 3: Status Priority
- DONE > IN PROGRESS > PENDING

### Priority Rule 4: Severity Priority (Issues)
- High > Medium > Low

---

## ⚠️ COMMON PITFALLS

### Pitfall 1: Sai Progress Calculation
❌ Lấy % từ individual progress field
✅ Tính từ số DONE tasks / total tasks

### Pitfall 2: Lỗi Status Mapping
❌ [Done], [done], [COMPLETED]
✅ [DONE], [IN PROGRESS], [PENDING]

### Pitfall 3: Group Not Found
❌ Dùng group không có trong groupColors
✅ Định sẵn group hoặc thêm vào groupColors

### Pitfall 4: Date Format
❌ 2026-01-30, 01/30/2026
✅ 30/01/2026 (DD/MM/YYYY)

### Pitfall 5: Empty Array
❌ mainTasks: [], issues: []
✅ Luôn có ít nhất 1-3 items

### Pitfall 6: Long Text
❌ Task title > 120 ký tự
✅ Keep title concise, dùng desc cho details

---

## 📊 CALCULATION EXAMPLES

### Example 1: Overall Progress
```
Input: 1 DONE, 5 total
Calculation: (1 / 5) * 100 = 20%
Rounding: 20
Output: overallProgress = 20
```

### Example 2: Status Counts
```
Input: mainTasks = [
  { status: "DONE" },
  { status: "DONE" },
  { status: "IN PROGRESS" },
  { status: "IN PROGRESS" },
  { status: "PENDING" }
]
doneTasks = 2
inProgressTasks = 2
pendingTasks = 1
totalTasks = 5
```

---

## 🔧 CUSTOMIZATION CHECKLIST

- [ ] project_name đã đặt
- [ ] project_id đã đặt (2-3 ký tự)
- [ ] version đã cập nhật
- [ ] release_date đúng format
- [ ] iteration_goal mô tả chính xác
- [ ] mainTasks có 3-10 items
- [ ] Mỗi task có group phù hợp
- [ ] Status mapping chính xác
- [ ] nextTwoWeeks có 1-4 categories
- [ ] issues có 1-5 items
- [ ] Severity gán đúng (High/Medium/Low)
- [ ] Overall progress calculated
- [ ] Colors pass contrast check
- [ ] Font size readable
- [ ] Responsive tested (mobile/tablet/desktop)

---

**Tài liệu này chứa đầy đủ rules để tạo report HTML từ file Markdown.**
**Tuân thủ các rules này để đảm bảo output chính xác và đẹp mắt.**
