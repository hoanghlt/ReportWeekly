# Context: Cách Tạo Report & HTML Dashboard Từ File Markdown

**Updated:** 27/02/2026 - Support cho WSale, OmniSell, FCP và các dự án khác

## I. QUY TRÌNH TẠO REPORT CHO DỰ ÁN MỚI

### Bước 1: Lấy Thông Tin từ User

Hỏi người dùng những thông tin sau:

```
1. Tên dự án (Project Name)
2. Mã viết tắt (Project ID) - 2-3 ký tự
3. Danh sách backlog/mục tiêu (12 - 20 cái)
4. Timeline dự kiến:
   - Release date staging
   - Release date production
   - Quý nào / Tháng nào
5. Backlog ưu tiên + timeline cụ thể (5-7 cái)
6. Backlog pending (không làm ngay)
7. Tiến độ của từng backlog ưu tiên
8. Công việc 2 tuần tiếp theo (có thể infer từ timeline)
9. Risk/Issues (có thể dùng default giống WSale)
```

### Bước 2: Suy Luận Deadline

- Nếu user nói "Quý 1 2026" → Deadline = 31/03/2026
- Nếu user nói "Tháng 2 2026" → Deadline = 28/02/2026
- Nếu user nói "Tháng 3 2026" → Deadline = 31/03/2026
- Etc.

### Bước 3: Tổ Chức Backlog

```
Backlog ưu tiên (5-7 cái):
- Có timeline cụ thể
- Có tiến độ % hoặc status
- Sẽ hiển thị trong Dashboard

Backlog khác:
- Chưa có timeline hoặc low priority
- Status = PENDING
- Liệt kê trong mục Tiến độ

Backlog Pending (không làm):
- Status = PENDING / Skipped
- Ghi chú tại sao pending
```

### Bước 4: Tính Overall Progress

```javascript
overall% = (DONE tasks / Total prioritized tasks) × 100

Ví dụ OmniSell:
- 1 DONE / 6 prioritized = 17%
- 5 IN PROGRESS
- 7 PENDING
```

### Bước 5: Xây Dựng Công Việc 2 Tuần

```
Dựa vào timeline backlog:
- Nếu backlog deadline < 14 ngày, sẽ nằm trong 2 tuần tiếp
- Chia thành Tuần 1 (7 ngày) và Tuần 2 (7 ngày)
- Thêm chi tiết cụ thể từ backlog
```

---

## II. PHÂN TÍCH VỀ LOGIC VÀ CÁCH LÀM

### 1. Cấu Trúc Dữ Liệu trong JavaScript

File HTML sử dụng object `projectData` để lưu trữ toàn bộ dữ liệu từ file Markdown:

```javascript
const projectData = {
  overallProgress: 17,           // % tiến độ tổng thể (từ mục Tiến độ)
  totalTasks: 6,                  // Tổng số nhiệm vụ chính (ưu tiên)
  doneTasks: 1,                   // Số nhiệm vụ hoàn thành
  
  mainTasks: [
    {
      title: "Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA)",  // Từ backlog ưu tiên
      status: "DONE",                                   // DONE, IN PROGRESS, PENDING
      progress: "100%",                                 // Từ tiến độ
      group: "Integration"                              // Phân loại nhóm công việc
    },
    {
      title: "Tổ chức lại bộ KQTV chung",
      status: "IN PROGRESS",
      progress: "0%",
      group: "Backend"
    },
    // ... các task khác
  ],
  
  nextTwoWeeks: [
    {
      category: "Tuần 1 (30/1 - 5/2)",                 // Từ mục "Công việc 2 tuần tiếp"
      items: [
        "Tổ chức lại bộ KQTV chung: Phân tích yêu cầu",
        "Định nghĩa cấu trúc dữ liệu KQTV",
        "Chuẩn bị phương án integration"
      ]
    }
  ],
  
  issues: [
    {
      title: "Resource dev chưa đáp ứng đủ",           // Từ mục Vấn đề
      desc: "Đội ngũ phát triển hiện tại chưa đủ nguồn lực...",
      severity: "Medium",                               // High, Medium, Low
      icon: "alert"
    }
  ]
};
```

**Lưu ý:** 
- `totalTasks` = số backlog ưu tiên (có timeline cụ thể)
- `mainTasks` = array của các backlog ưu tiên
- Các backlog khác (PENDING) không tính vào overall%

### 2. Cấu Hình Mặc Định (defaultConfig)

Các thông tin cấu hình dự vào file Markdown:

```javascript
const defaultConfig = {
  background_color: "#ffffff",
  surface_color: "#f8fafc",
  text_color: "#1e293b",
  primary_action: "#6366f1",
  secondary_action: "#8b5cf6",
  
  project_name: "WSale Project",        // Từ tên file hoặc mục đầu tiên
  project_id: "WSL",                    // Mã viết tắt
  version: "1.5",                       // Từ mục Version
  release_date: "31/03/2026",           // Từ mục Thời gian release
  iteration_goal: "Mô tả mục tiêu...",  // Từ mục Mục tiêu (tóm tắt)
  
  progress_label: "Tiến độ tổng thể",
  version_label: "Version",
  deadline_label: "Ngày Release",
  issues_label: "Vấn đề",
  
  font_family: "Space Grotesk",
  font_size: 16
};
```

### 3. Phân Loại Nhóm (Group Colors)

Mỗi nhóm công việc có một màu sắc riêng. Các nhóm có thể custom dựa vào dự án:

**Nhóm Chuẩn (từ WSale & OmniSell):**

```javascript
const groupColors = {
  "Infrastructure": { bg: "#3b82f620", color: "#3b82f6" },     // Xanh dương
  "Marketing": { bg: "#10b98120", color: "#10b981" },           // Xanh lục
  "Features": { bg: "#f59e0b20", color: "#f59e0b" },            // Cam
  "Automation": { bg: "#8b5cf620", color: "#8b5cf6" },          // Tím
  "Development": { bg: "#ec489920", color: "#ec4899" },         // Hồng
  "Backend": { bg: "#3b82f620", color: "#3b82f6" },             // Xanh dương
  "Integration": { bg: "#f59e0b20", color: "#f59e0b" },         // Cam
  "Database": { bg: "#8b5cf620", color: "#8b5cf6" }             // Tím
};
```

**Cách Gán Group:**
- Dựa vào tính chất backlog
- OmniSell: "Backend", "Integration", "Database", "Analytics", etc.
- WSale: "Infrastructure", "Features", "Development", etc.
- Có thể thêm group mới nếu cần

### 4. Hệ Thống Tab Navigation

HTML có 4 tab chính tương ứng với các view khác nhau:

| Tab | Tên | Nội Dung | Function |
|-----|-----|---------|----------|
| 1 | Dashboard | Tổng quan KPI, tiến độ, hoạt động gần đây | `renderDashboard()` |
| 2 | Tasks | Danh sách tất cả nhiệm vụ chính | `renderTasks()` |
| 3 | Next Plan | Kế hoạch 2 tuần tiếp theo | `renderRoadmap()` |
| 4 | Issues | Danh sách các vấn đề và rủi ro | `renderIssues()` |

### 5. Quy Trình Render

1. **Khởi tạo**: `renderApp(config)` - Vẽ header + tabs
2. **Chuyển Tab**: `switchTab(tab)` → `updateTabStyles()` → `renderContent()`
3. **Render Nội Dung**: 
   - `renderDashboard()` - Stats cards + Progress + Recent activity
   - `renderTasks()` - Task list with group badges
   - `renderRoadmap()` - Next 2 weeks plan
   - `renderIssues()` - Issue list with severity

---

## II. MAPPING TỬ FILE MARKDOWN ĐẾN HTML

### Từ Markdown → JavaScript Object

| Mục trong Markdown | Mapping đến JavaScript | Ví Dụ |
|-------------------|----------------------|--------|
| **1. Version hiện tại** | `config.version` | "1.5" |
| **2. Mục tiêu** | `projectData.mainTasks[].title` + `config.iteration_goal` | Tên các task chính |
| **3. Thời gian release** | `config.release_date` | "31/03/2026" |
| **4. Tiến độ** | `projectData.mainTasks[].progress` + `projectData.overallProgress` | "80%", "33%" |
| **5. Việc đã hoàn thành** | `projectData.mainTasks[].status = "DONE"` | Filter tasks |
| **6. Công việc 2 tuần tiếp** | `projectData.nextTwoWeeks[]` | Categories + items |
| **7. Vấn đề** | `projectData.issues[]` | Title + desc + severity |

### Cách Xác Định Status

- **DONE**: Khi mục tiêu hoàn thành (có [DONE] trong markdown)
- **IN PROGRESS**: Khi đang thực hiện (có [IN PROGRESS] trong markdown)
- **PENDING**: Khi chưa bắt đầu (không có thông tin progress)

---

## III. ĐIỂM NỖI BẬT TRONG CÁCH LÀM

### ✅ Ưu Điểm

1. **Responsive Design**: Sử dụng Tailwind CSS grid (md:grid-cols-2, md:grid-cols-4) để responsive
2. **Animation**: FadeIn, SlideIn animations tạo trải nghiệm mượt mà
3. **Color System**: Gradient colors cho header, badge colors cho status
4. **Group Categorization**: Phân loại task theo nhóm (Infrastructure, Marketing, etc.)
5. **Dynamic Rendering**: Dữ liệu được tính toán động từ projectData
6. **Customizable Config**: Font, màu sắc, label đều có thể thay đổi qua config
7. **Visual Hierarchy**: Stats cards → Progress bar → Task list
8. **Icon Usage**: SVG icons inline cho tất cả các element
9. **Progress Tracking**: Hiển thị % hoàn thành cả tổng thể và từng task
10. **Mobile First**: Layout mobile-first với responsive breakpoints

### 📊 Logic Tính Toán

```javascript
// Tính tiến độ tổng thể từ các task
overallProgress = Math.round((doneTasks / totalTasks) * 100);

// Phân loại task theo status
doneTasks = mainTasks.filter(t => t.status === 'DONE').length;
inProgressTasks = mainTasks.filter(t => t.status === 'IN PROGRESS').length;

// Tính số task theo group
tasksByGroup = mainTasks.reduce((acc, task) => {
  acc[task.group] = (acc[task.group] || 0) + 1;
  return acc;
}, {});
```

### 🎨 Color Scheme Strategy

- **Primary Gradient**: Purple (#667eea → #764ba2) cho header
- **Status Colors**: 
  - Green (#10b981) = Hoàn thành
  - Orange (#f59e0b) = Đang thực hiện
  - Gray = Chưa bắt đầu
- **Group Colors**: 5 màu khác nhau cho 5 nhóm công việc

### 📱 Responsive Breakpoints

```css
- xs: Mobile (< 640px)
- md: Tablet (≥ 768px) - grid-cols-1 md:grid-cols-2, md:grid-cols-4
```

---

## V. TEMPLATE MARKDOWN SẠCH (COPY & PASTE)

```markdown
[ProjectName]
1. Version hiện tại: [VERSION]
2. Mục tiêu 
- [Mục tiêu 1]
- [Mục tiêu 2]
- [Mục tiêu 3]
3. Thời gian release
- Staging - [VERSION]: [DATE]
4. Tiến độ
- [Backlog 1 (dates)]: [%] [STATUS]
- [Backlog 2 (dates)]: [%] [STATUS]
- [Backlog 3 (dates)]: [%] [STATUS]
5. Việc đã hoàn thành 
- [DONE backlog]
6. Công việc 2 tuần tiếp
Tuần 1 ([DATE] - [DATE]):
    - [Chi tiết 1]
    - [Chi tiết 2]
Tuần 2 ([DATE] - [DATE]):
    - [Chi tiết 1]
    - [Chi tiết 2]
7. Vấn đề
- [Vấn đề 1]: [Mô tả]
- [Vấn đề 2]: [Mô tả]
```

---

## VI. CÔNG THỨC TÍNH TOÁN TIẾN ĐỘ

### Tiến Độ Tổng Thể (Overall Progress)
```
Overall % = (Số task DONE / Tổng số task ưu tiên) × 100

Ví dụ OmniSell:
- 1 DONE / 6 prioritized tasks = 17%
- Không tính backlog PENDING (7 cái) vào overall

Ví dụ WSale:
- 1 DONE / 5 prioritized tasks = 20%
```

### Tiến Độ Chi Tiết
- Mỗi task có `progress` field riêng
- Có thể là % (80%, 100%, 0%), mô tả (Phân tích), hoặc status

### Status Priority
1. DONE (100%)
2. IN PROGRESS (0-99%)
3. PENDING (chưa xác định)

---

## VII. VÍ DỤ THỰC TẾ TỬ CÁC DỰ ÁN

### Ví Dụ 1: WSale (Đã Có)

**File:** `Report_WSale_ver_1.5.md`

```
Overall Progress: 33% (1 DONE / 5 prioritized)
mainTasks:
1. Nâng cấp K8s (80%) - Infrastructure - IN PROGRESS
2. LDP V.VIP MKT (100%) - Marketing - DONE
3. LDP V.VIP Map (Phân tích) - Features - IN PROGRESS
4. Autocall (10%) - Automation - IN PROGRESS
5. Mobile SOP (Phân tích) - Development - IN PROGRESS

nextTwoWeeks:
- Tuần 1-2: Phân tích, phát triển, test
```

### Ví Dụ 2: OmniSell (Vừa Tạo)

**File:** `Report_OmniSell_ver_2.2.md`

```
Overall Progress: 17% (1 DONE / 6 prioritized)
mainTasks:
1. Nhận KHTN VIP 7 DKOL (100%) - Integration - DONE
2. Tổ chức lại KQTV (0%) - Backend - IN PROGRESS
3. Cung cấp API KHTN (10%) - Integration - IN PROGRESS
4. Tiếp nhận KHTN SR (0%) - Backend - IN PROGRESS
5. Thay đổi địa chỉ (0%) - Database - IN PROGRESS

Pending: 7 backlog (Refactor, Custom utm, Event schema, Auto KHTN, Check trùng x2, Bổ sung màu)

nextTwoWeeks:
- Tuần 1: Phân tích KQTV
- Tuần 2: Chuẩn bị API FoxOne
```

### Ví Dụ 3: NewProject (Template)

**File:** `Report_NewProject_ver_X.Y.md`

```
Overall Progress: X% (? DONE / ? prioritized)
mainTasks:
1. [Backlog ưu tiên 1] (%) - [Group] - [STATUS]
2. [Backlog ưu tiên 2] (%) - [Group] - [STATUS]
...

Pending: [số backlog pending]

nextTwoWeeks:
- Tuần 1: [Chi tiết]
- Tuần 2: [Chi tiết]
```

---

## VIII. TEMPLATE ĐỂ TÁI SỬ DỤNG

### ProjectData Template

```javascript
const projectData = {
  overallProgress: [TÍNH TOÁN],
  totalTasks: [SỐ LƯỢNG],
  doneTasks: [SỐ LƯỢNG],
  mainTasks: [
    {
      title: "[TỪ MỤC TIÊU]",
      status: "[DONE|IN PROGRESS|PENDING]",
      progress: "[%|MÔ TẢ]",
      group: "[NHÓM CÔNG VIỆC]"
    }
  ],
  nextTwoWeeks: [
    {
      category: "[DANH MỤC]",
      items: ["[CHI TIẾT 1]", "[CHI TIẾT 2]"]
    }
  ],
  issues: [
    {
      title: "[TIÊU ĐỀ]",
      desc: "[MÔ TẢ CHI TIẾT]",
      severity: "[High|Medium|Low]"
    }
  ]
};
```

### Config Template

```javascript
const defaultConfig = {
  project_name: "[TÊN DỰ ÁN]",
  project_id: "[MÃ VIẾT TẮT]",
  version: "[VERSION]",
  release_date: "[NGÀY]",
  iteration_goal: "[MỤC TIÊU CHÍNH]",
  // ... các field khác giữ nguyên
};
```

---

## VII. CHIẾN LƯỢC TỐI ƯU HÓA

### Hiệu Suất
- Dùng `template literals` thay vì DOM manipulation
- CSS transitions thay vì JavaScript animations
- SVG inline cho icons (không load ảnh)

### Bảo Trì
- Tách dữ liệu (projectData) khỏi giao diện (render functions)
- Dùng config object centralized
- Function `renderX()` độc lập cho mỗi view

### UX
- Tab navigation immediate feedback
- Card hover animations
- Color coding cho status/severity
- Responsive grid layout

---

## VIII. NOTES QUAN TRỌNG

1. **Status Mapping**: Markdown [DONE] → JavaScript "DONE"
2. **Progress Calculation**: Cần tính chính xác từ số tasks hoàn thành
3. **Group Assignment**: Cần xác định đúng group cho mỗi task
4. **Severity Levels**: Cao (Red) → Medium (Orange) → Low (Green)
5. **Date Format**: Theo format DD/MM/YYYY
6. **Responsive**: Luôn test trên mobile, tablet, desktop
7. **Color Contrast**: Đảm bảo readable trên tất cả background

---

## IX. QUICK CHECKLIST TẠO REPORT MỚI

**Khi user cung cấp backlog cho dự án mới:**

- [ ] **1. Parse Backlog**
  - [ ] Sắp xếp ưu tiên (5-7 backlog có timeline)
  - [ ] Phân loại pending (chưa confirm)

- [ ] **2. Hỏi Thông Tin**
  - [ ] Tên dự án + Project ID
  - [ ] Version number
  - [ ] Quý/Tháng release → Suy luận deadline
  - [ ] Tiến độ từng backlog ưu tiên (%)
  - [ ] Risk/Issue (nếu khác default)
  - [ ] Công việc 2 tuần (nếu cần tùy chỉnh)

- [ ] **3. Tạo File Markdown**
  - [ ] Tên file: `Report_[ProjectName]_ver_[VERSION].md`
  - [ ] Folder: `/Reports/`
  - [ ] Tuân thủ cấu trúc 7 mục

- [ ] **4. Tính Toán**
  - [ ] Overall progress = (DONE / prioritized) × 100
  - [ ] Group assignment cho mỗi backlog
  - [ ] Severity cho issues

- [ ] **5. (Optional) Tạo HTML Dashboard**
  - [ ] Copy template từ WSale.html
  - [ ] Update config + projectData
  - [ ] Save ở `/HTML_Output/`
  - [ ] Test responsive + animation

---

## X. NOTES QUAN TRỌNG

### Về File Report

1. **Nếu user chỉ cấp backlog:**
   - Tôi hỏi tiến độ + deadline
   - Infer công việc 2 tuần từ timeline
   - Infer risk từ default WSale/OmniSell

2. **Nếu user cấp đầy đủ:**
   - Tạo file ngay
   - Yêu cầu confirm trước khi tạo HTML

3. **Nếu user muốn update later:**
   - File markdown có thể edit lại
   - HTML sẽ update theo dữ liệu mới

### Về Group Colors

- 5 group chuẩn: Infrastructure, Marketing, Features, Automation, Development
- Có thể thêm: Backend, Integration, Database, Analytics, API, etc.
- Mỗi group cần có `{ bg: "...", color: "..." }`

### Về Timeline Deadline

| User nói | Suy luận |
|----------|---------|
| "Quý 1" | 31/03 |
| "Quý 2" | 30/06 |
| "Quý 3" | 30/09 |
| "Quý 4" | 31/12 |
| "Tháng 2" | 28/02 |
| "Tháng 3" | 31/03 |
| Cụ thể "15/3" | 15/03 |

### Về Công Việc 2 Tuần

- Lấy backlog có deadline < 14 ngày từ hôm nay
- Chia Tuần 1 (7 ngày đầu) + Tuần 2 (7 ngày sau)
- Nếu không có backlog nào < 14 ngày, hỏi user

---

## XI. SỰ KHÁC BIỆT GIỮA CÁC DỰ ÁN

| Khía Cạnh | WSale | OmniSell | Khác |
|-----------|-------|---------|------|
| Version | 1.5 | 2.2 | ? |
| Release | 31/03 | 31/03 | ? |
| Quý | Q1 | Q1 | ? |
| Group | Infra, Marketing, Features, Automation, Development | Backend, Integration, Database + 5 chuẩn | Custom |
| Risk | Resource, Integration | Resource, Integration | ? |
| Backlog | 5 prioritized, 0 pending | 6 prioritized, 7 pending, 1 skipped | ? |
| Overall % | 20% (1/5) | 17% (1/6) | ? |

---

**File này được update lần cuối:** 30/01/2026
**Support cho dự án:** WSale, OmniSell, NewProject (và các dự án khác)
**Ready for use:** ✅
