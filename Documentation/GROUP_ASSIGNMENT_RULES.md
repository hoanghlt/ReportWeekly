# Rules Gán Group cho Backlog

## 📌 Hướng Dẫn Xác Định Group

Dựa vào **tính chất & nội dung** của backlog, xác định group phù hợp:

---

## 🎯 Các Group & Dấu Hiệu Nhận Biết

### 1️⃣ **Infrastructure** (Hạ tầng, DevOps, K8s)
**Dấu hiệu:**
- Liên quan đến hạ tầng, server, deployment
- K8s, Docker, cloud infrastructure
- Cơ sở hạ tầng hệ thống
- Network, load balancing
- CI/CD pipeline

**Ví dụ:**
- "Nâng cấp hạ tầng K8s cụm API TLS Inside" ✓
- "Setup Docker container" ✓
- "Tối ưu AWS S3 configuration" ✓
- "Upgrade server version" ✓

**Ví dụ sai:**
- "Bổ sung check trùng Đơn hàng Online" ✗ (Là Features)
- "Cung cấp API KHTN" ✗ (Là Integration hoặc API)

---

### 2️⃣ **Backend** (Nghiệp vụ, Logic, Database)
**Dấu hiệu:**
- Refactor code, architecture
- Business logic, algorithm
- Database schema, optimization
- Service layer, API logic
- Event handling, logging

**Ví dụ:**
- "Refactor cụm BE (nghiệp vụ & kiến trúc)" ✓
- "Chuẩn hóa event schema & logging" ✓
- "Tổ chức lại bộ KQTV chung" ✓
- "Tiếp nhận KHTN từ SR ghi nhận" ✓

---

### 3️⃣ **Integration** (Kết nối, API, Webhooks)
**Dấu hiệu:**
- Cung cấp/tiếp nhận API
- Tích hợp với service external
- Webhook, sync data
- Message queue, event bus
- 3rd party service connection

**Ví dụ:**
- "Cung cấp API KHTN cho FoxOne" ✓
- "Tiếp nhận KHTN từ SR system" ✓
- "Nhận KHTN VIP 7 DKOL" ✓
- "Tích hợp ecom-cms-web lên fox-erp" ✓

---

### 4️⃣ **Database** (Data, Schema, Storage)
**Dấu hiệu:**
- Thay đổi database schema
- Data migration
- Storage optimization
- Địa chỉ, configuration data
- Data validation, constraints

**Ví dụ:**
- "Thay đổi thông tin địa chỉ HCQG" ✓
- "Migration data từ old DB sang new DB" ✓
- "Optimize database indexes" ✓
- "Add new table for KHTN" ✓

---

### 5️⃣ **Features** (Tính năng mới, UI, User-facing)
**Dấu hiệu:**
- Tính năng mới cho user
- Giao diện, UI/UX
- User workflow
- Report, dashboard
- Mobile app features

**Ví dụ:**
- "LDP V.VIP Map: Tra cứu hạ tầng Wifi 7" ✓
- "WSale bản Mobile SOP" ✓
- "Auto tạo KHTN kênh Social: Zalo Mini app" ✓
- "Custom lại phần lưu các utm cho MKT" ✓

---

### 6️⃣ **Marketing** (MKT, Campaign, Analytics)
**Dấu hiệu:**
- Marketing campaigns
- Analytics, tracking
- User behavior, events
- Promotion, discount logic
- Campaign management

**Ví dụ:**
- "LDP V.VIP MKT: Bổ sung nhận diện tập data từ FMI" ✓
- "Promotion ECP: Đồng bộ campaign" ✓
- "Custom utm tracking" ✓ (hoặc Features)
- "Analytics dashboard" ✓

---

### 7️⃣ **Automation** (Auto, Check, Validation, Logic)
**Dấu hiệu:**
- Automatic processing
- Check, validate, duplicate detection
- Auto-generation
- Workflow automation
- Rule engine

**Ví dụ:**
- "Autocall: Check blacklist, check trùng SĐT" ✓
- "Bổ sung check trùng Đơn hàng Online" ✓
- "Bổ sung check trùng Checklist tư vấn" ✓
- "Auto tạo KHTN kênh Social" ✓

---

### 8️⃣ **Development** (Dev, Framework, Libraries)
**Dấu hiệu:**
- Upgrade dependencies
- Framework changes
- Development tools
- Code generation
- Build system

**Ví dụ:**
- "Upgrade SpringBoot from 2.x to 3.x" ✓
- "Migrate to React 18" ✓
- "Update build pipeline" ✓
- "Setup testing framework" ✓

---

### 9️⃣ **Analytics** (Data Analysis, Reporting)
**Dấu hiệu:**
- Data analysis
- Report generation
- Business intelligence
- Metrics, KPI
- Data warehouse

**Ví dụ:**
- "Create analytics dashboard" ✓
- "Generate sales report" ✓
- "Build KPI tracking system" ✓

---

### 🔟 **API** (API Design, Gateway, Protocol)
**Dấu hiệu:**
- API specification
- API Gateway
- Protocol changes
- API versioning
- API documentation

**Ví dụ:**
- "Design RESTful API schema" ✓
- "Setup API Gateway" ✓
- "Migrate API v1 to v2" ✓

---

## 🎯 Decision Tree (Cách Quyết Định)

```
Backlog là gì?

├─ Liên quan Server/K8s/Cloud?
│  └─> Infrastructure
│
├─ Refactor/Logic/Database schema?
│  └─> Backend
│
├─ Kết nối API/External service/Webhook?
│  └─> Integration
│
├─ Thay đổi DB/Data/Address?
│  └─> Database
│
├─ Tính năng mới/UI/Mobile?
│  └─> Features
│
├─ Auto/Check/Validation?
│  └─> Automation
│
├─ Marketing/Campaign/Analytics (user-facing)?
│  └─> Marketing
│
├─ Upgrade dependencies/Framework?
│  └─> Development
│
├─ Data Analysis/Report/BI?
│  └─> Analytics
│
└─ API design/Gateway/Protocol?
   └─> API
```

---

## 📊 Real-World Examples

### OmniSell Ver 2.2

| Backlog | Group | Lý Do |
|---------|-------|------|
| Nhận KHTN VIP 7 DKOL - GTEL PAY(BCA) | **Integration** | Tiếp nhận từ GTEL PAY (external service) |
| Tổ chức lại bộ KQTV chung | **Backend** | Thay đổi logic/schema KQTV |
| Cung cấp API KHTN cho FoxOne | **Integration** | Cung cấp API cho service external |
| Tiếp nhận KHTN từ SR nonSHD | **Backend** | Xử lý logic tiếp nhận + DB |
| Thay đổi thông tin địa chỉ HCQG | **Database** | Thay đổi data địa chỉ |
| Refactor cụm BE | **Backend** | Refactor architecture/logic |
| Bổ sung mã màu + mess | **Features** | UI/UX changes |
| Custom utm | **Features** hoặc **Marketing** | MKT tracking hoặc Feature |
| Event schema & logging | **Backend** | Architecture, logging system |
| Auto tạo KHTN Social | **Automation** | Auto-generation |
| Check trùng Đơn hàng | **Automation** | Validation logic |
| Check trùng Checklist | **Automation** | Validation logic |

### WSale Ver 1.5

| Backlog | Group | Lý Do |
|---------|-------|------|
| Nâng cấp K8s cụm API TLS | **Infrastructure** | K8s, deployment |
| LDP V.VIP MKT | **Marketing** | Marketing feature |
| LDP V.VIP Map | **Features** | User-facing feature |
| Autocall Logic | **Automation** | Auto check, validation |
| Mobile SOP | **Features** hoặc **Development** | Mobile app + framework |

---

## 🔑 Tips & Tricks

### Nếu khó chọn giữa 2 group:

**Backend vs Features?**
- Backend: Nếu focus vào logic/algorithm ➜ Backend
- Features: Nếu focus vào UI/User experience ➜ Features
- Ví dụ: "Bổ sung check trùng" = Automation (vì là check/validation)

**Features vs Marketing?**
- Features: General functionality ➜ Features
- Marketing: Specific to marketing/campaigns ➜ Marketing
- Ví dụ: "Custom utm" = Marketing (vì là MKT tracking)

**Integration vs Backend?**
- Integration: Kết nối external service ➜ Integration
- Backend: Internal logic/refactor ➜ Backend
- Ví dụ: "Cung cấp API" = Integration (vì là kết nối external)

**Database vs Backend?**
- Database: Schema/address/data changes ➜ Database
- Backend: Business logic changes ➜ Backend
- Ví dụ: "Thay đổi địa chỉ" = Database (vì là data change)

---

## ✅ Checklist Khi Gán Group

- [ ] Backlog có liên quan Infrastructure? → Infrastructure
- [ ] Là Auto/Check/Validation? → Automation
- [ ] Là kết nối external service? → Integration
- [ ] Là thay đổi data/DB schema? → Database
- [ ] Là refactor/logic? → Backend
- [ ] Là tính năng mới/UI? → Features
- [ ] Là MKT/Campaign? → Marketing
- [ ] Là upgrade dependencies? → Development

---

## 📌 Summary Table

| Group | Color | Ví Dụ | Key Words |
|-------|-------|--------|----------|
| Infrastructure | 🔵 Blue | K8s, Server, Cloud | deploy, infrastructure, k8s |
| Backend | 🔵 Blue | Refactor, Logic | refactor, logic, schema, business |
| Integration | 🟠 Orange | API, External service | api, integrate, webhook, external |
| Database | 🟣 Purple | Data, Address, Schema | database, data, address, schema |
| Features | 🟡 Amber | New feature, UI | feature, ui, user, app, mobile |
| Marketing | 🟢 Green | Campaign, Analytics | marketing, campaign, analytics, utm |
| Automation | 🟣 Purple | Auto, Check, Validate | auto, check, validate, duplicate |
| Development | 🩶 Gray | Dependencies, Framework | upgrade, framework, dependencies |
| Analytics | 📊 Multi | Report, BI | analytics, report, dashboard, bi |
| API | 🔵 Blue | API Design, Gateway | api, gateway, protocol |

---

**File này để tham khảo khi gán group cho backlog trong báo cáo mới!**
