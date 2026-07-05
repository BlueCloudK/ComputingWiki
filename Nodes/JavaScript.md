# JavaScript

Aliases: JS, ECMAScript, ngôn ngữ JavaScript

Type: Programming Language

## Context / Ngữ cảnh

JavaScript xuất hiện khi cần viết logic chạy trong browser, Node.js, frontend tooling, serverless function hoặc automation script. Nó là ngôn ngữ lõi của web runtime, đồng thời có nhiều behavior đặc thù dễ gây lỗi nếu chỉ nhìn như ngôn ngữ script đơn giản.

## Boundary / Ranh giới

### Nó là gì

JavaScript là ngôn ngữ lập trình dynamic, prototype-based, garbage-collected, single-threaded event-loop oriented trong nhiều runtime. Nó hỗ trợ function first-class, closure, promise/async-await, module system, object/prototype model và chạy trong môi trường như browser hoặc Node.js với API khác nhau.

### Nó không phải là gì

JavaScript không phải TypeScript, React hay Node.js, dù chúng liên quan chặt. TypeScript thêm type layer compile-time; React là frontend framework; Node.js là runtime server-side. JavaScript cũng không đảm bảo type safety hoặc concurrency safety nếu không có discipline/tooling/test phù hợp.

## Core Mechanism / Cơ chế lõi

Code JavaScript chạy trên call stack, async work được runtime/browser/Node API xử lý rồi callback/promise được đưa vào task/microtask queue qua event loop. Object dùng prototype chain. Module/import quyết định dependency. Type coercion, closure, `this`, promise rejection và mutation là các điểm thường gây bug.

## Project Role / Vai trò trong dự án

JavaScript là node cần mở khi debug frontend behavior, async race, promise error, browser API, Node.js service, build tool hoặc package dependency. Nó giúp team phân biệt lỗi language semantics, framework abstraction, runtime API và network/backend issue.

## Output / Artifact nên có

- Runtime note: browser, Node.js, edge runtime hay build-time script
- Async flow diagram nếu logic có promise, event, timer hoặc API call
- Module boundary và package dependency note
- Error handling policy: thrown error, rejected promise, async boundary
- Test case cho type coercion, async race, edge value và browser/runtime compatibility

## Decision Checklist / Câu hỏi kiểm tra

- Code này chạy ở browser, Node.js, worker hay build tool?
- Async flow dùng promise/async-await đúng chỗ chưa?
- Có unhandled rejection hoặc error bị swallow không?
- Type coercion/null/undefined có thể tạo bug không?
- Closure hoặc stale reference có làm state sai không?
- Module/dependency có chạy được ở target runtime không?
- Có cần TypeScript/lint/test để giảm lỗi dynamic type không?

## Failure Modes / Cách nó gây lỗi

- Async race làm request cũ ghi đè state mới.
- Unhandled promise rejection bị bỏ sót hoặc crash runtime.
- `this` binding sai làm method mất context.
- Type coercion như `==`, number/string/null tạo behavior bất ngờ.
- Mutation object/array làm state framework không nhận đổi hoặc đổi ngoài ý muốn.
- Browser API và Node.js API bị nhầm, code chạy local nhưng fail production/runtime khác.
- Package dependency ESM/CJS mismatch làm build/runtime lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ có thể dùng JavaScript đơn giản, nhưng vẫn nên rõ runtime và error handling.
- Không nên thêm framework/library lớn để né vài dòng JS nếu browser API đủ dùng.
- Không nên dựa vào TypeScript như thay thế hoàn toàn cho runtime validation/test.

## Gồm những gì

- [[Event Loop]]

## Nối mạnh

- [[Event Loop]] vì async behavior của JavaScript phụ thuộc event loop/task/microtask.
- [[Node.js]] vì Node.js là runtime server-side quan trọng của JavaScript.
- [[Frontend Framework]] vì framework frontend chạy trên JavaScript runtime.
- [[CSR]] vì client-side rendering phụ thuộc JavaScript trong browser.
- [[Unit Test]] vì JS dynamic behavior cần test để bắt regression.

## Liên quan rộng

- Browser runtime
- Frontend engineering
- Backend scripting
- Package ecosystem

## Keywords / Từ khóa tìm kiếm

- JavaScript
- JS
- ECMAScript
- ngôn ngữ JavaScript
- async await
- promise
- closure
- prototype chain
- event loop
- type coercion
- this binding
- ESM
- CommonJS
- JavaScript debugging

## Source trace

- MDN JavaScript Guide
- ECMAScript specification
