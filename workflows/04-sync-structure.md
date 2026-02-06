---
description: Workflow đồng bộ cấu trúc folder - Áp dụng cấu trúc chuẩn cho nhiều folder
---

# 🔗 Workflow 4: Đồng Bộ Cấu Trúc Folder (Sync Structure)

## Mục Đích
Áp dụng một cấu trúc folder chuẩn cho nhiều folder khác nhau:
- Tạo folder mới với cấu trúc giống folder mẫu
- Kiểm tra folder hiện có xem đã đủ cấu trúc chưa
- Bổ sung folder còn thiếu

---

## Bước 1: Chọn Folder Mẫu (Template)

**AI hỏi:**
```
🏗️ CHỌN NGUỒN CẤU TRÚC:

A. Sử dụng folder có sẵn làm mẫu
   📂 Đường dẫn folder mẫu: ___

B. Sử dụng template có sẵn trong skill
   1. 🏢 Cấu trúc Doanh nghiệp
   2. 📁 Cấu trúc Dự án
   3. 👤 Cấu trúc Cá nhân
   4. 💻 Cấu trúc Developer
   5. 🎨 Cấu trúc Creative

C. Tự định nghĩa cấu trúc mới
   [Mô tả cấu trúc mong muốn]

Chọn:
```

---

## Bước 2: Xem Trước Cấu Trúc

**AI hiển thị cấu trúc được chọn:**
```
📐 CẤU TRÚC SẼ ÁP DỤNG:

[Template Name]/
├── 01_Folder_A/
│   ├── Subfolder_1/
│   └── Subfolder_2/
├── 02_Folder_B/
├── 03_Folder_C/
├── 98_Templates/
└── INDEX.md

✅ Xác nhận cấu trúc này?
🔧 Điều chỉnh (thêm/bớt folder)
```

---

## Bước 3: Chọn Folder Đích

**AI hỏi:**
```
📂 ÁP DỤNG CẤU TRÚC CHO:

A. Tạo folder MỚI với cấu trúc này
   📂 Tên folder mới: ___
   📂 Vị trí: ___

B. Kiểm tra & bổ sung cho folder CÓ SẴN
   📂 Đường dẫn folder: ___

C. Áp dụng cho NHIỀU folder (batch)
   📂 Danh sách folder:
   - ___
   - ___
   - ___

Chọn:
```

---

## Bước 4: Kiểm Tra (Nếu Folder Có Sẵn)

**AI so sánh:**
```
🔍 SO SÁNH CẤU TRÚC:

| Folder chuẩn | Folder hiện tại | Trạng thái |
|--------------|-----------------|------------|
| 01_Folder_A/ | ✅ Có           | OK         |
| 02_Folder_B/ | ❌ Thiếu        | Cần tạo    |
| 03_Folder_C/ | ⚠️ Tên khác     | Đổi tên?   |
| INDEX.md     | ❌ Thiếu        | Cần tạo    |

📋 HÀNH ĐỘNG ĐỀ XUẤT:
- Tạo mới: 2 folder
- Đổi tên: 1 folder (03_Folder_C)
- Giữ nguyên: 1 folder

✅ Đồng ý thực hiện?
```

---

## Bước 5: Thực Hiện Đồng Bộ

**AI thực hiện:**
```
🔄 ĐANG ĐỒNG BỘ...

[1/4] Tạo folder 02_Folder_B/... ✅
[2/4] Tạo subfolder 02_Folder_B/Sub_1/... ✅
[3/4] Đổi tên Folder_C → 03_Folder_C/... ✅
[4/4] Tạo file INDEX.md... ✅
```

---

## Bước 6: Báo Cáo

```
✅ ĐỒNG BỘ HOÀN TẤT!

📁 Folder đã xử lý: [Tên folder]

📊 Kết quả:
- Folder tạo mới: 2
- Folder đổi tên: 1
- File tạo mới: 1 (INDEX.md)

📐 Cấu trúc hiện tại:
[Hiển thị tree đầy đủ]

💡 Áp dụng cho folder khác? Chạy lại workflow này!
```

---

## Lưu Template Mới (Tùy Chọn)

```
💾 Lưu cấu trúc này làm template mới?
- Tên template: ___
- Mô tả: ___

→ Lưu vào: skill/templates/[tên].json
```
