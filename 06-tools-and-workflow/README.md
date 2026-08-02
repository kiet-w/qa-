# 06 — Tools & Workflow: Công Cụ & Quản Lý Bug

## Mục tiêu
Thành thạo công cụ Chrome DevTools cho mục đích QA, quản lý bug trên Jira/Trello, làm quen với TestRail và Docker test environment.

---

## 1. Chrome DevTools qua góc nhìn QA

- **Console Tab:** Phát hiện các lỗi JavaScript ẩn (Uncaught TypeError, Red Console Errors).
- **Network Tab:** Check API Request/Response status (200, 400, 500), payload gửi đi, response data, và timing latency.
- **Application Tab:** Kiểm tra LocalStorage, SessionStorage, Cookies (Verify Token, Session Expiry).
- **Lighthouse Tab:** Audit nhanh chỉ số Performance, Accessibility (a11y), SEO.

---

## 2. Quản lý Bug trên Jira / Trello

- **Jira Workflow:** `To Do ➔ In Progress ➔ Ready for QA ➔ In QA ➔ Done (hoặc Reopened)`.
- **Bug Ticket Best Practices:** Đính kèm screenshot/video, ghi rõ Build Version, Environment, và các bước reproduction.

---

## 3. Test Management Tools (TestRail)

- Quản lý Repository Test Cases theo cây thư mục.
- Tạo các **Test Runs** cho từng phiên bản release.
- Ghi nhận trạng thái: `Passed`, `Failed`, `Blocked`, `Retest`.

---

## 4. Docker cho QA Test Environment

Chạy ứng dụng và database isolated trong container để đảm bảo môi trường test đồng nhất giữa Local và CI:
```bash
docker-compose -f docker-compose.test.yml up -d
```
