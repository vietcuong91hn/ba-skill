<!-- owner: claude -->
# Nhật ký quyết định của BA

Mỗi quyết định ghi một dòng. Không sửa dòng cũ; quyết định thay đổi thì thêm dòng mới dẫn chiếu mã cũ.

| Mã | Ngày | Việc | Quyết định | Căn cứ | Ảnh hưởng |
|---|---|---|---|---|---|
| D-001 | 17/11/2026 | G-00 | Đồng ý làm Bước 0. Chia sẻ file giữa hai worktree qua nhánh git (Gemini commit vào `feature/review-gemini`, Claude đọc bằng `git show`). Giao việc qua Orca orchestration. | Phiếu đề xuất G-00 | Cách làm việc chung cho mọi G-xx |
| D-002 | 17/11/2026 | G-00 | **Duyệt Mục 4.1** của `reviews/G-00_thongnhat.md`: 70 việc, Claude làm 49, Gemini làm 21. Đổi bên làm G-19, G-42, G-44, G-61, G-66; thêm G-69, G-70; G-71 không dùng; G-29 đổi B → Đk; tách G-58 (decision-log về G-57). | `reviews/G-00_thongnhat.md` Mục 4.1 | Cần sửa Mục 6 `CLAUDE.md`, `GEMINI.md`; tạo `task-board.md` |
| D-003 | 17/11/2026 | G-00 / G-13 | **Áp dụng chia loại dự án** trong G-13: A — phía chủ đầu tư; B — phía nhà cung cấp; C — sản phẩm nội bộ. Mỗi loại bật/tắt các việc liên quan. | Đề xuất P-01 của Gemini | G-13 BA Plan có phần chọn loại dự án |
| D-004 | 17/11/2026 | G-29 | Dự án **không có đội UX riêng** → G-29 Wireframe **áp dụng** (điều kiện Đk thỏa). | Trả lời câu hỏi mở số 3 | G-29 thực hiện khi đến giai đoạn đặc tả |

## Chưa quyết (chờ BA)

| # | Câu hỏi | Từ |
|---|---|---|
| Q-01 | Áp dụng bộ template riêng cho dự án vốn ngân sách nhà nước (P-02) không? | G-00 Mục 4.2 |
| Q-02 | Dự án sắp tới thuộc loại A, B hay C? | G-00 Mục 4.3 |
| Q-03 | Có dự án dùng vốn ngân sách nhà nước không? | G-00 Mục 4.3 |
