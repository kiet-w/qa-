# 14 — Automation Engineering

## Khi nào bắt đầu?

Sau khi xong chặng 08 và có vài UI/API tests ổn định chạy local. Đây là giai đoạn xây hệ thống test, không chỉ viết một script.

## Backlog học theo thứ tự

1. **Project structure:** config, fixtures, test data, page/component objects hoặc screenplays phù hợp.
2. **Reliable locators:** accessibility role, label, test id; locator convention với developer.
3. **Test isolation:** independent data, setup/teardown, tránh shared state và test-order dependency.
4. **Assertions & waits:** explicit meaningful assertions, wait for state not arbitrary sleep.
5. **Debugging:** traces, screenshots, videos, logs, retry policy; phân tích flaky tests.
6. **Parallel execution:** shard/worker, test data collision, runtime trade-off.
7. **CI/CD:** chạy smoke trên pull request, regression theo lịch; secrets quản lý qua CI secret store.
8. **Reporting & quality signals:** report, trend, failure ownership, flaky rate, suite runtime.
9. **Code review:** readability, deterministic test, duplication, maintainability.

## Definition of done

- [ ] Có test project chạy lặp lại ổn định.
- [ ] Có README hướng dẫn chạy local và CI.
- [ ] Có report/traces khi fail.
- [ ] Không commit secrets hoặc hard-code production data.
