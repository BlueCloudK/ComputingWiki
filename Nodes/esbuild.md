# esbuild

Aliases: esbuild, esbuild bundler

Type: Frameworks and Tools

## Context / Ngữ cảnh

esbuild xuất hiện khi JavaScript/TypeScript project cần bundle, transpile hoặc minify rất nhanh cho frontend, backend tooling hoặc library build. Nó thường nằm bên dưới tool như Vite hoặc được dùng trực tiếp trong build script.

## Boundary / Ranh giới

### Nó là gì

esbuild là JavaScript bundler/transpiler/minifier viết bằng Go, nổi bật vì tốc độ cao. Nó có thể bundle module, transform TypeScript/JSX, target browser/runtime, generate sourcemap, define env constant và minify output.

### Nó không phải là gì

esbuild không phải type checker TypeScript đầy đủ và không thay thế toàn bộ frontend framework. Nó cũng không phải luôn tương đương Webpack/Rollup về plugin ecosystem hoặc edge-case bundling. Nếu cần type safety, vẫn cần `tsc` hoặc tool type check riêng.

## Core Mechanism / Cơ chế lõi

esbuild đọc entry points, resolve import, transform syntax theo target, tree-shake phần không dùng, bundle dependency nếu cấu hình, rồi output JS/CSS/sourcemap. Config quan trọng gồm platform, target, format, external, define, loader, splitting và sourcemap.

## Project Role / Vai trò trong dự án

esbuild là node cần mở khi debug build nhanh nhưng behavior runtime sai, bundle thiếu dependency, env define sai, sourcemap lệch, ESM/CJS mismatch hoặc TypeScript compile nhưng type error không bị bắt. Nó giúp team tách vấn đề build transform với type check/test/runtime.

## Output / Artifact nên có

- Build config: entry, outfile/outdir, platform, target, format
- External dependency rule và bundle strategy
- Sourcemap/minify/define config theo environment
- Type check step riêng nếu dùng TypeScript
- Bundle inspection/debug note khi output sai hoặc quá lớn

## Decision Checklist / Câu hỏi kiểm tra

- Build target là browser, Node.js hay neutral/library?
- Có cần bundle dependency hay mark external?
- TypeScript có được type check riêng không?
- ESM/CJS format có khớp runtime/package consumer không?
- Env variable/define có thay đổi behavior production không?
- Sourcemap có đủ debug production/staging không?
- Plugin/loader có xử lý CSS/asset đúng không?

## Failure Modes / Cách nó gây lỗi

- TypeScript transform pass nhưng type error không bị chặn.
- Mark external sai làm runtime thiếu package.
- Bundle dependency sai target làm code browser chứa Node.js API hoặc ngược lại.
- Define env sai làm dead-code elimination cắt nhầm branch.
- Sourcemap thiếu/lệch làm debug production khó.
- ESM/CJS output không khớp consumer gây import error.

## Khi nào chưa cần hoặc dễ over-engineer

- App dùng Vite/Next/Nuxt đã wrap build tool tốt thì hiếm khi cần config esbuild trực tiếp.
- Không nên tự build pipeline esbuild phức tạp nếu framework build đủ dùng.
- Không nên dùng esbuild như type checker duy nhất cho TypeScript project nghiêm túc.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì esbuild transform/bundle JavaScript.
- [[Frontend Framework]] vì nhiều framework/toolchain dùng bundler/transpiler phía dưới.
- [[npm]] vì esbuild thường chạy qua npm scripts/package dependency.
- [[CI]] vì build esbuild cần chạy reproducibly trong pipeline.
- [[SWC]] vì SWC là công cụ transform JS/TS tương tự ở một số use case.

## Liên quan rộng

- Bundling
- Transpilation
- Minification
- Build performance

## Keywords / Từ khóa tìm kiếm

- esbuild
- esbuild bundler
- JavaScript bundler
- TypeScript transpile
- JSX transform
- sourcemap
- minify
- tree shaking
- ESM CJS
- external dependency
- esbuild debugging

## Source trace

- esbuild documentation
