# 05 — SDLC, STLC & Agile: QA làm việc trong team như thế nào

## Mục tiêu

Bạn hiểu software được giao như thế nào, QA tham gia ở mỗi điểm nào, và các nghi thức Scrum căn bản.

![SDLC and STLC](diagrams/sdlc-stlc.svg)

## 1. SDLC — Software Development Life Cycle

1. **Requirement:** xác định vấn đề, user, business rule, acceptance criteria.
2. **Design:** UX/UI, kiến trúc, API/data design.
3. **Development:** implement code và unit test.
4. **Testing:** xác minh chất lượng theo risk/requirement.
5. **Deployment:** đưa bản đã duyệt ra staging/production.
6. **Maintenance:** theo dõi, hỗ trợ, sửa lỗi, cải tiến.

QA không chờ đến bước Testing. QA nên review requirement sớm, làm rõ acceptance criteria, chuẩn bị test data/environment và nêu risk trước khi code xong.

## 2. STLC — Software Testing Life Cycle

1. Requirement analysis: hiểu testable requirement và đặt câu hỏi.
2. Test planning: scope, risk, estimate, approach, exit criteria.
3. Test design: scenario, test case, test data, traceability.
4. Environment setup: URL/build, account, device, browser, tools.
5. Execution: run tests, log result, thu evidence.
6. Defect reporting & tracking: tạo, triage, retest, regression.
7. Test closure: summary, coverage, open risk, lesson learned.

## 3. Delivery models

- **Waterfall:** từng giai đoạn tuần tự; phù hợp requirement ổn định nhưng feedback chậm.
- **V-Model:** mỗi bước phát triển liên kết một lớp test tương ứng; nhấn mạnh test planning sớm.
- **Agile:** giao từng phần nhỏ, lấy feedback thường xuyên và điều chỉnh theo sprint/flow.
- **Kanban:** nhìn công việc trên board, giới hạn work-in-progress, không bắt buộc sprint cố định.
- **XP:** nhấn mạnh engineering practices như TDD, pair programming, refactoring, continuous integration.
- **SAFe:** khung Agile quy mô nhiều team/tổ chức; người mới chỉ cần nhận biết.

## 4. Scrum căn bản cho QA

| Sự kiện/artefact | QA cần làm |
| --- | --- |
| Product backlog | Đọc story, nhận diện risk/testability |
| Sprint planning | Estimate test effort, dependencies, test data |
| Daily standup | Nêu blocker, kết quả test, bug cần hỗ trợ |
| Trong sprint | Test sớm từng story, report rõ, retest fix |
| Sprint review | Cung cấp trạng thái chất lượng, demo khi cần |
| Retrospective | Nêu cách giảm bug/process waste ở sprint sau |

![Scrum feedback loop](diagrams/scrum-feedback-loop.svg)

## Checklist

- [ ] Nêu được 6 pha SDLC và 7 pha STLC.
- [ ] Chỉ ra QA tham gia trước khi developer hoàn tất code như thế nào.
- [ ] Phân biệt Waterfall, V-Model, Scrum và Kanban ở mức cơ bản.
- [ ] Giải thích Sprint, User Story, Backlog, Daily, Review, Retrospective.
