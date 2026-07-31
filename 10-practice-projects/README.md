# 10 — Dự án thực hành & Portfolio

## Mục tiêu

Biến kiến thức thành bằng chứng: test case, test run, bug report, ticket workflow và phần giải thích cách bạn dùng AI có review.

## Project 1 — SauceDemo: Login và Add to Cart

Website: https://www.saucedemo.com. Đây là web demo; chỉ dùng tài khoản test được công khai trên trang.

![Add-to-cart test flow](diagrams/add-to-cart-test-flow.svg)

### Deliverables tối thiểu

1. `test-plan.md`: scope, out-of-scope, risks, environment, data, exit criteria.
2. `test-cases.csv` hoặc Google Sheet: tối thiểu 20 test case (Login 8, Add to Cart 12).
3. `test-run-summary.md`: build/date/environment, pass/fail/blocked, known risk.
4. `bug-reports/`: tối thiểu 3 report. Không bịa lỗi là lỗi thật; bạn có thể ghi **sample/simulated** để luyện format.
5. `evidence/`: ảnh/video/log đã che dữ liệu nhạy cảm.
6. `ai-review.md`: prompt, output tóm tắt, các test bạn xóa/sửa/thêm và lý do.

### Thứ tự thực hiện chi tiết

1. Đọc app như user: login, products, cart, checkout. Ghi flow và các điểm không rõ.
2. Viết test plan nhỏ. Risk nên bao gồm login, cart persistence, quantity, pricing, access/session.
3. Viết scenario trước: valid/invalid login; add/remove item; nhiều item; refresh; cart badge; navigation.
4. Dùng AI tạo draft test cases theo prompt chặng 09. Đánh dấu assumption AI đưa ra.
5. Review draft: đối chiếu hành vi thật, thêm dữ liệu và expected cụ thể, gắn priority.
6. Chạy từng test ở Chrome; cập nhật Pass/Fail/Blocked và actual result.
7. Với mỗi fail: tái hiện, thu evidence, tạo bug report đầy đủ. Nếu không tái hiện được, ghi rõ “Not reproducible” và điều kiện đã thử.
8. Tạo board Jira/Trello mô phỏng flow ticket; đưa bug qua New, In progress, Ready for retest, Done (chỉ Done khi đã retest).
9. Viết summary: coverage, kết quả, bugs, rủi ro chưa test và “release recommendation” có lý do.
10. Commit portfolio lên GitHub; README portfolio chỉ dùng dữ liệu demo, không có token/password.

## Project 2 — API demo với Postman

Dùng JSONPlaceholder hoặc API sandbox được phép. Tạo collection có GET/POST, assertions manual cho status/body, và một report ngắn về negative case. Không thử tấn công API công cộng, không load test production.

## Tiêu chí tự đánh giá

| Mức | Dấu hiệu |
| --- | --- |
| Chưa đạt | Test case mơ hồ, expected không có oracle, bug không tái hiện được |
| Đạt trainee | Có scope/risk, case rõ, evidence, biết retest và giải thích AI review |
| Tốt | Ưu tiên theo risk, có API/DevTools evidence, summary nêu open risk thực tế |

## Checklist portfolio

- [ ] Có README mô tả mục tiêu và môi trường test.
- [ ] Có test plan, test cases, test execution và bug reports.
- [ ] Có evidence an toàn.
- [ ] Có phần chứng minh review AI output.
- [ ] Có GitHub repo sạch, dễ đọc, không chứa secret.
