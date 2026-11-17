---
name: mql5-development
description: Viết và compile EA MQL5 mới theo brief đã duyệt, chuẩn bị backtest phát triển qua queue.
---

Đọc cùng `skills/mt5-pipeline/SKILL.md`; paths tính từ project root.

Input: task Lead, frozen brief B + approval ref verified còn hiệu lực, input policy/test plan, data/profile/oracle refs. Trước viết source hoặc compile kiểm active B, closure/hash, provenance purpose đúng và policy. Chưa duyệt hoặc reader không kiểm được thì BLOCKED, không viết/compile/backtest strategy. Không dùng reviewer/spec PASS làm approval.

Tool: chỉ `mt5-editor` mười tool đúng role manifest. Kiểm get_workspace_info, allowed roots, build và host/Wine mapping trước staging. Tạo source EA mới và dependencies pin trong `source/`, dùng syntax_check/compile_file, đọc lại source/EX5 exact bytes+hash cùng compile log trong `builds/`. Không dùng EA có sẵn/Probe thay strategy mới; không shell launch compiler/Tester. Không ghi đè EA đang chạy, không arbitrary HTTP/build_project/account/Terminal tools.

Output: source/includes, build provenance/log, EX5, full SET inputs và profiles đúng B, candidate freeze C trước evidence run; handoff refs cho Lead. Submit job purpose development vào queue duy nhất trên segment đã duyệt. AuditFixtureMode=off cho strategy; nonce binding chỉ AuditAttempt theo policy. Từng attempt output mới, effective profile/costs/data/config/SET và audit phải đầy đủ. Không trực tiếp Tester prepare/run/stop, không tự xem holdout.

Error: compile lỗi giữ DEVELOPMENT; code-only fix cùng B phải candidate revision mới/run mới và evidence phân loại. Đổi risk/rules/SET ngoài policy trả Lead/Research cho brief mới. UNKNOWN/crash/timeout không launch lại; báo dispatcher reconcile. Thiếu EX5/config/report/coverage thì INCOMPLETE, không lấy log 0 lỗi làm strategy PASS. Trả task cho Lead; Validator bot khác Engineer kiểm độc lập.
