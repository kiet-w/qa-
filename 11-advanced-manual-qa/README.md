# 11 — Advanced Manual QA: Kỹ Thuật Manual QA Nâng Cao

## Mục tiêu
Làm chủ kỹ thuật Session-Based Exploratory Testing (SBET), kỹ năng Bug Advocacy (thuyết phục Dev/PM fix bug), và Pair Testing với Developer.

---

## 1. Session-Based Exploratory Testing (SBET)

Exploratory Testing không phải là test bừa bãi. SBET quản lý theo quy trình:
1. **Charter:** Mục tiêu phiên test (VD: "Khám phá luồng thanh toán khi mất kết nối mạng").
2. **Time-box:** Khung thời gian cố định (60 - 90 phút).
3. **Session Log:** Ghi chép chi tiết các bước, phát hiện, câu hỏi và lỗi.
4. **Debrief:** Họp ngắn với Team để review kết quả.

---

## 2. Bug Advocacy (Kỹ năng thuyết phục sửa bug)

Để PM/Dev đồng ý fix một bug khó:
- Cung cấp dữ liệu tác động: "80% người dùng dùng Chrome trên Mobile bị ảnh hưởng bởi lỗi này ➔ Gây thất thoát doanh thu".
- Gửi kèm Video / Network trace rõ ràng.
