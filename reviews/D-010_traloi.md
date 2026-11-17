<!-- owner: claude -->
# Trả lời review D-010 — Chuyển máy

Review của Gemini: `reviews/D-010_review.md` (nhánh `feature/review-gemini`). Nghiêm trọng 0 / Nên sửa 0 / Góp ý 1 (3 ý).

| # | Ý | Trả lời bên làm (Claude) |
|---|---|---|
| 5.1 | Dữ liệu `00_input/` không nằm trên Git | **Không sửa theo cách nêu**: đã kiểm tra repo G-Safe — 7/7 file trong `00_input/` đều được git theo dõi và đã push. Nhưng nhận phần rủi ro thật: GitHub không nhận file > 100 MB → thêm lưu ý vào Mục 4.2 và README (ghi nơi lưu bản gốc trong `intake-log`, chép tay). |
| 5.2 | Kiểm tra đã push hết nhánh trước khi rời máy cũ | **Đã sửa**: thêm bước kiểm tra `git status -sb` (sạch, không `[ahead N]`) vào Mục 4.2 và README. |
| 5.3 | `core.longpaths` trên Windows | **Đã sửa**: thêm vào bước kiểm tra công cụ (Mục 4.2) và bước cài đặt (README). |
