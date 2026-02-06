---
description: Workflow dọn folder định kỳ - Duy trì cấu trúc gọn gàng
---

# 🔄 Workflow 2: Dọn Folder Định Kỳ (Periodic Cleanup)

## Mục Đích
Dành cho folder **đã được tổ chức**, cần dọn dẹp định kỳ để:
- Xử lý file mới chưa được phân loại
- Đổi tên file không đúng quy chuẩn
- Di chuyển file nằm sai vị trí

---

## Khi Nào Nên Chạy?

| Tần suất | Phù hợp với |
|----------|-------------|
| Hàng tuần | Folder làm việc chính, có nhiều file mới |
| Hàng tháng | Folder dự án, ít thay đổi |
| Hàng quý | Folder lưu trữ, archive |

---

## Bước 1: Xác Nhận Folder

**AI hỏi:**
```
📂 Folder cần dọn dẹp: [Đường dẫn]

✅ Xác nhận folder này đã được tổ chức trước đó?
- Có → Tiếp tục
- Chưa → Sử dụng Workflow "Lần Đầu Sử Dụng"
```

---

## Bước 2: Quét File Mới & Lỗi

**AI thực hiện:**
```powershell
# Tìm file ở root (chưa phân loại)
Get-ChildItem -Path "[PATH]" -File

# Tìm file có tên không đúng quy chuẩn (có dấu, khoảng trắng...)
Get-ChildItem -Path "[PATH]" -Recurse -File | Where-Object { $_.Name -match '[àáảãạăắằẳẵặâấầẩẫậ]|[ ]' }
```

**Báo cáo:**
```
🔍 KẾT QUẢ QUÉT:

📁 File chưa phân loại (nằm ở root): X file
📝 File tên không đúng quy chuẩn: X file
📅 File có thể cần archive (>6 tháng): X file

Chi tiết:
| # | Tên file | Vấn đề | Đề xuất |
|---|----------|--------|---------|
| 1 | xxx.docx | Ở root | → 01_Folder/ |
| 2 | báo cáo.pdf | Có dấu | → Bao_Cao.pdf |
| ... | ... | ... | ... |
```

---

## Bước 3: Xác Nhận Hành Động

**AI hỏi từng nhóm:**
```
📋 HÀNH ĐỘNG ĐỀ XUẤT:

[Nhóm 1] Di chuyển X file vào đúng folder
✅ Đồng ý / ❌ Bỏ qua / 🔧 Điều chỉnh

[Nhóm 2] Đổi tên X file theo quy chuẩn  
✅ Đồng ý / ❌ Bỏ qua / 🔧 Điều chỉnh

[Nhóm 3] Archive X file cũ
✅ Đồng ý / ❌ Bỏ qua / 🔧 Điều chỉnh
```

---

## Bước 4: Thực Hiện

**AI thực hiện sau khi user đồng ý từng nhóm:**
```
🔄 ĐANG XỬ LÝ...

[1/3] Di chuyển file chưa phân loại... ✅
[2/3] Đổi tên file theo quy chuẩn... ✅
[3/3] Archive file cũ... ✅ (nếu có)
```

---

## Bước 5: Báo Cáo Hoàn Thành

```
✅ DỌN DẸP HOÀN TẤT!

📊 Kết quả:
- File đã di chuyển: X
- File đã đổi tên: X
- File đã archive: X

📅 Lần dọn tiếp theo: [Gợi ý ngày]

💡 Tip: Đặt reminder để dọn dẹp định kỳ!
```

---

## Tự Động Hóa (Tùy Chọn)

Nếu muốn nhắc nhở tự động, tạo Task Scheduler:
```powershell
# Tạo reminder hàng tuần
$action = New-ScheduledTaskAction -Execute "powershell" -Argument "Write-Host 'Nhắc: Dọn folder!'"
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Monday -At 9am
Register-ScheduledTask -TaskName "FolderCleanupReminder" -Action $action -Trigger $trigger
```
