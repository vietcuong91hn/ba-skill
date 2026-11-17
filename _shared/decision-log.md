<!-- owner: claude -->
# Nhật ký quyết định của BA

Mỗi quyết định ghi một dòng. Không sửa dòng cũ; quyết định thay đổi thì thêm dòng mới dẫn chiếu mã cũ.

| Mã | Ngày | Việc | Quyết định | Căn cứ | Ảnh hưởng |
|---|---|---|---|---|---|
| D-001 | 17/11/2026 | G-00 | Đồng ý làm Bước 0. Chia sẻ file giữa hai worktree qua nhánh git (Gemini commit vào `feature/review-gemini`, Claude đọc bằng `git show`). Giao việc qua Orca orchestration. | Phiếu đề xuất G-00 | Cách làm việc chung cho mọi G-xx |
| D-002 | 17/11/2026 | G-00 | **Duyệt Mục 4.1** của `reviews/G-00_thongnhat.md`: 70 việc, Claude làm 49, Gemini làm 21. Đổi bên làm G-19, G-42, G-44, G-61, G-66; thêm G-69, G-70; G-71 không dùng; G-29 đổi B → Đk; tách G-58 (decision-log về G-57). | `reviews/G-00_thongnhat.md` Mục 4.1 | Cần sửa Mục 6 `CLAUDE.md`, `GEMINI.md`; tạo `task-board.md` |
| D-003 | 17/11/2026 | G-00 / G-13 | **Áp dụng chia loại dự án** trong G-13: A — phía chủ đầu tư; B — phía nhà cung cấp; C — sản phẩm nội bộ. Mỗi loại bật/tắt các việc liên quan. | Đề xuất P-01 của Gemini | G-13 BA Plan có phần chọn loại dự án |
| D-004 | 17/11/2026 | G-29 | Dự án **không có đội UX riêng** → G-29 Wireframe **áp dụng** (điều kiện Đk thỏa). | Trả lời câu hỏi mở số 3 | G-29 thực hiện khi đến giai đoạn đặc tả |
| D-005 | 17/11/2026 | G-62 | **Không làm** bộ template riêng cho dự án vốn ngân sách nhà nước (P-02). | Trả lời Q-01 | G-62 không có hạng mục này |
| D-006 | 17/11/2026 | Chung | Loại dự án (A/B/C), nguồn vốn và thông tin dự án khác **chưa rõ thì các trợ lý hỏi lại BA**, không tự đoán. | Trả lời Q-02, Q-03 | Ghi vào Mục 6 `CLAUDE.md`, `GEMINI.md`; hỏi khi bắt đầu từng dự án (G-13) |
| D-007 | 17/11/2026 | G-57 | Đồng ý phiếu cập nhật `CLAUDE.md`, `GEMINI.md` theo D-002, D-003, có ghi D-001 vào hai file. | Phiếu đề xuất cập nhật hai file nhiệm vụ | Claude sửa, Gemini review |
| D-008 | 17/11/2026 | G-57 | Ghi đúng môi trường chạy: Gemini chạy bằng **Antigravity CLI** (không phải Gemini CLI) trong `CLAUDE.md`, `GEMINI.md`, `README.md`; README cập nhật danh mục G-01 … G-70. | BA yêu cầu "sửa lại chạy trên antigravity cho chuẩn" | Claude sửa, Gemini review |
| D-009 | 17/11/2026 | G-57 | **Hướng submodule**: `ba-skill` là bộ quy tắc gốc; mỗi dự án là repo riêng gắn `ba-skill` tại `_skill/`, chốt phiên bản bằng tag. Mã công việc trong dự án = mã dự án + số thứ tự (dự án mã `G` dùng G-01 … G-70). Tin nhắn mở đầu `[MÃ]`. Thêm `templates/project/`, Mục 4.1 vào hai file quy tắc; gắn tag `v1.0` sau khi Gemini review. | BA: "đồng ý hướng submodule"; "mã dự án là G, có các hậu tố đằng sau tương ứng các task" | Mọi dự án mới; dự án đầu tiên G-Safe |

## Chưa quyết (chờ BA)

Không còn câu hỏi mở. Q-01 → D-005; Q-02, Q-03 → D-006 (hỏi theo từng dự án).
