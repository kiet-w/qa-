# 02 — QA Foundations: cách QA suy nghĩ

## Mục tiêu

Bạn có thể phân biệt QA và Testing; chọn được black-box, white-box hoặc gray-box; biết dựa vào đâu để kết luận hành vi đúng hay sai.

![QA approaches](diagrams/testing-approaches.svg)

## 1. QA khác Testing như thế nào?

| QA (Quality Assurance) | Testing |
| --- | --- |
| Tập trung phòng ngừa lỗi trong toàn bộ quy trình. | Hoạt động kiểm tra để tìm hoặc xác minh lỗi. |
| Bao gồm requirement review, strategy, quy trình, giao tiếp và cải tiến. | Bao gồm thiết kế/running test, ghi nhận kết quả, báo lỗi. |
| Câu hỏi: “Làm sao sản phẩm ít lỗi hơn?” | Câu hỏi: “Sản phẩm đang lỗi ở đâu?” |

Testing là một phần của QA; không phải toàn bộ QA.

## 2. QA mindset và AI mindset

Trước khi test một feature, hãy hỏi:

1. Người dùng chính là ai và muốn hoàn thành việc gì?
2. Luồng thành công là gì? Điều kiện nào cần có trước đó?
3. Input rỗng, sai định dạng, quá dài, trùng hoặc độc hại thì sao?
4. Nếu mất mạng, refresh, hết phiên đăng nhập hoặc bấm nút liên tục thì sao?
5. Dữ liệu có bị mất, lộ hoặc thay đổi sai không?
6. Requirement nào còn mơ hồ? Cần hỏi BA/PO/Designer/Developer điều gì?

**AI mindset:** dùng AI để brainstorm và viết bản nháp, không dùng AI thay cho việc hiểu feature. AI không nhìn thấy business rule thật nếu bạn không cung cấp nó.

## 3. Ba testing approach

- **Black box:** chỉ nhìn input và output. Ví dụ nhập username/password, kiểm tra điều hướng và thông báo lỗi. Đây là điểm bắt đầu của Manual QA.
- **White box:** nhìn vào cấu trúc code, nhánh điều kiện, unit test, coverage. Developer dùng nhiều hơn; QA cần hiểu để trao đổi.
- **Gray box:** biết một phần API, database, log hoặc kiến trúc nhưng vẫn test qua UI/API. Ví dụ đọc Network để biết request nào thất bại.

## 4. Test oracle: căn cứ kết luận đúng/sai

Oracle theo thứ tự tin cậy nên ưu tiên:

1. Acceptance criteria, requirement hoặc business rule đã được xác nhận.
2. User story, API contract, thiết kế Figma và content đã duyệt.
3. Trao đổi với PO/BA/Designer/Developer và câu trả lời được ghi lại.
4. Luật/chuẩn áp dụng: bảo mật, accessibility, quy định ngành.
5. Hành vi phiên bản cũ hoặc sản phẩm tương tự — chỉ dùng như tín hiệu, không tự coi là requirement.
6. Gợi ý của AI — chỉ là oracle phụ; phải xác minh lại.

## Các bước áp dụng khi nhận feature mới

1. Đọc user story và acceptance criteria; tô đậm từ như “must”, “only”, “always”.
2. Liệt kê input, output, role người dùng, dữ liệu và tích hợp liên quan.
3. Tìm oracle cho từng expected result. Không rõ thì ghi câu hỏi thay vì tự đoán.
4. Chọn approach test phù hợp: UI black-box, API gray-box, hoặc review logic với dev.
5. Viết danh sách rủi ro trước khi viết test case chi tiết.

## Checklist

- [ ] Giải thích QA vs Testing bằng ví dụ login.
- [ ] Phân biệt Black/White/Gray box.
- [ ] Liệt kê ít nhất 4 oracle cho một feature.
- [ ] Viết 5 câu hỏi QA mindset cho feature Add to Cart.
