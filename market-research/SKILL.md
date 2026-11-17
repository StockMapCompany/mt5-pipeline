---
name: market-research
description: Nghiên cứu dữ liệu và hoàn thiện brief chiến lược MT5 trước khi người dùng duyệt.
---

Đọc cùng `skills/mt5-pipeline/SKILL.md`; paths tính từ project root.

Input: prompt, phạm vi nghiên cứu, manifest nguồn và yêu cầu Lead; chưa có approval vẫn được research thị trường. Đọc role manifest cho toàn bộ server+tool được phép; không lấy holdings cloud làm broker account.

Tool: `mt5-terminal` chỉ market history/time/symbol/calendar đúng allowlist; `mt5-marketdata` chỉ sáu tool marketdata trong manifest. Trước dữ liệu lấy get_workspace_info/time, kiểm broker/cloud symbol mapping, UTC/broker/DST; timezone bất nhất không dùng chia split. Không file/account/Tester/chart/order tool.

Output: `research/`, `data/manifest.json` và raw/processed có nguồn/quyền dùng/ranges/hash/coverage/limitations; working brief.md, rules.json và test-plan.json đầy đủ checklist §9.4. Pin development/holdout/warm-up, oracle trade và no-trade, costs, tolerances, robustness/repeatability, PASS/FAIL/INCOMPLETE trước xem outcome. Không tự chọn thông số chiến lược để đạt test. N/A phải có lý do, không TBD ở quy tắc quyết định. Trả Lead refs/hash để freeze và trình người dùng, không tự giao Engineer.

Error: dữ liệu không export được ghi fingerprint + limitation; thiếu dữ liệu/timezone/rule thì BLOCKED có câu hỏi cụ thể cho Lead. Không truy cập holdout ngoài quyền plan hoặc xóa lịch sử exposure. Đổi criteria sau xem run cần B mới/duyệt mới và giữ exposure; không gọi dữ liệu đã tune là holdout độc lập.
