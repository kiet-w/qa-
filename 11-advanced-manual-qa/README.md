# 11 — Advanced Manual QA

## Khi nào bắt đầu?

Sau khi bạn tự viết được test case/bug report rõ ràng, biết dùng DevTools cơ bản, và đã hoàn thành ít nhất một project ở chặng 10.

## Mục tiêu

Nâng từ “chạy test theo case” thành người biết thiết kế coverage, quản lý rủi ro release và khám phá lỗi có hệ thống.

## Backlog học theo thứ tự

1. **Test design techniques:** equivalence partitioning, boundary value analysis, decision table, state transition, pairwise testing.
2. **Requirement review:** phát hiện ambiguity, conflict, missing acceptance criteria trước khi code.
3. **Traceability:** liên kết requirement → test case → test run → bug → release.
4. **Exploratory testing sâu:** charter, timebox, note-taking, debrief, biến phát hiện thành regression cases.
5. **Release testing:** entry/exit criteria, smoke suite, risk-based regression, go/no-go recommendation.
6. **Cross-browser & responsive:** browser matrix, device/viewport matrix, compatibility evidence.
7. **Localization/time/date:** timezone, currency, language, encoding, daylight saving khi project cần.

## Folder gợi ý khi mở rộng

Tạo từng folder con khi bắt đầu học thật, ví dụ `01-boundary-and-equivalence/`, `02-decision-tables/`, `03-exploratory-charters/`. Mỗi folder nên có `README.md`, `examples/`, `exercises/` và `evidence/`.

## Definition of done

- [ ] Có test design cho một feature bằng ít nhất 3 kỹ thuật.
- [ ] Có exploratory charter và debrief note.
- [ ] Có release summary nêu rõ risk còn lại, không chỉ số lượng Pass/Fail.
