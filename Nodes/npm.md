# npm

Aliases: npm, Node Package Manager

Type: Frameworks and Tools

## Context / Ngữ cảnh

npm xuất hiện khi JavaScript/Node.js project cần quản lý package dependency, script, version, registry và publish package. Nó ảnh hưởng trực tiếp tới install reproducibility, CI speed, supply-chain risk và local development workflow.

## Boundary / Ranh giới

### Nó là gì

npm là package manager và registry ecosystem cho JavaScript. Trong project, npm thường được dùng qua `package.json`, `package-lock.json`, `npm install`, `npm ci`, npm scripts và dependency version ranges.

### Nó không phải là gì

npm không phải JavaScript runtime. Node.js mới là runtime chạy code server-side; npm quản lý package và script. npm cũng không tự đảm bảo dependency an toàn hoặc build reproducible nếu lockfile, script và registry policy không rõ.

## Core Mechanism / Cơ chế lõi

`package.json` khai báo dependencies/devDependencies/scripts. Lockfile ghi dependency tree cụ thể. `npm install` có thể cập nhật lockfile theo ranges; `npm ci` dùng lockfile sạch cho CI. npm tải package từ registry, chạy lifecycle scripts nếu được phép và đặt dependency vào `node_modules` hoặc cache.

## Project Role / Vai trò trong dự án

npm là node cần mở khi debug install fail, dependency version lệch, CI khác local, package script lỗi, supply-chain audit hoặc build frontend/backend Node.js. Nó giúp team kiểm tra lockfile, Node/npm version, registry, script và dependency risk.

## Output / Artifact nên có

- `package.json` scripts/dependencies rõ vai trò
- Lockfile committed và dùng `npm ci` trong CI
- Node/npm version policy qua `.nvmrc`, `.node-version` hoặc engine field
- Dependency audit/update policy
- Debug note cho install cache, peer dependency, registry và lifecycle script

## Decision Checklist / Câu hỏi kiểm tra

- Project dùng npm, pnpm hay yarn, và lockfile nào là source of truth?
- CI dùng `npm ci` hay `npm install`?
- Node/npm version có pin hoặc document chưa?
- Dependency range có quá rộng gây version drift không?
- Lifecycle script có chạy code không tin cậy không?
- Registry/private package auth có an toàn không?
- Có policy update/audit dependency không?

## Failure Modes / Cách nó gây lỗi

- Local dùng dependency khác CI vì lockfile không được commit hoặc bị update ngẫu nhiên.
- `npm install` trong CI làm lockfile drift hoặc build không reproducible.
- Peer dependency conflict làm install fail sau package upgrade.
- Lifecycle script của dependency chạy code không mong muốn.
- Private registry/token sai làm CI install fail.
- Dependency typo-squatting hoặc compromised package gây supply-chain risk.

## Khi nào chưa cần hoặc dễ over-engineer

- Script JS rất nhỏ không dependency có thể chưa cần npm project đầy đủ.
- Không nên thêm package cho logic đơn giản nếu native API đủ dùng.
- Không nên đổi package manager chỉ vì trend nếu team/tooling hiện tại ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì npm là package ecosystem chính của JavaScript.
- [[Node.js]] vì Node.js project thường dùng npm để quản lý dependency/script.
- [[CI]] vì CI cần install dependency reproducibly bằng lockfile.
- [[GitHub Actions]] vì Actions thường chạy npm scripts trong workflow.
- [[Secret]] vì registry token/private package auth là secret cần bảo vệ.

## Liên quan rộng

- Package management
- Supply-chain security
- Frontend tooling
- Node.js development

## Keywords / Từ khóa tìm kiếm

- npm
- Node Package Manager
- package.json
- package-lock.json
- npm install
- npm ci
- npm scripts
- dependency version
- peer dependency
- npm registry
- npm audit
- lifecycle script
- npm debugging

## Source trace

- npm documentation
- Node.js documentation
