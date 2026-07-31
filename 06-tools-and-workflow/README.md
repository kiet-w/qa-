# 06 — Công cụ & Workflow: thu thập bằng chứng và quản lý công việc

## Mục tiêu

Bạn biết dùng Chrome DevTools căn bản, tổ chức test case bằng Sheet và quản lý bug/task trên Jira hoặc Trello.

## 1. Chrome DevTools: quy trình điều tra bug

![DevTools investigation](diagrams/devtools-investigation.svg)

| Tab | Dùng để làm gì | Khi nào đưa vào bug report |
| --- | --- | --- |
| Elements | Xem DOM, CSS, text/attribute đang render | Lỗi layout/text/element |
| Console | Xem JavaScript errors/warnings | Trang trắng, click không phản hồi |
| Network | Xem request, status, headers, payload, response, timing | Lỗi API, timeout, dữ liệu sai |
| Application | Cookie, local storage, session storage | Lỗi login/session/cache |

### Các bước điều tra không phá dữ liệu

1. Tái hiện bug trong Incognito hoặc profile sạch nếu nghi cache/extension.
2. Mở DevTools (`F12`), chọn Console và Network; bật `Preserve log` khi cần theo dõi điều hướng.
3. Lặp lại bước gây lỗi. Ở Network, lọc `Fetch/XHR`, xem status code và response.
4. Ghi thông tin hữu ích: URL request, status, error message, thời điểm; che token, cookie, email và dữ liệu nhạy cảm trước khi đính kèm.
5. Chỉ kết luận nguyên nhân khi có bằng chứng hoặc developer xác nhận. QA có thể báo “API returns 500” thay vì đoán “database hỏng”.

## 2. Google Sheets/Excel

Tạo các tab sau:

- `Test Cases`: ID, title, preconditions, steps, data, expected, actual, status, priority.
- `Test Run`: build, environment, ngày test, tổng pass/fail/blocked, liên kết bugs.
- `Bug Log`: Bug ID, title, severity, priority, status, owner, link evidence.
- `Glossary`: khái niệm và ví dụ do bạn tự viết.

Quy tắc: không bỏ actual result trống khi test fail; không sửa lịch sử test để “đẹp số”.

## 3. Jira/Trello workflow

Jira thường có Issue type: Story, Task, Bug, Epic. Trello có thể mô phỏng bằng card và list.

### Board thực hành

Tạo các cột: `Backlog` → `Ready for Test` → `Testing` → `Bug Found` → `Ready for Retest` → `Done`.

Khi tạo Bug card/ticket:

1. Chọn title theo mẫu `[Feature] observed behavior under condition`.
2. Điền đủ bug report chặng 04; gắn environment/build và attachment.
3. Gắn severity, priority, assignee và link test case.
4. Không đóng bug ngay khi developer nói “đã fix”; chuyển sang Retest và tự xác minh.

## Checklist

- [ ] Dùng Console và Network để ghi evidence cho một lỗi demo.
- [ ] Có Sheet với Test Cases, Test Run, Bug Log.
- [ ] Tạo board và đi một bug qua New → Retest → Done.
- [ ] Biết che secret trước khi attach log/screenshot.
