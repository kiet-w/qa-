# 09 — AI-Powered QA: dùng AI có kiểm chứng

## Mục tiêu

Bạn dùng AI để tăng tốc test planning, test case, exploratory ideas, bug report và log analysis; đồng thời biết cách review để AI không làm sai business logic.

![AI review loop](diagrams/ai-qa-review-loop.svg)

## Nguyên tắc không thay đổi

1. Requirement đã xác nhận và ứng dụng thật là nguồn quyết định; AI không phải nguồn quyết định cuối.
2. AI output là **draft**, không phải deliverable hoàn chỉnh.
3. Không gửi secret, token, mật khẩu, dữ liệu khách hàng hoặc source code nhạy cảm vào AI không được công ty phê duyệt.
4. Không tin severity/priority AI tự gán nếu không kiểm tra impact và quy ước team.
5. Lưu prompt/output quan trọng như một note học tập, nhưng không copy nguyên văn khi chưa review.

## Quy trình dùng AI cho một feature

### Bước 1 — Chuẩn bị context tối thiểu

Cung cấp: user story, acceptance criteria, user role, trạng thái/giới hạn dữ liệu, platform, phần không nằm trong scope và format output. Xóa dữ liệu nhạy cảm trước khi gửi.

### Bước 2 — Yêu cầu AI tạo bản nháp

Ví dụ prompt:

```text
You are assisting a manual QA tester. Create a DRAFT test design only.

Feature: Add one or more products to cart.
Rules: cart badge increases by the number of distinct added products;
out-of-stock items cannot be added; cart persists after refresh for logged-in users.
Scope: web UI on Chrome desktop.

Return positive, negative, and edge scenarios in a table with:
ID, title, preconditions, steps, test data, expected result, risk, priority.
Flag assumptions instead of inventing missing rules.
```

### Bước 3 — Review như một QA

1. Xóa test không thuộc feature hoặc dựa trên rule không có thật.
2. So từng expected result với acceptance criteria/oracle.
3. Thêm business rule, role, dữ liệu, integration và history mà AI không biết.
4. Kiểm tra đủ positive, negative, boundary, state transition, error/recovery, security/accessibility khi phù hợp.
5. Sắp xếp priority theo impact/likelihood thật, không theo câu chữ AI.
6. Chạy test trên app và ghi actual/evidence; không đánh Pass chỉ vì AI nói hợp lý.

### Bước 4 — Dùng AI ở các điểm phù hợp

| Công việc | AI có thể hỗ trợ | QA phải xác minh |
| --- | --- | --- |
| Test planning | Brainstorm risk/dependency | Scope và risk theo business |
| Test cases | Draft cases từ spec | Expected result, missing cases |
| Exploratory | Gợi ý edge cases/charters | Tính thực tế trên app |
| Bug report | Chuẩn hóa ghi chú thô | Steps, actual, severity, secrets |
| Logs/network | Giải thích dấu hiệu/error | Evidence và nguyên nhân gốc |
| Automation | Skeleton test/locator idea | Selector, assertion, flakiness |

## Câu trả lời phỏng vấn mẫu

> “Tôi dùng AI để brainstorm rủi ro, tạo bản nháp test case, chuẩn hóa bug report và hỗ trợ đọc log. Trước khi dùng kết quả, tôi đối chiếu từng expected result với acceptance criteria, thêm business context mà AI không biết, chạy trên ứng dụng thật và lưu evidence. Vì vậy AI giúp tôi nhanh hơn nhưng không thay thế trách nhiệm QA.”

## Checklist

- [ ] Viết prompt có scope, rules, platform và output format.
- [ ] Ghi rõ assumption AI đưa ra và xác nhận/xóa nó.
- [ ] Review ít nhất 10 AI-generated test cases trên app demo.
- [ ] Không đưa secret/data nhạy cảm vào prompt.
