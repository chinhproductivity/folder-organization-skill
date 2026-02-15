---
description: Workflow to standardize and integrate new Agents, Skills, or Workflows into the Antigravity ecosystem.
---

# 07. Antigravity Integration Workflow

Workflow này hướng dẫn cách đưa một thành phần mới (Agent, Skill, tài liệu) vào hệ thống Antigravity đúng chuẩn.

## 🟢 Phase 1: Xác Định & Chuẩn Hoá (Identify & Standardize)

- [ ] **Xác định loại thành phần**:
  - `Agent`: Nhân sự AI (file .md prompt).
  - `Skill`: Bộ kỹ năng (folder chứa SKILL.md).
  - `Workflow`: Quy trình làm việc (file .md).
  - `Knowledge`: Tài liệu kiến thức (file .pdf, .md, .docx).

- [ ] **Chuẩn hoá tên (Naming)**:
  - **Quy tắc**: Viết thường, dùng gạch nối, không dấu, không khoảng trắng.
  - *Ví dụ sai*: `Social Media Manager`, `tài liệu dự án`
  - *Ví dụ đúng*: `social-media-manager`, `tai-lieu-du-an`

- [ ] **Chuẩn hoá định dạng (Formatting)**:
  - Agent/Workflow: Bắt buộc là Markdown (`.md`).
  - Skill: Phải là folder chứa file `SKILL.md` ở gốc.

## 🟡 Phase 2: Kiểm Tra Trùng Lặp (Duplication Check)

- [ ] **Kiểm tra trong `.antigravity`**:
  - Chạy lệnh `list_dir` tại `.antigravity` để xem đã có chưa.
  - Nếu đã có: Dừng lại, kiểm tra nội dung xem có cần update không. **KHÔNG TẠO BẢN SAU**.

## 🟠 Phase 3: Tích Hợp (Integration)

Copy/Di chuyển thành phần vào đúng vị trí "nhà" của nó:

- [ ] **Agents**:

  ```powershell
  Move-Item -Path "[Path_To_New_Agent]" -Destination ".antigravity/agents/"
  ```

- [ ] **Skills**:

  ```powershell
  Move-Item -Path "[Path_To_New_Skill_Folder]" -Destination ".antigravity/skills/"
  ```

- [ ] **Workflows**:
  - *Lưu ý*: Workflow thường nằm trong folder của Skill tương ứng.
  - Nếu là workflow chung: đưa vào `.agent/workflows/`.

- [ ] **Knowledge**:

  ```powershell
  Move-Item -Path "[Path_To_Doc]" -Destination ".antigravity/knowledge_base/"
  ```

## 🔴 Phase 4: Khai Báo (Registration) - *Optional*

- [ ] Nếu là Skill mới, hãy cập nhật vào file `README.md` tổng của Antigravity (nếu có) để mọi người biết.
- [ ] Thông báo cho User biết đã tích hợp thành công.
