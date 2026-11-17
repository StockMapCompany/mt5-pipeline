---
name: mt5-pipeline
description: Thực hiện hợp đồng chung cho nhiệm vụ pipeline MT5 offline trong dự án này, từ nghiên cứu brief đến bàn giao EA.
---

Áp dụng cùng skill riêng theo vai trong `department/role-manifests/`. Nguồn chuẩn là `docs/specs/mt5-pipeline.md` R3-roadmap1, đặc biệt §4, §9–14. Đường dẫn trong tài liệu này tính từ project root, không từ thư mục skill. Chỉ dùng project cwd đã đọc lại; CP2 là source, chưa chứng minh bot runtime đã nạp. Không tự cấp quyền ngoài nhiệm vụ được giao.

Trước nhận việc, kiểm task theo `templates/schemas/r3/task.json`: task_id, strategy/revision, actor/recipient ID thật, input refs exact bytes+SHA256, role manifest ref và bundle ref, acceptance, output dự kiến và return_to bot/thread/task. Dùng `python3 scripts/check-skills.py` kiểm nguồn/pin; CP3 phải so bản runtime và ID thật. Sai hash, sai recipient hoặc bundle/runtime lệch thì BLOCKED và trả Lead. Không dùng ID minh họa thay cấu hình thật. Đọc `department/task-contract.md` cho giai đoạn nhận/trả việc.

Mọi handoff dùng `mt5-handoff/1`, giữ task_id, revision, actor/recipient, skill_bundle_ref, input/output refs, acceptance, blocked_reason và return_to. Chỉ Lead giao việc bằng cơ chế MausBot được khám phá/kiểm ở CP3, không tự kích hoạt vì xuất hiện file. Một người giữ quyền sửa revision; Validator chỉ đọc snapshot. Không sửa DB/status projection trực tiếp: writer `python3 scripts/mt5_pipeline.py` với request schema §9, CAS/dedup và evidence. Lệnh chưa hiện thực phải fail closed; không giả thành công hoặc tự dùng lối khác.

Brief: prompt thiếu quy tắc vẫn được nghiên cứu. Lead/Research hoàn thiện checklist §9.4, freeze exact closure B rồi trình NguyenToan duyệt đúng B. Chỉ approval verified có purpose đúng brief_kind và còn hiệu lực mới cho phát triển/compile/backtest strategy. Lead/reviewer PASS, spec approval, release approval hay file tự ký không thay duyệt brief. Thiếu nguồn thật: SOURCE_UNVERIFIABLE, giữ BLOCKED; reader fixture không là quyền runtime. Technical fixture chỉ dùng approval đúng plan/digest, không chuyển thành strategy PASS.

Đổi bytes brief/rules/risk/criteria/data/profile/input ngoài policy: brief B mới, Research rồi người dùng duyệt lại; invalidate downstream, dừng/reconcile job cũ đúng run_id trước đổi active brief. Code-only bugfix/SET trong policy giữ B nếu chứng minh được nhưng candidate C mới, run/validation/release mới. Không phân loại được thì BLOCKED. Revoke/reject giữ audit, không ghi đè approval; queued job không launch, run đang chạy phải invalidated và reconcile.

Queue dispatcher là phần mềm, không bot thứ sáu. Engineer/Validator chỉ submit yêu cầu, không gọi Tester trực tiếp hoặc launch qua shell. Một Tester; UNKNOWN/RECOVERY_REQUIRED không retry hoặc tự nhả khóa. Không lấy launch ACK/status stopped/report cũ làm COMPLETE. Candidate freeze trước run; C/B, source/includes/build/EX5/SET/profile/report/audit phải nối đúng hash; refs không traversal/symlink/case collision. Chỉ dùng MCP tích hợp đúng alias §10 và mapping được kiểm; không dùng HTTP/shell để vượt allowlist. Tool không liệt kê mặc định deny. `native:*` vẫn giữ: shared folder/native shell là audit-only, không isolation.

Validator khác Engineer; giữ raw evidence, FAIL/INCOMPLETE không bị Lead đảo PASS. Reuse run COMPLETE cùng C/B khi plan/coverage/evidence/exposure hợp lệ, không bắt rerun vì đổi vai. Thiếu holdout chưa lộ hoặc oracle thì INCOMPLETE. Thêm run cần lý do theo plan. Không đổi tiêu chí sau xem kết quả.

Chỉ offline trên máy hiện tại, một MT5. Execution dormant/no-deploy; không account login, EA attach, order, live monitor hoặc nhiều máy. RELEASED offline không là quyền Demo; CP8 cần thiết kế và quyền riêng. Che secret trong log/export, chỉ lưu secret reference. Mọi lỗi ghi reason + refs vào handoff, nêu điều đã/chưa kiểm; không lấy fixture/docs/hash check làm runtime PASS.
