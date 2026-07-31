# 04 — Manual Testing Workflow: từ requirement đến bug report

## Mục tiêu

Bạn có thể nhận một feature, lập kế hoạch vừa đủ, viết test case, thực thi, ghi bug có thể tái hiện và báo kết quả test.

![Manual testing loop](diagrams/manual-test-cycle.svg)

## 1. Quy trình đầy đủ cho một feature

### Bước 1 — Đọc và làm rõ requirement

Đọc user story, acceptance criteria, thiết kế và business rule. Ghi ra các câu hỏi chưa rõ; không tự đặt expected result khi chưa có oracle.

Ví dụ user story: “Là một khách hàng, tôi muốn thêm sản phẩm vào giỏ để mua sau.” Câu hỏi cần làm rõ: giới hạn số lượng? guest có cart không? cart có giữ sau refresh không? hết hàng xử lý thế nào?

### Bước 2 — Lập test plan ngắn

Test plan cho feature nhỏ chỉ cần trả lời:

- **Scope:** Add to Cart, cart badge, cart details; phần nào không test.
- **Risk:** sai giá/số lượng, mất cart, thêm nhầm item, lỗi quyền.
- **Approach:** smoke happy path, functional/negative/edge, exploratory, compatibility.
- **Environment & data:** URL, browser, account, sản phẩm còn hàng/hết hàng.
- **Entry/exit criteria:** khi nào bắt đầu; điều kiện nào cho phép kết thúc/pass.
- **Owner/timeline:** ai test, khi nào retest, cần ai hỗ trợ.

### Bước 3 — Viết scenario rồi mới viết test case

Scenario là ý tưởng cấp cao: “User thêm một sản phẩm vào cart.” Test case là hướng dẫn có thể chạy lại.

| Cột test case | Ý nghĩa |
| --- | --- |
| ID / Title | Nhận diện và mô tả ngắn gọn |
| Preconditions | Trạng thái cần có trước khi chạy |
| Steps | Các thao tác rõ, đánh số |
| Test data | Username, product, số lượng… |
| Expected result | Kết quả quan sát được, không mơ hồ |
| Actual / Status | Điền khi chạy: Pass, Fail, Blocked |
| Priority / Note | Lý do ưu tiên và thông tin thêm |

### Bước 4 — Thực thi và ghi bằng chứng

1. Xác nhận đúng environment/build/account.
2. Chạy từng bước đúng thứ tự, không bỏ qua precondition.
3. So expected với actual; ghi actual ngay khi thấy khác biệt.
4. Khi fail: chụp ảnh/quay video; lấy console hoặc Network nếu hữu ích.
5. Thử tái hiện ít nhất một lần; thử xác định scope (browser khác? account khác? mạng khác?).
6. Tạo bug report, liên kết test case và ticket liên quan.

### Bước 5 — Retest, regression và test summary

- **Retest:** chạy đúng steps của bug trên bản đã fix để xác nhận actual nay đúng expected.
- **Regression:** chạy các test liên quan vì fix có thể phá vùng khác.
- **Summary:** báo số Pass/Fail/Blocked/Not run, bug còn mở, risk còn lại và recommendation release.

## 2. Bug report chuẩn

![Defect lifecycle](diagrams/defect-lifecycle.svg)

Một bug report tốt cho developer đủ thông tin tái hiện mà không phải đoán.

```text
Title: [Cart] Badge stays at 0 after adding an in-stock product

Environment:
- URL/build: ...
- OS/browser/device: Windows 11, Chrome 126
- Account/test data: standard_user, Backpack

Precondition: User is logged in on Products page.

Steps to reproduce:
1. Click Add to cart for Backpack.
2. Observe the cart icon.

Expected result: Cart badge displays 1 and selected product appears in cart.
Actual result: Cart badge displays 0 while product is not visible in cart.

Severity: High   Priority: High
Attachment: video-cart-badge.mp4, console-error.txt
```

### Severity và Priority

- **Severity** = mức ảnh hưởng kỹ thuật/người dùng. Blocker: không dùng được flow chính; Critical: mất/lộ data hoặc crash lớn; High: chức năng chính sai; Medium/Low: ảnh hưởng nhỏ/cosmetic.
- **Priority** = mức độ business cần sửa sớm. Một lỗi text có thể Low severity nhưng High priority nếu nằm trên trang marketing sắp launch.

Không tự gán tuỳ tiện khi team có quy ước; dùng severity/priority của dự án.

## Bài tập bắt buộc

Làm [Bài thực hành SauceDemo](../10-practice-projects/README.md): ít nhất 12 test case Add to Cart và 3 bug report mô phỏng hoặc bug thực tế.

## Checklist

- [ ] Viết được test plan một trang.
- [ ] Phân biệt scenario với test case.
- [ ] Có test case positive, negative và edge case.
- [ ] Bug report có title, environment, steps, expected, actual, severity, priority, attachment.
- [ ] Biết retest và regression sau fix.
