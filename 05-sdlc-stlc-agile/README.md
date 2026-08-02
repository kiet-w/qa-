# 05 — SDLC, STLC & Agile/Scrum Workflow

## Mục tiêu
Hiểu rõ vòng đời phát triển phần mềm (SDLC), vòng đời kiểm thử (STLC), vai trò và công việc hàng ngày của QA trong team Agile/Scrum.

---

## 1. SDLC Models & Vị trí của QA

- **Waterfall:** QA chỉ vào test ở đoạn cuối ➔ Rủi ro phát hiện lỗi muộn, chi phí sửa cực đắt.
- **V-Model:** Mỗi pha Dev có 1 pha Test tương ứng (Requirement ➔ Acceptance Test, Architecture ➔ Integration Test, Code ➔ Unit Test).
- **Agile/Scrum:** Dev & QA làm việc song song trong các Sprint (1-2 tuần). QA tham gia từ khâu grooming/planning (Shift-Left Testing).

---

## 2. STLC (Software Testing Life Cycle)

```
Requirement Analysis ➔ Test Planning ➔ Test Case Development ➔ Environment Setup ➔ Test Execution ➔ Test Cycle Closure
```

---

## 3. QA trong Agile/Scrum Ceremonies

| Ceremony | Vai trò & Hoạt động của QA |
|---|---|
| **Sprint Planning / Grooming** | Đọc Requirement/User Story, hỏi các câu hỏi Edge cases làm rõ spec, estimate effort test |
| **Daily Standup** | Báo cáo: Hôm qua test gì, hôm nay test gì, có Blocker nào không |
| **Sprint Review / Demo** | Báo cáo tình hình chất lượng, số lượng bug, demo tính năng đã test |
| **Retrospective** | Đóng góp ý kiến cải tiến quy trình release, giảm thiểu bug tái diễn |

---

## 4. Definition of Done (DoD)

Một User Story chỉ được xem là **DONE** khi:
- [x] Code đã được Code Review.
- [x] Unit Test & Integration Test PASS.
- [x] QA đã Execute toàn bộ Test Cases & Verified PASS.
- [x] Không còn open Critical / Major bugs.
- [x] Code đã deploy thành công lên Staging/Production.
