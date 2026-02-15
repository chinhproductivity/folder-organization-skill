---
name: Folder Organization System
description: Hệ thống hóa và tổ chức lại cấu trúc folder/file một cách khoa học, có thể áp dụng cho cá nhân hoặc doanh nghiệp
---

# Skill: Folder Organization System

## 📋 Mô Tả

Skill này giúp AI hệ thống hóa và tổ chức lại cấu trúc folder/file một cách khoa học, đảm bảo:

- Không xóa bất kỳ file nào
- Đặt tên folder/file theo quy chuẩn
- Phân loại theo logic phù hợp với mục đích sử dụng
- Áp dụng quy tắc quản trị dữ liệu (Naming, Security, Lifecycle)
- Có verification để đảm bảo không mất dữ liệu

---

## 🚨 QUY TẮC BẮT BUỘC (CRITICAL RULES)

1. **KHÔNG BAO GIỜ XÓA FILE** - Chỉ di chuyển và đổi tên
2. **LUÔN ĐẾM SỐ FILE TRƯỚC VÀ SAU** - Để verify không mất dữ liệu
3. **LUÔN LẬP KẾ HOẠCH TRƯỚC** - User phải approve trước khi thực hiện
4. **TẠO FILE INDEX.md** - Để dễ tra cứu cấu trúc mới
5. **BACKUP THÔNG TIN CẤU TRÚC CŨ** - Lưu lại cấu trúc ban đầu

---

## 🌌 QUY TẮC HỆ SINH THÁI ANTIGRAVITY (ANTIGRAVITY ECOSYSTEM RULES)

1. **SINGLE SOURCE OF TRUTH**: Mọi Agent, Skill, Workflow mới **BẮT BUỘC** phải được lưu trữ tập trung tại `.antigravity`.
   - Agents → `.antigravity/agents`
   - Skills → `.antigravity/skills`
   - Knowledge → `.antigravity/knowledge_base`

2. **CHUẨN HOÁ ĐẦU VÀO (INPUT STANDARDIZATION)**:
   - Tên thư mục hệ thống (skill/agent): Dùng `kebab-case` (ví dụ: `marketing-strategy`, không dùng `Marketing Strategy`).
   - Tên file tài liệu: Dùng `snake_case` hoặc `PascalCase` tuỳ loại, nhưng không chứa khoảng trắng.
   - Định dạng: Ưu tiên Markdown (`.md`) cho tài liệu hướng dẫn, PDF cho tài liệu tham khảo cố định.

3. **KIỂM TRA TRÙNG LẶP (NO DUPLICATION)**:
   - Trước khi tạo mới, luôn kiểm tra xem Agent/Skill đó đã tồn tại trong `.antigravity` chưa.
   - Nếu đã có, hãy **CẬP NHẬT** (Update) thay vì tạo bản sao (Duplicate).

---

## 📝 INPUT CẦN THU THẬP TỪ USER

Trước khi bắt đầu, AI **BẮT BUỘC** phải thu thập đầy đủ các thông tin sau:

### 1. Thông Tin Cơ Bản

```markdown
- **Tên folder cần tổ chức:** [Đường dẫn đầy đủ]
- **Mục đích của folder này:** [Cá nhân / Doanh nghiệp / Dự án / Khác]
- **Mô tả ngắn nội dung:** [Folder này chứa loại tài liệu gì?]
```

### 2. Yêu Cầu Cụ Thể

```markdown
- **Có cấu trúc/sơ đồ tổ chức sẵn không?** [Có / Không]
  - Nếu CÓ: Cung cấp sơ đồ hoặc mô tả cấu trúc mong muốn
  - Nếu KHÔNG: AI sẽ đề xuất cấu trúc dựa trên phân tích nội dung
- **Ngôn ngữ đặt tên:** [Tiếng Việt không dấu / Tiếng Anh / Hỗn hợp]
- **Format đặt tên:** [PascalCase / snake_case / kebab-case]
- **Có cần đánh số thứ tự folder không?** [Có / Không]
```

### 3. Quy Tắc Riêng (Nếu Có)

```markdown
- **Các quy tắc đặc biệt:** [Ví dụ: Không đổi tên file có ngày tháng, giữ nguyên một số folder...]
- **Folder/File cần giữ nguyên:** [Danh sách nếu có]
```

---

## 🔄 QUY TRÌNH THỰC HIỆN (WORKFLOW)

### Phase 1: Thu Thập Thông Tin

1. Hỏi user các thông tin INPUT ở trên
2. Không tiến hành nếu thiếu thông tin quan trọng

### Phase 2: Khảo Sát Cấu Trúc Hiện Tại

1. Dùng `list_dir` để khám phá cấu trúc folder
2. **ĐẾM TỔNG SỐ FILE BAN ĐẦU** và lưu lại:

```powershell
$beforeCount = (Get-ChildItem -Path "[FOLDER_PATH]" -Recurse -File).Count
Write-Host "Total files before: $beforeCount"
```

1. Lưu danh sách file vào file tạm (tùy chọn):

```powershell
Get-ChildItem -Path "[FOLDER_PATH]" -Recurse -File | Select-Object FullName | Export-Csv "file_list_before.csv"
```

### Phase 3: Phân Tích & Phân Loại

1. Phân loại files/folders theo chức năng
2. Xác định nguyên tắc phân loại phù hợp:
   - **Theo Chủ Sở Hữu (Owner)** - Ai tạo/quản lý tài liệu?
   - **Theo Mục Đích Chính (Primary Purpose)** - Mục tiêu chính là gì?
   - **Theo Workflow** - Ai sử dụng trong công việc?
   - **Theo Thời Gian** - Năm/Quý/Tháng
   - **Theo Dự Án** - Từng project riêng

### Phase 4: Lập Kế Hoạch (PLANNING)

1. Tạo file `implementation_plan.md` với:
   - Cấu trúc mới đề xuất (dạng tree)
   - Bảng mapping: Folder/File cũ → Vị trí mới
   - Quy chuẩn đặt tên áp dụng
   - Các bước thực hiện chi tiết
2. **YÊU CẦU USER XÁC NHẬN** trước khi thực hiện

### Phase 5: Thực Hiện (EXECUTION)

1. Tạo cấu trúc folder mới
2. Di chuyển và đổi tên files/folders
3. Thực hiện theo từng batch nhỏ để dễ kiểm soát

### Phase 6: Xác Minh (VERIFICATION)

1. **ĐẾM LẠI TỔNG SỐ FILE SAU KHI HOÀN THÀNH**:

```powershell
$afterCount = (Get-ChildItem -Path "[FOLDER_PATH]" -Recurse -File).Count
if ($beforeCount -eq $afterCount) {
    Write-Host "✓ PASSED: All $afterCount files preserved"
} else {
    Write-Host "✗ FAILED: Before=$beforeCount, After=$afterCount"
}
```

1. So sánh với số file ban đầu
2. Tạo file `INDEX.md` với cấu trúc mới và hướng dẫn tra cứu

---

## 📁 QUY CHUẨN ĐẶT TÊN (NAMING CONVENTIONS)

### Folders

| Loại | Quy chuẩn | Ví dụ |
|------|-----------|-------|
| Folder chính | `[Số]_[Tên_Không_Dấu]` | `01_Marketing`, `02_Tai_Chinh` |
| Subfolder | `[Tên_Không_Dấu]` | `Bao_Cao_Tuan`, `Hop_Dong_CTV` |

### Files

| Loại | Quy chuẩn | Ví dụ |
|------|-----------|-------|
| File có ngày | `YYYY-MM-DD_[Tên_File]` | `2025-01-15_Bao_Cao_Tuan.xlsx` |
| File thường | `[Tên_Không_Dấu]` | `Chinh_Sach_Dai_Ly.pdf` |

### Ký Tự Cần Tránh

- Dấu tiếng Việt (à, á, ả, ã, ạ...)
- Khoảng trắng (thay bằng `_`)
- Ký tự đặc biệt (&, %, #, @...)

---

## 🏢 MẪU CẤU TRÚC THEO LOẠI

### Cấu Trúc Cho Doanh Nghiệp (Có Sơ Đồ Tổ Chức)

```
Company_Name/
├── 00_Ban_Giam_Doc/           # Ban Giám Đốc
├── 01_Phong_Hanh_Chinh/       # Hành chính - Nhân sự
├── 02_Phong_Tai_Chinh/        # Tài chính - Kế toán
├── 03_Phong_Kinh_Doanh/       # Kinh doanh - Marketing
├── 04_Phong_Ky_Thuat/         # Kỹ thuật - Sản phẩm
├── 98_Bieu_Mau/               # Templates & Forms
└── INDEX.md
```

### Cấu Trúc Cho Dự Án

```
Project_Name/
├── 01_Chien_Luoc/             # Chiến lược & Kế hoạch
├── 02_Thiet_Ke/               # Design & Mockups
├── 03_Phat_Trien/             # Development
├── 04_Tai_Lieu/               # Documentation
├── 05_Test_QA/                # Testing
├── 06_Deploy/                 # Deployment
└── INDEX.md
```

### Cấu Trúc Cho Cá Nhân

```
Personal_Folder/
├── 01_Cong_Viec/              # Work
├── 02_Hoc_Tap/                # Learning
├── 03_Tai_Chinh/              # Finance
├── 04_Ca_Nhan/                # Personal
├── 05_Luu_Tru/                # Archive
└── INDEX.md
```

---

## 📄 MẪU INDEX.md

```markdown
# INDEX - [Tên Folder]

> **Cập nhật:** [Ngày]
> **Tổng số files:** [Số lượng]

## 📁 Cấu Trúc

| # | Folder | Mô tả | Items |
|---|--------|-------|-------|
| 01 | `01_Folder_Name/` | Mô tả ngắn | XX |
| ... | ... | ... | ... |

## 🔍 Tra Cứu Nhanh

| Cần tìm | Vào folder |
|---------|------------|
| [Loại tài liệu] | `[Folder path]` |
| ... | ... |

---
*Cập nhật: [Ngày]*
```

---

## ✅ CHECKLIST TRƯỚC KHI BẮT ĐẦU

- [ ] Đã thu thập đủ thông tin từ user
- [ ] Đã đếm số file ban đầu
- [ ] Đã lưu cấu trúc cũ (nếu cần)
- [ ] Đã xác định nguyên tắc phân loại
- [ ] Đã tạo implementation plan
- [ ] User đã approve kế hoạch
- [ ] Đã thực hiện di chuyển/đổi tên
- [ ] Đã đếm lại số file sau khi hoàn thành
- [ ] Số file trước = Số file sau
- [ ] Đã tạo INDEX.md

---

## 🔧 SCRIPTS HỮU ÍCH

### Đếm File (PowerShell)

```powershell
(Get-ChildItem -Path "[PATH]" -Recurse -File).Count
```

### Liệt Kê Tất Cả File

```powershell
Get-ChildItem -Path "[PATH]" -Recurse -File | Select-Object FullName, Length, LastWriteTime
```

### Di Chuyển Folder

```powershell
Move-Item -Path "[SOURCE]" -Destination "[DEST]" -Force
```

### Đổi Tên Folder

```powershell
Rename-Item -Path "[PATH]" -NewName "[NEW_NAME]" -Force
```

---

## 📚 VÍ DỤ THỰC TẾ

Skill này được phát triển dựa trên case study tổ chức folder **Lắp Đặt 247**, một doanh nghiệp có sẵn sơ đồ tổ chức với các khối:

- Ban Tổng Giám Đốc (BOD)
- Khối Văn Phòng (HCNS, TCKT, Pháp lý)
- Khối Kinh Doanh (Sales, Marketing)
- Khối Vận Hành (Operations)
- Khối Sản Phẩm & Tech

Kết quả: Tổ chức lại ~900 files từ 58 items lộn xộn thành 6 khối phòng ban có cấu trúc rõ ràng.

---

## ⚠️ XỬ LÝ LỖI THƯỜNG GẶP (ERROR HANDLING)

### 1. Folder Đang Được Sử Dụng

```
Lỗi: "Cannot rename the item because it is in use"
```

**Giải pháp:**

- Đóng tất cả file đang mở trong folder
- Đóng VS Code/IDE nếu đang mở folder
- Đóng File Explorer đang trỏ vào folder
- Thử lại sau vài giây (cloud sync có thể đang chạy)

### 2. Đường Dẫn Quá Dài (Windows)

```
Lỗi: "Path too long" hoặc "Could not find a part of the path"
```

**Giải pháp:**

- Rút ngắn tên folder/file
- Di chuyển folder gốc lên gần root (ví dụ: `D:\Work`)
- Bật Long Path Support trong Windows

### 3. Không Có Quyền (Permission Denied)

**Giải pháp:**

- Chạy terminal với quyền Administrator
- Kiểm tra quyền truy cập folder

---

## 🖥️ HỖ TRỢ ĐA HỆ ĐIỀU HÀNH

### macOS / Linux (Bash)

```bash
# Đếm file
find "[PATH]" -type f | wc -l

# Liệt kê file
find "[PATH]" -type f -exec ls -la {} \;

# Di chuyển folder
mv "[SOURCE]" "[DEST]"

# Đổi tên folder
mv "[OLD_NAME]" "[NEW_NAME]"
```

### Windows (PowerShell) - Đã có ở trên

---

## 🔀 XỬ LÝ TÀI LIỆU ĐA MỤC ĐÍCH

Khi một tài liệu phục vụ nhiều phòng ban/mục đích:

### Nguyên Tắc Quyết Định

1. **Chủ Sở Hữu (Owner)** - Ai tạo và duy trì?
2. **Mục Đích Chính (Primary Purpose)** - Tạo ra để làm gì?
3. **Tần Suất Sử Dụng (Usage)** - Bộ phận nào dùng nhiều nhất?

### Ví Dụ Thực Tế

| Tài liệu | Vừa là | Vừa là | → Phân vào |
|----------|--------|--------|------------|
| Chính sách thu hút thợ | Pháp lý | Marketing | **Kinh doanh** (mục đích chính: thu hút) |
| Hợp đồng CTV | Pháp lý | Nhân sự | **Pháp lý** (chủ sở hữu: bộ phận pháp lý) |
| Báo cáo tài chính | Tài chính | BOD | **Tài chính** (tạo bởi kế toán) |

### Lưu Ý

- KHÔNG tạo bản sao ở nhiều nơi (gây trùng lặp, khó cập nhật)
- Có thể tạo shortcut/link nếu cần truy cập nhanh từ nhiều nơi

---

## 🔄 ROLLBACK / KHÔI PHỤC

### Trước Khi Thực Hiện

Lưu lại cấu trúc cũ:

```powershell
# Lưu cấu trúc folder
Get-ChildItem -Path "[PATH]" -Recurse | Select-Object FullName, PSIsContainer | Export-Csv "structure_backup.csv" -Encoding UTF8

# Lưu danh sách file với đường dẫn đầy đủ
Get-ChildItem -Path "[PATH]" -Recurse -File | Select-Object FullName | Out-File "file_paths_backup.txt"
```

### Nếu Cần Khôi Phục

1. Sử dụng **OneDrive/Cloud Version History** để restore
2. Hoặc sử dụng file backup để biết vị trí cũ

---

## ☁️ LÀM VIỆC VỚI CLOUD SYNC (OneDrive, Google Drive, Dropbox)

### Best Practices

1. **Đợi sync hoàn tất** trước khi di chuyển file tiếp theo
2. **Kiểm tra icon trạng thái** (✓ = đã sync)
3. **Tránh di chuyển nhiều file cùng lúc** - chia thành batch nhỏ
4. **Kiểm tra Recycle Bin** nếu nghi ngờ mất file -cloud thường backup

### Xử Lý Conflict

Nếu có file conflict (2 version):

- Giữ version mới nhất
- Xóa file có suffix "conflict"

---

## 💬 PROMPT MẪU CHO USER

User có thể copy prompt này để bắt đầu sử dụng skill:

```
Tôi muốn bạn giúp tôi hệ thống hóa lại folder của mình.

**Thông tin:**
- Folder cần tổ chức: [đường dẫn]
- Loại: [Cá nhân / Doanh nghiệp / Dự án]
- Mô tả nội dung: [folder này chứa gì?]
- Có sơ đồ tổ chức sẵn: [Có / Không]
- Nếu có, cấu trúc mong muốn: [mô tả hoặc attach file]

**Yêu cầu:**
- Ngôn ngữ đặt tên: [Tiếng Việt không dấu / Tiếng Anh]
- Có đánh số folder: [Có / Không]
- Quy tắc đặc biệt: [nếu có]

**Lưu ý quan trọng:**
- KHÔNG được xóa bất kỳ file nào
- Đếm số file trước và sau để verify
- Lập kế hoạch cho tôi xác nhận trước khi thực hiện
```

---

## 📋 TỔNG HỢP CÁC BƯỚC (QUICK REFERENCE)

```
1. THU THẬP → Hỏi input từ user
2. ĐẾM FILE → Ghi lại số lượng ban đầu
3. KHÁM PHÁ → list_dir để hiểu cấu trúc
4. PHÂN TÍCH → Xác định nguyên tắc phân loại
5. LẬP KẾ HOẠCH → Tạo implementation_plan.md
6. XÁC NHẬN → User approve
7. THỰC HIỆN → Di chuyển/đổi tên theo batch
8. VERIFY → Đếm lại, so sánh số file
9. TẠO INDEX → File hướng dẫn tra cứu
10. BÁO CÁO → Thông báo hoàn thành
```
