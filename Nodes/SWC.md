# SWC

Aliases: SWC, Speedy Web Compiler, swc

Type: Frameworks and Tools

## Context / Ngữ cảnh

SWC xuất hiện khi JavaScript/TypeScript project cần compiler/transpiler nhanh cho frontend framework, build pipeline, test transform hoặc bundling. Nó thường nằm trong Next.js, tooling Rust-based hoặc pipeline cần thay Babel/TypeScript transform để tăng tốc.

## Boundary / Ranh giới

### Nó là gì

SWC là compiler/transpiler JavaScript/TypeScript viết bằng Rust. Nó transform syntax hiện đại sang target runtime, xử lý JSX/TS, minify và có thể tham gia bundling tùy toolchain. Giá trị chính là tốc độ và khả năng tích hợp vào framework build.

### Nó không phải là gì

SWC không tự là frontend framework và không thay thế type checking đầy đủ nếu chỉ dùng ở chế độ transpile. Nó cũng không luôn tương thích 100% với plugin Babel/TypeScript edge cases. Khi đổi từ Babel/tsc sang SWC, cần kiểm tra decorator, plugin, sourcemap và transform semantic.

## Core Mechanism / Cơ chế lõi

SWC parse source thành AST, transform theo config như target, module format, JSX, decorator, minify, rồi emit JavaScript và sourcemap. Nó thường chạy bên trong framework/test runner/bundler, nên lỗi có thể xuất hiện như compile pass nhưng runtime behavior khác do transform/config.

## Project Role / Vai trò trong dự án

SWC là node cần mở khi debug build/test nhanh nhưng output lạ, Next.js transform, Jest/Vitest transform, decorator/metadata issue, sourcemap lệch hoặc TypeScript type error không bị bắt. Nó giúp team tách compiler transform khỏi type check và runtime logic.

## Output / Artifact nên có

- SWC config: target, parser syntax, JSX, module, minify, sourcemap
- Type check step riêng nếu dùng TypeScript
- Compatibility note khi thay Babel/tsc plugin
- Test case cho syntax/feature nhạy cảm như decorator, class field, ESM/CJS
- Debug artifact: emitted code/sourcemap khi build behavior sai

## Decision Checklist / Câu hỏi kiểm tra

- SWC đang được gọi trực tiếp hay qua framework/tool nào?
- Target runtime/browser có khớp output không?
- TypeScript có được type check riêng không?
- Có plugin/Babel behavior nào không tương thích không?
- Sourcemap có đủ debug không?
- Module output ESM/CJS có khớp runtime/test runner không?
- Minify có làm đổi behavior edge case không?

## Failure Modes / Cách nó gây lỗi

- Transpile pass nhưng type error không bị chặn.
- Decorator/metadata/class field transform khác Babel/tsc làm runtime lỗi.
- Sourcemap lệch làm stack trace khó đọc.
- ESM/CJS transform sai làm import/export lỗi trong test hoặc production.
- Minify transform gây bug khó tái hiện.
- Framework update đổi SWC config mặc định làm build behavior thay đổi.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ dùng framework mặc định ổn có thể không cần chạm SWC config.
- Không nên đổi compiler chỉ để nhanh hơn nếu compatibility/test chưa đủ.
- Không nên coi SWC là thay thế hoàn toàn cho type checker hoặc integration test.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì SWC transform JavaScript/TypeScript.
- [[Frontend Framework]] vì nhiều framework dùng SWC trong build pipeline.
- [[esbuild]] vì cả hai đều là tool transform/bundle tốc độ cao.
- [[CI]] vì compiler/build config cần chạy ổn định trong pipeline.
- [[npm]] vì SWC thường đi qua package/script trong JavaScript project.

## Liên quan rộng

- Compiler tooling
- Transpilation
- Build performance
- TypeScript toolchain

## Keywords / Từ khóa tìm kiếm

- SWC
- Speedy Web Compiler
- swc
- JavaScript compiler
- TypeScript transpiler
- JSX transform
- Rust compiler tool
- SWC config
- decorator transform
- sourcemap
- ESM CJS
- SWC debugging

## Source trace

- SWC documentation
- Next.js compiler documentation
