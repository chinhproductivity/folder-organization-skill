# 📁 Folder Organization Skill for AI Agents

Bộ skill hướng dẫn AI hệ thống hóa và tổ chức lại cấu trúc folder/file một cách khoa học, có thể áp dụng cho cá nhân hoặc doanh nghiệp.

## ✨ Tính Năng

- ✅ **Không xóa file** - Chỉ di chuyển và đổi tên
- ✅ **Verification** - Đếm file trước/sau để đảm bảo không mất dữ liệu
- ✅ **Lập kế hoạch trước** - User approve trước khi thực hiện
- ✅ **Đa nền tảng** - Windows (PowerShell) + macOS/Linux (Bash)
- ✅ **Hỗ trợ Cloud** - Best practices cho OneDrive, Google Drive, Dropbox

## 🚀 Cách Sử Dụng

### 1. Copy folder vào dự án của bạn

```bash
# Clone repo
git clone https://github.com/YOUR_USERNAME/folder-organization-skill.git

# Copy vào .agent/skills/
cp -r folder-organization-skill/folder-organization /path/to/your/project/.agent/skills/
```

### 2. Gọi skill bằng prompt

```
Tôi muốn bạn giúp tôi hệ thống hóa lại folder của mình.

**Thông tin:**
- Folder cần tổ chức: [đường dẫn]
- Loại: [Cá nhân / Doanh nghiệp / Dự án]
- Mô tả nội dung: [folder này chứa gì?]
- Có sơ đồ tổ chức sẵn: [Có / Không]

**Yêu cầu:**
- Ngôn ngữ đặt tên: [Tiếng Việt không dấu / Tiếng Anh]
- Có đánh số folder: [Có / Không]

**Lưu ý quan trọng:**
- KHÔNG được xóa bất kỳ file nào
- Đếm số file trước và sau để verify
- Lập kế hoạch cho tôi xác nhận trước khi thực hiện
```

## 📋 Nội Dung Skill

| File/Folder | Mô tả |
|-------------|-------|
| `SKILL.md` | Hướng dẫn chi tiết cho AI agent |
| `workflows/` | Các workflow từng bước |

---

## 🔄 Workflows Có Sẵn

| # | Workflow | Khi nào dùng |
|---|----------|--------------|
| 1 | **First-Time Setup** | Folder lộn xộn, cần tổ chức từ đầu |
| 2 | **Periodic Cleanup** | Folder đã tổ chức, cần dọn định kỳ |
| 3 | **Archive Old Files** | Lưu trữ file cũ, giảm lộn xộn |
| 4 | **Sync Structure** | Áp dụng cấu trúc chuẩn cho nhiều folder |
| 5 | **New Project Setup** | Tạo folder mới cho dự án với cấu trúc sẵn |
| 7 | **Antigravity Integration** | Đưa Agent/Skill mới vào hệ thống Antigravity đúng chuẩn |

👉 Chi tiết: Xem folder `/workflows`

### Các Sections Trong SKILL.md

1. **Quy tắc bắt buộc** - Critical rules
2. **Input cần thu thập** - Thông tin từ user
3. **Quy trình 6 phases** - Workflow chi tiết
4. **Quy chuẩn đặt tên** - Naming conventions
5. **Mẫu cấu trúc** - Templates cho doanh nghiệp/dự án/cá nhân
6. **Xử lý lỗi** - Error handling
7. **Cloud sync** - Best practices
8. **Rollback** - Khôi phục nếu cần

## 🏢 Ví Dụ Thực Tế

Skill này được phát triển dựa trên case study tổ chức folder **Lắp Đặt 247**:

- Input: 58 items lộn xộn
- Output: 6 khối phòng ban có cấu trúc rõ ràng
- Kết quả: ~900 files được tổ chức lại mà không mất file nào

## 📄 License

MIT License - Tự do sử dụng và chia sẻ.

## 🤝 Đóng Góp

Mọi đóng góp đều được hoan nghênh! Vui lòng tạo Issue hoặc Pull Request.

---

**Tác giả:** Tuyết Chinh  
**Facebook:** [Tuyết Chinh](https://www.facebook.com/chinhproductivity)  
**Website:** [tuyetchinh.com](https://tuyetchinh.com)  
**Buy me a coffee:** MB Bank `0983095803`  

**Ngày tạo:** 2026-02-06
