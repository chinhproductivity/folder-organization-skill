---
description: Workflow archive file cũ - Lưu trữ file không còn sử dụng thường xuyên
---

# 📦 Workflow 3: Archive File Cũ (Archive Old Files)

## Mục Đích
Tự động tìm và di chuyển file cũ (ít sử dụng) vào folder lưu trữ để:
- Giảm lộn xộn trong folder làm việc
- Giữ folder chính gọn nhẹ
- Vẫn có thể tìm lại khi cần

---

## Tiêu Chí Archive

| Tiêu chí | Mặc định | Có thể tùy chỉnh |
|----------|----------|------------------|
| Thời gian không sửa | > 6 tháng | ✅ |
| Thời gian không mở | > 3 tháng | ✅ |
| Kích thước file | Không giới hạn | ✅ |
| Loại file | Tất cả | ✅ Có thể loại trừ |

---

## Bước 1: Thiết Lập Tiêu Chí

**AI hỏi:**
```
📦 THIẾT LẬP ARCHIVE:

📂 Folder nguồn: [Đường dẫn]

📅 Archive file không sửa đổi trong bao lâu?
- 3 tháng
- 6 tháng (mặc định)
- 1 năm
- Tùy chỉnh: ___

📁 Folder archive đích:
- [PATH]/99_Archive/ (mặc định)
- Tùy chỉnh: ___

🚫 Loại file KHÔNG archive:
- Templates (*.template.*)
- File đang mở (*.tmp, *.lock)
- Khác: ___
```

---

## Bước 2: Quét File Đủ Điều Kiện

**AI thực hiện:**
```powershell
# Tìm file cũ hơn 6 tháng
$cutoffDate = (Get-Date).AddMonths(-6)
Get-ChildItem -Path "[PATH]" -Recurse -File | 
    Where-Object { $_.LastWriteTime -lt $cutoffDate } |
    Select-Object FullName, LastWriteTime, Length
```

**Báo cáo:**
```
🔍 FILE ĐỦ ĐIỀU KIỆN ARCHIVE:

📊 Tổng số: X file (XX MB)
📅 Cũ nhất: [Ngày]
📅 Mới nhất trong nhóm: [Ngày]

| # | Tên file | Lần sửa cuối | Kích thước |
|---|----------|--------------|------------|
| 1 | xxx.docx | 2024-01-15   | 2.5 MB     |
| 2 | yyy.pdf  | 2024-02-20   | 1.2 MB     |
| ... | ... | ... | ... |

⚠️ Xem kỹ danh sách trước khi archive!
```

---

## Bước 3: Xác Nhận

**AI hỏi:**
```
📋 XÁC NHẬN ARCHIVE:

✅ Archive tất cả X file? 
❌ Bỏ qua và không archive
🔧 Loại trừ một số file (liệt kê số thứ tự)

Nhập lựa chọn:
```

---

## Bước 4: Thực Hiện Archive

**AI thực hiện:**
```
📦 ĐANG ARCHIVE...

Cấu trúc archive:
99_Archive/
└── [Năm]_[Tháng]/
    ├── [Tên_File_1]
    ├── [Tên_File_2]
    └── ...

[1/X] Di chuyển xxx.docx... ✅
[2/X] Di chuyển yyy.pdf... ✅
...
```

---

## Bước 5: Tạo Log Archive

**AI tự động tạo file log:**
```
📄 Tạo file: 99_Archive/ARCHIVE_LOG.md

Nội dung:
| Ngày archive | File | Vị trí gốc | Kích thước |
|--------------|------|------------|------------|
| 2025-01-15   | xxx  | 01_Docs/   | 2.5 MB     |
| ...          | ...  | ...        | ...        |
```

---

## Bước 6: Báo Cáo Hoàn Thành

```
✅ ARCHIVE HOÀN TẤT!

📊 Kết quả:
- File đã archive: X
- Dung lượng giải phóng: XX MB
- Vị trí archive: 99_Archive/2025_01/

📄 Log file: 99_Archive/ARCHIVE_LOG.md

💡 Cần khôi phục file? Xem ARCHIVE_LOG.md để biết vị trí gốc.
```

---

## Khôi Phục File (Nếu Cần)

```powershell
# Di chuyển file từ archive về vị trí gốc
Move-Item -Path "99_Archive/2025_01/xxx.docx" -Destination "01_Docs/xxx.docx"
```
