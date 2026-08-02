# 03 — Test Design & Techniques: Kỹ Thuật Thiết Kế Test

## Mục tiêu
Nắm vững 6 kỹ thuật thiết kế test case chuẩn quốc tế (Black-box Test Design Techniques) giúp tối ưu hóa số lượng test case mà vẫn đảm bảo độ bao phủ (coverage) cao nhất.

---

## 📊 Sơ đồ trực quan (Diagrams & Lifecycles)

### Risk-based Testing Prioritization
![Risk-based Testing Prioritization](diagrams/risk-prioritization.svg)

### Equivalence Partitioning & Boundary Value Analysis
![Equivalence Partitioning & Boundary Value Analysis](diagrams/bva-ep.svg)

### Decision Table Testing Matrix
![Decision Table Testing Matrix](diagrams/decision-table.svg)

### State Transition Testing (Order Flow)
![State Transition Testing (Order Flow)](diagrams/state-transition.svg)

## 1. Equivalence Partitioning (EP - Phân vùng tương đương)

Chia tập dữ liệu đầu vào thành các nhóm (partitions) mà hệ thống xử lý giống nhau. Chỉ cần chọn 1 giá trị đại diện cho mỗi nhóm.

**Ví dụ:** Field "Tuổi" chấp nhận 18 đến 65.
- Partition 1 (Invalid): `< 18` ➔ Đại diện: `15`
- Partition 2 (Valid): `18 - 65` ➔ Đại diện: `30`
- Partition 3 (Invalid): `> 65` ➔ Đại diện: `70`
➔ Giảm từ hàng nghìn test case xuống 3 test cases đại diện.

---

## 2. Boundary Value Analysis (BVA - Phân tích giá trị biên)

Lỗi phần mềm thường tập trung ở BIÊN của ranh giới các vùng tương đương.
- Công thức chọn biên: **min-1, min, min+1, max-1, max, max+1**

**Ví dụ:** Field "Tuổi" (18 - 65):
- Biên dưới: `17` (Invalid), `18` (Valid), `19` (Valid)
- Biên trên: `64` (Valid), `65` (Valid), `66` (Invalid)
➔ 6 test values tập trung bắt các lỗi `>` thành `>=` hoặc `<` thành `<=`.

---

## 3. Decision Table Testing (Bảng quyết định)

Dùng khi kết quả phụ thuộc vào NHIỀU ĐIỀU KIỆN kết hợp.

**Ví dụ:** Tính năng Giảm giá đơn hàng:

| Condition / Action | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
|---|---|---|---|---|
| Là thành viên VIP? | True | True | False | False |
| Đơn hàng > 500k? | True | False | True | False |
| **Giảm giá (%)** | **20%** | **10%** | **5%** | **0%** |

Mỗi cột Rule tương ứng 1 Test Case chuẩn xác.

---

## 4. State Transition Testing (Chuyển đổi trạng thái)

Dùng cho các đối tượng có vòng đời và trạng thái phức tạp (ví dụ: Đơn hàng, Vé máy bay, Tài khoản).

```
[Draft] ──submit──▶ [Submitted] ──approve──▶ [Approved] ──ship──▶ [Delivered]
                          │
                          └──reject──▶ [Rejected]
```
- **Test:** Tất cả các luồng chuyển trạng thái hợp lệ.
- **Negative Test:** Thử thực hiện chuyển trạng thái KHÔNG hợp lệ (Ví dụ: Từ `Draft` nhảy thẳng sang `Delivered` ➔ Phải báo lỗi).

---

## 5. Pairwise Testing (Combinatorial Testing)

Khi có quá nhiều biến số kết hợp (OS x Browser x Resolution x Language), Pairwise giúp giảm 80-90% số lượng test case bằng cách đảm bảo mọi CẶP biến đều được test ít nhất 1 lần.
- Tool hỗ trợ: PICT (Microsoft), AllPairs.

---

## 6. Error Guessing & Negative Testing

- **Error Guessing:** Dùng trực giác và kinh nghiệm để đoán chỗ hay lỗi (Nhập emoji, copy-paste trailing space, double click submit, SQL injection string `' OR '1'='1`).
- **Positive vs Negative Testing:**
  - Positive: Input đúng ➔ Kỳ vọng kết quả đúng (~40% test cases).
  - Negative: Input sai/bất thường ➔ Kỳ vọng hệ thống xử lý mượt mà, báo lỗi rõ ràng (~60% test cases).

---

## Checklist & Bài tập
- [ ] Áp dụng EP và BVA cho field Password (8 - 20 ký tự, chứa ít nhất 1 chữ hoa, 1 số).
- [ ] Lập Decision Table cho tính năng áp dụng mã Voucher.
- [ ] Vẽ State Transition Diagram cho quy trình Đặt hàng online.
