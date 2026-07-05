# Webpack

Aliases: Webpack

Type: Frameworks and Tools

## Context / Ngữ cảnh

Webpack xuất hiện khi JavaScript/frontend project cần bundle nhiều module, asset, loader và plugin thành output phù hợp browser hoặc runtime mục tiêu.

## Boundary / Ranh giới

### Nó là gì

Webpack là module bundler. Nó xây dependency graph từ entry point, xử lý module/asset qua loader/plugin và emit bundle/output files.

### Nó không phải là gì

Webpack không phải frontend framework và không tự quyết định UI architecture. Nó là build tool cho module, asset và optimization pipeline.

## Core Mechanism / Cơ chế lõi

Webpack bắt đầu từ entry, resolve import/module, áp loader cho file type, chạy plugin ở build lifecycle, rồi tạo bundle/chunk/asset theo config mode, target và optimization.

## Project Role / Vai trò trong dự án

Dùng node này khi debug bundle size, loader config, module resolution, asset path, code splitting, sourcemap hoặc build khác dev/prod.

## Output / Artifact nên có

- `webpack.config`
- Entry/output config
- Loader/plugin list
- Module resolution/alias note
- Bundle analysis report nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Entry point và output path có đúng không?
- Loader nào xử lý file type nào?
- Alias/module resolution có khớp IDE/test không?
- Bundle/chunk size có được đo không?
- Dev/prod config có khác gì nguy hiểm không?

## Failure Modes / Cách nó gây lỗi

- Loader order sai làm build fail hoặc output sai.
- Alias khác giữa build/test/IDE.
- Bundle quá lớn nhưng không được split.
- Asset public path sai sau deploy.
- Sourcemap sai làm production debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Project mới có thể dùng Vite/framework preset thay vì tự config Webpack.
- Không nên tùy biến loader/plugin sâu nếu preset đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì Webpack bundle JavaScript module.
- [[Module System]] vì Webpack resolve import/module graph.
- [[Babel]] vì Babel thường được dùng như transform trong Webpack pipeline.
- [[Vite]] vì Vite là lựa chọn build/dev server hiện đại trong nhiều project.
- [[Build Cache]] vì cache ảnh hưởng tốc độ build Webpack.

## Liên quan rộng

- Module bundling
- Asset pipeline
- Code splitting

## Keywords / Từ khóa tìm kiếm

- Webpack
- module bundler
- webpack config
- loader
- plugin
- code splitting
- bundle analysis
- Webpack debugging

## Source trace

- Webpack documentation
