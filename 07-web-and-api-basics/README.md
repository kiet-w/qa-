# 07 — Web & API Basics: hiểu ứng dụng đang giao tiếp ra sao

## Mục tiêu

Bạn đọc được HTML/CSS/JS ở mức cơ bản, hiểu HTTP request/response và gửi được request đơn giản bằng Postman.

![HTTP request response](diagrams/http-request-response.svg)

## 1. Web cơ bản, học vừa đủ cho QA

- **HTML:** cấu trúc trang và semantic elements: form, button, input, label, table.
- **CSS:** màu, spacing, layout, responsive; hữu ích khi báo lỗi visual/compatibility.
- **JavaScript:** sự kiện click/input, validation client-side, DOM; hữu ích khi đọc Console.
- **DOM:** cây element mà trình duyệt render; dùng DevTools Elements để inspect.

Đừng bắt đầu bằng framework phức tạp. Hãy inspect một form login, tìm `input`, `button`, `label`, rồi thử resize màn hình và dùng keyboard Tab.

## 2. HTTP cần biết

| Thành phần | Ý nghĩa |
| --- | --- |
| URL/endpoint | Địa chỉ tài nguyên/API |
| Method | Ý định thao tác: GET, POST, PUT, PATCH, DELETE |
| Headers | Metadata: Content-Type, Authorization, Accept… |
| Params/body | Dữ liệu gửi đi |
| Status code | Kết quả cấp HTTP |
| Response body | Dữ liệu/error server trả về |

Status thường gặp: `200 OK`, `201 Created`, `400 Bad Request`, `401 Unauthenticated`, `403 Forbidden`, `404 Not Found`, `409 Conflict`, `500 Server Error`.

## 3. Bài thực hành Postman từng bước

1. Mở Postman, tạo Collection `QA Learning` và Environment `Demo`.
2. Dùng API công khai, ví dụ `https://jsonplaceholder.typicode.com` (không dùng dữ liệu thật).
3. Gửi `GET /posts/1`; kiểm tra status 200, thời gian response, headers và JSON body.
4. Gửi `POST /posts` với header `Content-Type: application/json` và body mẫu. So sánh status/body với tài liệu API.
5. Thử một request sai: endpoint không tồn tại hoặc body thiếu field (nếu API hỗ trợ) để quan sát error.
6. Lưu request có tên rõ ràng, viết note: mục đích, input, expected status/body, actual.

## 4. API test checklist

- Happy path: valid input, expected status/schema/data.
- Validation: field thiếu, sai type, boundary, duplicate.
- Auth/authz: không token, token hết hạn, role sai (chỉ trên môi trường được phép).
- Error contract: status/message có rõ và không lộ secret/stack trace không?
- Side effect: POST/DELETE có thay đổi dữ liệu đúng một lần không?
- Performance basic: response bất thường chậm? (không tự load test production).

## Checklist

- [ ] Giải thích GET/POST/PUT/PATCH/DELETE.
- [ ] Đọc được request và response trong Network.
- [ ] Gửi được GET và POST demo bằng Postman.
- [ ] Phân biệt 401 với 403.
- [ ] Không đưa production secret/token vào collection hoặc screenshot.
