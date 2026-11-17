---
name: strategy-validation
description: Kiểm định độc lập candidate EA MT5 đóng băng và đánh giá tái dùng run theo test plan đã duyệt.
---

Đọc cùng `skills/mt5-pipeline/SKILL.md`; paths tính từ project root.

Input: task Lead, C/B và approval ref verified còn hiệu lực, snapshot immutable, criteria/split/test plan và development results. Kiểm khác bot Engineer, refs/digest/lineage, profile/segment, raw evidence và exposure ledger. Không sửa source, criteria hoặc snapshot để tạo PASS.

Tool: chỉ `mt5-terminal` năm read market/time/workspace tool trong role manifest và native đọc artifact project. Không đọc file/journal MT5 trực tiếp, không compile, không Tester launch/stop; adapter thu evidence. Yêu cầu run bổ sung qua queue, purpose validation và segment được plan cho phép.

Output: `validation/` report exact digest bind C/B, checks rules/entry/exit/risk/rounding/costs/data/ngoài mẫu/leakage/robustness/oracle trade+no-trade, run refs, reuse_assessments và additional_run_reasons theo §9.4/§12–13. Reuse run COMPLETE cùng C/B có coverage/evidence/profile/exposure phù hợp; [] additional_run_reasons hợp lệ nếu plan đã phủ. Thiếu yêu cầu mới submit thêm run với requirement_id/reason/job_ref; không chạy lại chỉ vì đổi requester. Đổi purpose không làm holdout đã tune trở lại độc lập.

Error/verdict: rule sai → FAIL; thiếu dữ liệu/audit/holdout độc lập/effective config/oracle → INCOMPLETE; PASS chỉ khi mọi tiêu chí được duyệt đủ bằng chứng. Ghi limitation/fingerprint không giả hash dữ liệu thiếu. Kỹ thuật lỗi trả Lead/Engineer cho C mới; đổi giả thuyết trả Research/B mới và duyệt lại. Giữ raw run, correction report mới có supersedes; Lead không override FAIL. Trả Lead handoff đúng task/refs/verdict, không deploy.
