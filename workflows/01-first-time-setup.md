---
description: Workflow lần đầu sử dụng - Hệ thống hóa folder từ đầu
---

# 🚀 Workflow 1: Lần Đầu Sử Dụng (First-Time Setup)

## Mục Đích
Dành cho người **lần đầu** muốn hệ thống hóa lại folder đang lộn xộn thành cấu trúc khoa học, gọn gàng.

---

## Bước 1: Xác Định Mục Đích

**AI hỏi người dùng:**
```
Bạn muốn tổ chức folder này cho mục đích gì?

1. 👤 Cá nhân (tài liệu học tập, công việc freelance, file cá nhân)
2. 📁 Dự án (tài liệu cho 1 project cụ thể)
3. 🏢 Doanh nghiệp (tổ chức theo sơ đồ công ty, phòng ban)
4. 🎨 Creative (thiết kế, media, content)
5. 💻 Developer (code, documentation, assets)

Chọn số (1-5) hoặc mô tả mục đích khác:
```

---

## Bước 2: Thu Thập Thông Tin Cơ Bản

**AI hỏi tiếp:**
```
📂 Đường dẫn folder cần tổ chức:
[Ví dụ: D:\Documents\MyFolder]

📝 Mô tả ngắn về nội dung folder:
[Folder này chứa những gì?]

🏗️ Bạn đã có sẵn cấu trúc/sơ đồ tổ chức mong muốn chưa?
- Có → Vui lòng mô tả hoặc attach file
- Chưa → AI sẽ đề xuất cấu trúc phù hợp
```

---

## Bước 3: Chọn Quy Chuẩn Đặt Tên

**AI gợi ý các option:**
```
🏷️ Chọn quy chuẩn đặt tên folder/file:

A. Tiếng Việt không dấu + Gạch dưới
   Ví dụ: 01_Tai_Lieu_Du_An, Bao_Cao_Thang_01.xlsx

B. Tiếng Anh + Gạch dưới  
   Ví dụ: 01_Project_Documents, Monthly_Report_Jan.xlsx

C. Hỗn hợp (giữ nguyên tên gốc có ý nghĩa)
   Ví dụ: 01_Marketing, Báo cáo Q1.xlsx

D. Tùy chỉnh khác (mô tả quy chuẩn riêng của bạn)

📌 Có đánh số thứ tự folder không? (01, 02, 03...)
- Có (dễ sắp xếp theo thứ tự)
- Không (tự do hơn)
```

---

## Bước 4: Khảo Sát & Đếm File

**AI thực hiện (tự động):**
```powershell
# Đếm tổng số file
$count = (Get-ChildItem -Path "[PATH]" -Recurse -File).Count
Write-Host "📊 Tổng số file hiện tại: $count"

# Liệt kê cấu trúc
Get-ChildItem -Path "[PATH]" -Recurse | Select-Object FullName
```

**AI báo cáo:**
```
📊 KẾT QUẢ KHẢO SÁT:
- Tổng số file: XXX
- Tổng số folder: XXX
- Các loại file chính: .docx, .xlsx, .pdf, .jpg...
- Kích thước folder: XX MB

⚠️ Số liệu này sẽ được verify lại sau khi hoàn thành.
```

---

## Bước 5: Đề Xuất Cấu Trúc Mới

**AI phân tích và đề xuất:**
```
📐 CẤU TRÚC ĐỀ XUẤT:

[Tên Folder Gốc]/
├── 01_[Tên_Folder_1]/
│   ├── [Subfolder_A]/
│   └── [Subfolder_B]/
├── 02_[Tên_Folder_2]/
├── 03_[Tên_Folder_3]/
├── ...
├── 98_Templates/
└── INDEX.md

📋 BẢNG PHÂN BỔ:
| File/Folder hiện tại | → Di chuyển đến |
|---------------------|-----------------|
| [Tên cũ 1]          | 01_xxx/         |
| [Tên cũ 2]          | 02_xxx/         |
| ...                 | ...             |

✅ Bạn có đồng ý với cấu trúc này không?
- Đồng ý → Tiếp tục thực hiện
- Điều chỉnh → Nói rõ muốn thay đổi gì
```

---

## Bước 6: Thực Hiện (Sau Khi User Đồng Ý)

**AI thực hiện từng bước:**
```
🔄 ĐANG THỰC HIỆN...

[1/5] Tạo cấu trúc folder mới... ✅
[2/5] Di chuyển file nhóm 1... ✅
[3/5] Di chuyển file nhóm 2... ✅
[4/5] Đổi tên file theo quy chuẩn... ✅
[5/5] Tạo file INDEX.md... ✅
```

---

## Bước 7: Xác Minh & Báo Cáo

**AI kiểm tra:**
```powershell
$afterCount = (Get-ChildItem -Path "[PATH]" -Recurse -File).Count
```

**Báo cáo hoàn thành:**
```
✅ HOÀN THÀNH!

📊 KẾT QUẢ XÁC MINH:
- File trước: XXX
- File sau: XXX
- Trạng thái: ✅ Không mất file nào

📁 CẤU TRÚC MỚI:
[Hiển thị tree folder mới]

📄 File INDEX.md đã được tạo để hướng dẫn tra cứu.

💡 Gợi ý tiếp theo:
- Xem file INDEX.md để biết cách tìm file
- Sử dụng Workflow "Dọn Định Kỳ" để duy trì cấu trúc
```

---

## Lưu Ý Quan Trọng

⚠️ **KHÔNG BAO GIỜ** xóa file - chỉ di chuyển và đổi tên  
⚠️ **LUÔN** đếm file trước/sau để verify  
⚠️ **LUÔN** hỏi user xác nhận trước khi thực hiện
