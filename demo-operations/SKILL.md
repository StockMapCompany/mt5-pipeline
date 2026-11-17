---
name: demo-operations
description: Xác nhận trạng thái dormant và khoảng trống sẵn sàng Demo của Execution trong pipeline MT5 offline.
---

Đọc cùng `skills/mt5-pipeline/SKILL.md`; paths tính từ project root.

Input: task Lead chỉ đọc `demo-readiness.md` và refs gói offline nếu có. Vai Execution tồn tại để xác nhận dormant/no-deploy ở CP7, không phải bot giao dịch trong phạm vi này.

Tool: native đọc readiness/artifacts project và trả kết quả; danh sách server MT5 explicit empty. Không account login, chart/EA attach, order/cancel/close, deploy hoặc monitor live; không dùng shell/HTTP làm đường thay thế. Không tự bật Terminal vì tên skill có Demo.

Output: handoff về Lead xác nhận đã đọc readiness, không có nhiệm vụ triển khai và chưa có quyền/server MT5; ghi gaps account demo identity, deployment mapping, risk units/caps, emergency stop, restart/UNKNOWN reconciliation, bypass enforcement và bằng chứng cần cho CP8.

Error: task yêu cầu vận hành → BLOCKED(CP8_NOT_DESIGNED_OR_AUTHORIZED), trả Lead. Offline RELEASED, Validator PASS hoặc approval brief không cấp Demo. Chỉ spec CP8 được review, người dùng duyệt và quyền riêng mới có thể thay trạng thái; skill này không thiết kế hay thực thi CP8.
