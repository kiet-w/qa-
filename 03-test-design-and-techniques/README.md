# 03 — Test Design & Techniques: chọn đúng thứ cần test

## Mục tiêu

Bạn hiểu các loại test thường gặp, phân biệt Smoke/Sanity/Regression và biết ưu tiên khi không đủ thời gian test tất cả.

![Risk-based prioritization](diagrams/risk-prioritization.svg)

## 1. Phân loại nhanh các loại test

| Nhóm | Mục đích | Ví dụ |
| --- | --- | --- |
| Functional | Tính năng có đúng theo rule không? | Add to Cart cập nhật đúng số lượng |
| Non-functional | Chất lượng sử dụng/vận hành | Tốc độ, bảo mật, accessibility |
| Unit | Một hàm/module nhỏ | Hàm tính tổng tiền |
| Integration | Nhiều thành phần ghép với nhau | UI → API → database |
| UAT | Business/user chấp nhận sản phẩm | PO xác nhận flow mua hàng |
| Compatibility | Nhiều browser/device/OS | Safari mobile, Chrome desktop |

### Các loại test dễ nhầm

- **Smoke:** kiểm tra nhanh các flow sống còn của build mới: mở app, login, thao tác chính. Nếu fail, dừng test sâu và báo build không ổn.
- **Sanity:** kiểm tra hẹp sau một thay đổi/fix nhỏ, tập trung vào vùng vừa sửa và ảnh hưởng gần đó.
- **Regression:** chạy lại các test cũ liên quan sau thay đổi để xem chức năng đang tốt có bị phá không.
- **Exploratory:** test có mục tiêu nhưng không bị giới hạn bởi script cố định; ghi lại note để biến phát hiện tốt thành test case sau này.

### Non-functional cần biết

- **Performance/Load/Stress:** tốc độ, tải dự kiến, và hành vi khi vượt tải.
- **Security:** authentication, authorization, data exposure, XSS, SQL injection, CSRF.
- **Accessibility:** keyboard navigation, focus, contrast, label cho screen reader, thông báo lỗi.
- **Usability:** user có hiểu và hoàn thành việc dễ dàng không.

## 2. Prioritize theo rủi ro

Ưu tiên không chỉ là “cái dễ test trước”. Đánh giá từng vùng theo:

1. **Impact:** nếu fail thì mất tiền, mất dữ liệu, không login được hoặc lộ dữ liệu?
2. **Likelihood:** code mới, phức tạp, từng có bug, tích hợp nhiều hệ thống hoặc requirement mơ hồ?
3. **Reach/Frequency:** bao nhiêu người dùng, dùng bao nhiêu lần?
4. **Detectability:** lỗi có dễ bị phát hiện trước khi user gặp không?

Ví dụ: Auth, payment và quyền truy cập thường Impact cao; vì vậy chạy trước phần đổi màu nút hoặc text phụ.

## 3. Quy trình thiết kế test cho một feature

1. Chuyển requirement thành danh sách rule có thể kiểm tra.
2. Vẽ flow happy path: user bắt đầu ở đâu, thao tác gì, thành công ở đâu.
3. Tìm negative path: thiếu quyền, input sai, trạng thái không hợp lệ.
4. Tìm edge case: min/max length, số lượng 0/1/lớn, double click, refresh, network lỗi, nhiều tab.
5. Gắn risk và priority cho từng nhóm test.
6. Chọn mức test phù hợp: smoke trước, sanity sau fix, regression trước release.
7. Viết test case có expected result rõ; xem chặng 04 để chạy và report.

## Checklist

- [ ] Nêu được sự khác nhau giữa Smoke, Sanity, Regression.
- [ ] Có risk list cho Login hoặc Add to Cart.
- [ ] Chọn 5 test đầu tiên nếu chỉ có 30 phút trước release.
- [ ] Viết 3 exploratory charter, ví dụ: “Khám phá cart khi mạng chập chờn trong 20 phút”.
