# Vite

Aliases: Vite

Type: Frameworks and Tools

## Context / Ngữ cảnh

Vite xuất hiện khi frontend project cần dev server nhanh, hot reload và build production cho JavaScript/TypeScript app hiện đại.

## Boundary / Ranh giới

### Nó là gì

Vite là frontend build tool và dev server. Nó cung cấp workflow phát triển nhanh, plugin ecosystem và production build cho web app.

### Nó không phải là gì

Vite không phải frontend framework. Nó không tự quyết định component model, routing, state management hoặc backend architecture.

## Core Mechanism / Cơ chế lõi

Trong dev, Vite phục vụ module nhanh qua native ESM và transform khi cần. Trong build, Vite dùng bundler/config/plugin để tạo static assets hoặc bundle production.

## Project Role / Vai trò trong dự án

Dùng node này khi debug dev server, HMR, env variable, asset path, alias, bundle output hoặc frontend build trong CI.

## Output / Artifact nên có

- `vite.config`
- Package scripts
- Env/base path note
- Plugin list
- Build output check

## Decision Checklist / Câu hỏi kiểm tra

- App dùng framework plugin nào?
- Base path production có đúng không?
- Env nào được expose ra client?
- Alias có khớp test và IDE không?
- Build có chạy trong CI không?

## Failure Modes / Cách nó gây lỗi

- Base path sai làm asset không tải được sau deploy.
- Env client/server bị nhầm boundary.
- Dev chạy nhưng production build fail.
- Plugin hoặc alias config lệch giữa test và build.
- Bundle lớn nhưng không được đo.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang nhỏ có thể dùng static HTML/CSS/JS.
- Không nên tùy biến plugin quá nhiều nếu preset đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì Vite build JavaScript frontend.
- [[Frontend Framework]] vì Vite thường dùng cùng React/Vue/Svelte.
- [[npm]] vì Vite thường chạy qua package scripts.
- [[esbuild]] vì Vite dùng esbuild cho nhiều transform.
- [[CI]] vì production build cần chạy trong pipeline.

## Liên quan rộng

- Frontend build
- Dev server
- Hot module reload
- Asset pipeline

## Keywords / Từ khóa tìm kiếm

- Vite
- Vite dev server
- Vite build
- vite config
- HMR
- frontend build
- Vite debugging

## Source trace

- Vite documentation
