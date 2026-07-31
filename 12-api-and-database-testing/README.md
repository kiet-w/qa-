# 12 — API & Database Testing

## Khi nào bắt đầu?

Sau chặng 07: đã hiểu HTTP, gửi được GET/POST và đọc request/response trên DevTools.

## Mục tiêu

Kiểm tra được hệ thống qua API và dữ liệu, không chỉ nhìn giao diện UI.

## Backlog học theo thứ tự

1. **Postman nâng cao:** collections, environments, variables, pre-request scripts, tests, collection runner.
2. **API contracts:** schema, required/optional fields, pagination, filtering, sorting, idempotency, error contract.
3. **Authentication & authorization:** Bearer token, session, refresh token, role/permission — chỉ test trong môi trường được phép.
4. **API workflows:** tạo dữ liệu bằng API, kiểm tra UI, cleanup dữ liệu test an toàn.
5. **SQL cơ bản:** SELECT, WHERE, JOIN, GROUP BY, ORDER BY; chỉ đọc dữ liệu ở môi trường được cấp quyền.
6. **Database validation:** đối chiếu request/UI/database, integrity, duplicate, transaction/rollback ở mức khái niệm.
7. **Contract/API automation:** Newman, Playwright API hoặc tool phù hợp sau khi manual API vững.

## Quy tắc an toàn

Không chạy query ghi/xóa trên production; không commit token, cookie, file environment có secret; không thử vượt quyền trên hệ thống không có cho phép rõ ràng.

## Definition of done

- [ ] Có Postman Collection được đặt tên và mô tả rõ.
- [ ] Có test positive/negative/auth/error cho một endpoint demo.
- [ ] Viết được SQL SELECT/JOIN đơn giản trên database training.
- [ ] Giải thích được cách đối chiếu UI → API → database.
