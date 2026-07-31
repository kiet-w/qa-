# Fundamentals Before HTML, CSS, JavaScript and Automation

Day la phan nen tang can hoc truoc khi di vao HTML, CSS, JavaScript, Playwright, Cypress hoac automation. Thu tu duoi day uu tien logic hoc: cai sau dua tren cai truoc.

## 1. Computer and Internet Basics

Nguoi moi nen dam bao minh lam duoc cac viec co ban sau:

- Su dung may tinh thanh thao.
- Dung Google Chrome thanh thao.
- Biet tim kiem Google hieu qua.
- Biet tai, giai nen va cai phan mem.
- Tao tai khoan GitHub.
- Biet chup man hinh hoac quay video ngan de dinh kem bug report.

## 2. QA Mindset and AI Mindset

### What is Quality Assurance?

Quality Assurance la qua trinh dam bao chat luong san pham bang cach ngan ngua loi tu dau: quy trinh, requirement, review, test strategy, communication va cai tien lien tuc.

Testing la mot hoat dong trong QA, tap trung vao viec tim loi hoac xac minh san pham co hoat dong dung hay khong.

Noi ngan gon:

- QA: lam sao de san pham it loi hon tu ca quy trinh.
- Testing: kiem tra san pham de tim loi.

### QA Mindset

QA mindset la tu duy luon dat cau hoi:

- Cai gi co the sai?
- User that se dung tinh nang nay nhu the nao?
- Neu input sai, mat mang, refresh trang, dang nhap het han thi sao?
- Neu requirement khong ro thi nen hoi lai ai?

### AI Mindset

AI khong thay the QA mindset. AI chi giup tang toc qua trinh nghi y tuong, viet test case, tong hop bug report va giai thich log.

Neu ban chua hieu feature, AI de tao ra test case rat generic. Vi vay AI output luon can con nguoi review lai.

## 3. Testing Approaches

### Black Box Testing

Kiem thu qua input va output, khong can nhin code. Vi du: nhap username/password vao form login va quan sat ket qua.

AI ho tro: dua user story/spec cho AI de generate test case nhap, sau do QA review lai theo app that.

### White Box Testing

Kiem thu dua tren cau truc code ben trong. Thuong lien quan unit test, branch coverage, condition coverage.

AI ho tro: AI code review co the goi y test case dua tren nhanh logic trong code, nhung QA manual moi chi can hieu khai niem.

### Gray Box Testing

Ket hop black box va white box. QA biet mot phan ve API, database, log hoac flow he thong, nhung van test chu yeu qua UI/API.

AI ho tro: phan tich log, error trace, network response de goi y vung can test ky hon.

## 4. Test Oracles and Test Prioritization

### Test Oracles

Test oracle la nguon giup ban xac dinh ket qua dung hay sai.

Nguon oracle co the la:

- Requirement document
- User story
- Acceptance criteria
- Design/Figma
- Business rule
- San pham tuong tu
- Y kien Product Owner, BA, Designer hoac Developer

AI co the lam oracle phu khi spec khong ro, vi du hoi: "Theo UX thong thuong, login sai mat khau nen hien thong bao nhu the nao?".

Khong bao gio dung AI lam oracle duy nhat, vi AI co the hallucinate hoac doan sai nghiep vu.

### Test Prioritization

Khi khong du thoi gian test het, uu tien theo:

- Chuc nang quan trong voi business.
- Flow duoc user dung nhieu.
- Vung moi sua code.
- Vung tung co bug.
- Rui ro cao: payment, auth, data loss, security.

AI ho tro: hoi AI tao risk list cho feature, roi QA tu sap xep lai theo context that.

## 5. Testing Techniques

### Functional vs Non-Functional Testing

Functional Testing kiem tra tinh nang co lam dung hay khong.

Non-Functional Testing kiem tra chat luong phi chuc nang: performance, security, usability, accessibility, compatibility.

### Smoke Testing

Test nhanh cac chuc nang cot loi sau khi co build/deploy moi de xem build co "song" khong.

Vi du: mo app, login, xem dashboard, them san pham vao gio hang.

### Sanity Testing

Test nhanh sau mot thay doi nho hoac bug fix de xem phan vua sua co hoat dong dung khong.

Sanity hep hon smoke.

### Regression Testing

Chay lai cac test case cu sau khi code thay doi de dam bao khong pha chuc nang da dung.

AI ho tro: cac cong cu self-healing automation nhu Testim, mabl, Applitools co the giup giam viec sua script khi UI doi nhe.

### Exploratory Testing

Test khong theo script co dinh, dua vao truc giac, kinh nghiem va muc tieu tim loi.

AI ho tro: goi y edge cases hoac cach "pha app" ma QA co the bo sot.

### UAT

User Acceptance Testing la giai doan nguoi dung, khach hang hoac business stakeholder xac nhan san pham dap ung nhu cau that truoc khi release.

### Unit Testing

Test tung ham hoac module nho nhat. Thuong do developer viet, thuoc white box testing.

### Integration Testing

Test nhieu module ghep lai voi nhau co hoat dong dung khong.

Vi du: UI goi API, API ghi database, database tra du lieu dung.

### Load, Performance and Stress Testing

- Load Testing: kiem tra he thong voi luong tai du kien.
- Performance Testing: do toc do, response time, throughput.
- Stress Testing: day he thong vuot nguong de xem gioi han va cach no fail.

AI ho tro: phan tich log va metrics de goi y diem nghen.

### Security Testing

Kiem tra rui ro bao mat nhu authentication, authorization, data exposure, SQL injection, XSS, CSRF.

AI ho tro: cong cu nhu Snyk, GitHub Advanced Security, CodeQL co the phat hien dependency/code risk, nhung van can con nguoi xac minh.

### Accessibility Testing

Kiem tra app co dung duoc voi nguoi khuyet tat hay khong.

Vi du: contrast mau, keyboard navigation, screen reader labels, form error message ro rang.

## 6. Manual Testing Core

### Test Planning

Xac dinh scope test, rui ro, thoi gian, nguon luc, moi truong test va tieu chi pass/fail.

AI ho tro: hoi AI feature nay co rui ro gi, can test nhung luong nao.

### Test Cases and Test Scenarios

Test Scenario la y tuong test cap cao.

Test Case la huong dan chi tiet hon, thuong gom:

- Test Case ID
- Title
- Preconditions
- Steps
- Test Data
- Expected Result
- Actual Result
- Status
- Note

AI ho tro: generate draft test case tu user story/spec. QA phai review va sua lai theo app that.

### Verification vs Validation

Verification: co xay dung dung theo spec khong?

Validation: co phai thu user that can khong?

Vi du:

- Verification: nut "Add to cart" them dung san pham vao gio theo requirement.
- Validation: flow mua hang co de hieu va phu hop voi cach user that mua hang khong.

### Compatibility Testing

Kiem tra tren nhieu browser, thiet bi, OS va do phan giai.

Vi du: Chrome, Edge, Safari; desktop, tablet, mobile.

### TDD

Test-Driven Development la cach developer viet test truoc, sau do moi viet code de pass test. QA khong nhat thiet phai viet TDD luc dau, nhung nen hieu de phoi hop voi developer.

## 7. Bug Report

Mot bug report tot giup developer tai hien loi nhanh va sua dung loi.

Thanh phan can co:

- Title: ngan gon, ro loi.
- Steps to Reproduce: cac buoc tai hien theo thu tu.
- Expected Result: ket qua mong doi.
- Actual Result: ket qua thuc te.
- Severity: muc do anh huong ky thuat/nguoi dung.
- Priority: muc do uu tien sua theo business.
- Environment: OS, browser, app version, device.
- Attachment: screenshot, video, console log, network log neu co.

Vi du format:

```text
Title: Login shows blank page after entering valid credentials

Environment:
- OS: Windows 11
- Browser: Chrome 126
- App: saucedemo.com

Steps to Reproduce:
1. Open https://www.saucedemo.com
2. Enter valid username
3. Enter valid password
4. Click Login

Expected Result:
User is redirected to the Products page.

Actual Result:
The page becomes blank and no product list is displayed.

Severity: High
Priority: High

Attachment:
- screenshot-login-blank-page.png
```

AI ho tro: dua ghi chu loi tho cho AI de format thanh bug report chuan. Sau do QA kiem tra lai steps, expected, actual va severity.

## 8. SDLC, STLC and Agile

### SDLC

Software Development Life Cycle la vong doi phat trien phan mem.

Cac giai doan pho bien:

1. Requirement
2. Design
3. Development
4. Testing
5. Deployment
6. Maintenance

### STLC

Software Testing Life Cycle la vong doi kiem thu phan mem.

Cac giai doan pho bien:

1. Requirement Analysis
2. Test Planning
3. Test Case Design
4. Test Environment Setup
5. Test Execution
6. Defect Reporting
7. Test Closure

### Delivery Models

Waterfall: lam tuan tu, xong giai doan nay moi sang giai doan tiep theo.

V-Model: moi giai doan development co giai doan testing tuong ung.

Agile: chia nho cong viec, lap lai nhanh, nhan feedback lien tuc.

### Scrum Basics

- Sprint: chu ky lam viec co dinh, thuong 1-2 tuan.
- User Story: mo ta nhu cau tu goc nhin user.
- Product Backlog: danh sach viec can lam.
- Sprint Backlog: viec team cam ket trong sprint.
- Daily Standup: hop ngan moi ngay.
- Sprint Review: demo ket qua.
- Retrospective: nhin lai cach lam viec de cai tien.

### Kanban, XP and SAFe

Kanban: quan ly cong viec theo flow lien tuc tren board, khong bat buoc sprint.

XP: Extreme Programming, tap trung chat luong code qua TDD, pair programming, refactoring.

SAFe: Agile o quy mo lon cho nhieu team trong to chuc.

AI ho tro: Jira/Trello AI co the tom tat ticket, goi y priority, viet acceptance criteria hoac test case nhap.

## 9. Tools to Know Early

| Tool | Priority | Why |
| --- | --- | --- |
| Google Chrome + DevTools | Required | Test UI, inspect elements, console, network |
| Excel / Google Sheets | Required | Write manual test cases |
| Jira / Trello | Recommended early | Manage tickets, tasks, bugs |
| VS Code | Recommended | Useful later for automation and reading code |
| Postman | Recommended | API testing basics |
| GitHub | Good to have | Important for automation and project collaboration |
| TestRail / qTest / Zephyr / TestLink | Later | Centralized test case management |

## 10. Interview Angle for AI-Powered QA Trainee

Hay chuan bi cau tra loi cho cau hoi:

Ban dung AI o buoc nao trong quy trinh test, va ban kiem chung ket qua AI dua ra nhu the nao?

Cau tra loi tot nen co y:

- Dung AI de brainstorm risk va edge case.
- Dung AI de generate draft test case tu user story.
- Dung AI de format bug report ro rang hon.
- Dung AI de giai thich console/network error.
- Khong tin AI 100%.
- Luon doi chieu voi requirement, acceptance criteria, app thuc te va team member lien quan.

## 11. Practice Exercise: Add To Cart

Prompt mau de dung AI:

```text
You are a QA assistant. Generate manual test cases for an add-to-cart feature.

Context:
- User can view product list.
- User can add one or more products to cart.
- Cart badge should update after adding product.
- User can open cart and see selected products.

Please output:
- Positive test cases
- Negative test cases
- Edge cases
- Columns: ID, Title, Preconditions, Steps, Test Data, Expected Result, Priority
```

Viec cua QA sau khi AI tra loi:

- Xoa test case khong dung voi app that.
- Them test case lien quan business rule that.
- Chinh expected result cho ro rang.
- Gan priority dua tren rui ro.
- Chay test tren app va ghi actual result.
