# GitHub Actions

Aliases: GitHub Actions, github actions

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

GitHub Actions xuất hiện khi repo GitHub cần tự động hóa CI, test, build, release, deployment, scheduled job hoặc repository maintenance. Nó thường nằm trên critical path của PR check, artifact build, Docker image publish, documentation deploy và production release.

## Boundary / Ranh giới

### Nó là gì

GitHub Actions là workflow automation platform tích hợp trong GitHub. Workflow được định nghĩa bằng YAML trong `.github/workflows`, trigger theo event như push, pull_request, schedule hoặc workflow_dispatch, rồi chạy job/step trên runner hosted hoặc self-hosted.

### Nó không phải là gì

GitHub Actions không tự đảm bảo CI/CD tốt. Workflow YAML có thể chạy sai trigger, dùng secret quá rộng, cache sai hoặc deploy production thiếu gate. Nó cũng không phải runtime production; nó là automation runner cho repo/process.

## Core Mechanism / Cơ chế lõi

Event trigger workflow. Workflow gồm job, mỗi job chạy trên runner, có steps dùng shell command hoặc action tái sử dụng. Job có thể dùng matrix, cache, artifact, environment, permission, secret và concurrency control. Status check trả về PR/commit để cho phép hoặc chặn merge.

## Project Role / Vai trò trong dự án

GitHub Actions là node cần mở khi thiết kế PR check, chạy test, publish package/image, deploy, hoặc debug pipeline đỏ. Nó giúp team trace từ event → workflow → job → step → runner → secret/cache/artifact → status check.

## Output / Artifact nên có

- Workflow YAML theo mục tiêu: CI, release, deploy, audit
- Required checks và branch protection nếu dùng
- Secret/permission policy: `permissions`, environment secret, OIDC nếu có
- Cache/artifact policy: key, retention, restore behavior
- Debug runbook: failed step, runner, log, artifact, re-run, concurrency cancellation

## Decision Checklist / Câu hỏi kiểm tra

- Workflow trigger đúng event chưa?
- Job cần quyền gì trong `permissions` và có đang quá rộng không?
- Secret nào được expose, ở branch/PR nào?
- Cache key có làm dùng dependency/build cũ sai không?
- Matrix có test đủ runtime/OS/version cần hỗ trợ không?
- Deploy job có environment approval/concurrency không?
- Log/artifact có đủ debug nhưng không lộ secret không?

## Failure Modes / Cách nó gây lỗi

- Pull request từ fork không có secret làm workflow fail hoặc bị skip nhầm.
- `permissions: write-all` hoặc token quá rộng tạo risk supply-chain.
- Cache key quá rộng dùng dependency cũ và build sai.
- Trigger sai làm push/PR quan trọng không chạy check.
- Deploy job chạy song song nhiều lần vì thiếu concurrency lock.
- Log in env/secret làm credential lộ trong Actions log.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo nhỏ một người có thể bắt đầu bằng một workflow CI đơn giản.
- Không nên ghép CI, release và deploy production vào một workflow khó đọc nếu boundary khác nhau.
- Không nên dùng third-party action không pin version/sha cho path nhạy cảm.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì GitHub Actions thường chạy CI checks trong GitHub repo.
- [[CD]] vì GitHub Actions có thể điều phối release/deploy pipeline.
- [[Matrix Build]] vì matrix strategy là feature phổ biến của Actions.
- [[Build Cache]] vì Actions cache ảnh hưởng tốc độ và correctness pipeline.
- [[Secret]] vì Actions secret/token là boundary bảo mật quan trọng.

## Liên quan rộng

- Workflow automation
- Pull request checks
- Release pipeline
- DevOps tooling

## Keywords / Từ khóa tìm kiếm

- GitHub Actions
- github actions
- workflow yaml
- actions runner
- workflow trigger
- pull_request workflow
- workflow_dispatch
- actions cache
- actions artifact
- GitHub Actions secrets
- permissions token
- OIDC deploy
- GitHub Actions debugging

## Source trace

- GitHub Actions documentation
- GitHub Actions security hardening documentation
