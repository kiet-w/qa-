# 02 — QA Foundations: Tư Duy & Nền Tảng QA

## Mục tiêu
Hiểu bản chất QA là gì, tư duy khác developer ra sao, phân biệt Verification vs Validation, nắm vững 7 nguyên tắc ISTQB, Bug Life Cycle, và Severity vs Priority.

---

## 📊 Sơ đồ trực quan (Diagrams & Lifecycles)

### Mối quan hệ QA ⊃ QC ⊃ Testing
![Mối quan hệ QA ⊃ QC ⊃ Testing](diagrams/qa-qc-testing.svg)

### Ba phương pháp Testing (Black box, Gray box, White box)
![Ba phương pháp Testing (Black box, Gray box, White box)](diagrams/testing-approaches.svg)

### Vòng đời của Bug (Bug Life Cycle)
![Vòng đời của Bug (Bug Life Cycle)](diagrams/bug-lifecycle.svg)

### Ma trận Severity vs Priority
![Ma trận Severity vs Priority](diagrams/severity-priority.svg)

## 1. QA vs QC vs Testing

| Khái niệm | Định nghĩa & Mục tiêu | Tính chất | Ví dụ |
|---|---|---|---|
| **QA (Quality Assurance)** | Tập trung vào **quy trình** — đảm bảo cách làm đúng để sản phẩm ít lỗi nhất | Phòng ngừa (Preventive) | Coding standards, Code review checklist, CI/CD pipeline rule |
| **QC (Quality Control)** | Tập trung vào **sản phẩm** — kiểm tra sản phẩm có đạt chuẩn không | Phát hiện (Detective) | Chạy bộ test, kiểm tra output của build |
| **Testing** | Hoạt động thực thi cụ thể nằm trong QC để tìm lỗi | Thực thi (Execution) | Nhập wrong password -> check error message |

> 💡 **Cách nhớ:** QA = "Làm đúng cách" ➔ QC = "Sản phẩm đúng chưa" ➔ Testing = "Chạy thử tìm lỗi".

---

## 2. QA Mindset: Adversarial & Systemic Thinking

Dev khi code feature "Form đăng ký" nghĩ:
> "User nhập tên, email, password ➔ validate ➔ lưu DB ➔ redirect dashboard. Done."

QA khi test cùng feature nghĩ:
> "Nếu user nhập toàn space? Nếu email có dấu '+'? Nếu password đúng 8 ký tự biên? Nếu click submit 2 lần liên tiếp? Nếu mất mạng giữa chừng?"

### 5 Câu hỏi QA luôn tự hỏi:
1. Input nào user có thể nhập mà dev chưa nghĩ tới? (Edge cases)
2. Chuyện gì xảy ra ở ranh giới? (Boundary values: min, max, empty, overflow)
3. Thứ tự thao tác nào có thể gây lỗi? (Sequence: back button, double submit, refresh)
4. Trong điều kiện môi trường nào hệ thống sẽ fail? (Slow network, low memory)
5. Requirement nào đang mơ hồ? (Ambiguous requirement gap)

---

## 3. Black Box, White Box & Gray Box Testing

- **Black Box:** Không biết code bên trong, chỉ test Input ➔ Output từ góc nhìn User.
- **White Box:** Nhìn vào cấu trúc code, branches, loops để thiết kế test cases (Unit test).
- **Gray Box:** Biết 1 phần kiến trúc (API spec, DB schema) nhưng test từ bên ngoài.
  - *Dev background advantage:* Bạn làm Gray Box testing cực kỳ tự nhiên vì hiểu cả frontend, backend lẫn database.

---

## 4. Verification vs Validation

- **Verification:** "Are we building the product RIGHT?" (Đúng spec/kỹ thuật chưa?) ➔ Code review, static analysis, unit test.
- **Validation:** "Are we building the RIGHT product?" (Đúng nhu cầu user chưa?) ➔ UAT, Beta testing, Usability test.

---

## 5. 🆕 ISTQB 7 Testing Principles (7 Nguyên Tắc Vàng)

1. **Testing shows the presence of defects, not their absence:** Test chỉ chứng minh có lỗi, không chứng minh "hết lỗi".
2. **Exhaustive testing is impossible:** Không thể test hết mọi tổ hợp input ➔ Phải chọn test thông minh (Risk-based).
3. **Early testing saves time and money:** Test càng sớm (từ requirement), chi phí sửa càng rẻ (Shift-Left Testing).
4. **Defects cluster together (Pareto 80/20):** 80% lỗi nằm ở 20% module phức tạp nhất ➔ Tập trung test vùng nguy cơ cao.
5. **Pesticide paradox:** Chạy lại cùng 1 bộ test hoài sẽ không tìm được lỗi mới ➔ Phải luôn cập nhật test cases.
6. **Testing is context dependent:** Test banking app khác hoàn toàn test game mobile hay IoT.
7. **Absence-of-errors fallacy:** App không có lỗi kỹ thuật nhưng không đáp ứng nhu cầu user thì vẫn thất bại.

---

## 6. 🆕 Bug Life Cycle & Severity vs Priority

### Bug Life Cycle
```
New ➔ Open/Assigned ➔ In Progress ➔ Fixed ➔ Retest ➔ Verified (Closed) ✅
                                                 └➔ Reopened 🔄 (nếu lỗi còn)
                                └➔ Rejected / Deferred / Duplicate ❌
```

### Severity (Mức độ kỹ thuật) vs Priority (Mức độ ưu tiên)
- **Severity (QA đánh giá):** Critical (crash/data loss), Major (feature chính hỏng), Minor (lỗi phụ có workaround), Trivial (cosmetic).
- **Priority (PM/PO quyết định):** Urgent (sửa ngay), High (sửa trong sprint), Medium, Low.
- 💡 **Ví dụ kinh điển:**
  - *High Severity + Low Priority:* App crash khi nhập emoji vào field ít dùng.
  - *Low Severity + High Priority:* Logo công ty trên trang chủ bị lệch/sai màu.

---

## Checklist & Bài tập
- [ ] Phân biệt QA vs QC vs Testing bằng ví dụ thực tế.
- [ ] Giải thích 7 nguyên tắc ISTQB.
- [ ] Phân biệt Severity vs Priority và cho 2 ví dụ minh họa.
- [ ] Bài tập: Viết 5 câu hỏi "Nếu... thì sao?" cho tính năng Quên mật khẩu.
