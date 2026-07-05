# Prompt Registry

Aliases: Prompt Registry, prompt version registry

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Prompt Registry xuất hiện khi nhiều prompt/template được dùng trong production AI app và cần version, owner, diff, approval, rollback và eval trace rõ.

## Boundary / Ranh giới

### Nó là gì

Prompt Registry là nơi quản lý prompt như artifact có version: system prompt, prompt template, tool instruction, output schema và metadata liên quan.

### Nó không phải là gì

Prompt Registry không phải chỉ là folder text. Nếu không có version/eval/owner, nó không giúp kiểm soát prompt regression.

## Core Mechanism / Cơ chế lõi

Prompt được lưu với id, version, purpose, variables, owner, changelog và eval result. Runtime hoặc config chọn version cụ thể; pipeline có thể rollback hoặc promote prompt version.

## Project Role / Vai trò trong dự án

Dùng node này khi app có nhiều agent/prompt, cần kiểm soát thay đổi prompt, audit behavior hoặc rollback nhanh khi prompt mới gây lỗi.

## Output / Artifact nên có

- Prompt id/version
- Template variables
- Owner/purpose
- Eval result per version
- Changelog và rollback note

## Decision Checklist / Câu hỏi kiểm tra

- Prompt này dùng ở flow nào?
- Version nào đang chạy production?
- Biến template có schema rõ không?
- Prompt đổi có chạy eval chưa?
- Có rollback về version cũ không?

## Failure Modes / Cách nó gây lỗi

- Prompt bị sửa trực tiếp không có version.
- Runtime dùng nhầm prompt staging/production.
- Prompt variables thiếu làm output lỗi.
- Không có eval trace nên không biết version nào tốt hơn.
- Registry có nhưng không được runtime dùng thật.

## Khi nào chưa cần hoặc dễ over-engineer

- App thử nghiệm một prompt có thể dùng version file đơn giản.
- Không nên build registry phức tạp nếu chưa có prompt regression thực tế.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Regression]] vì registry giúp phát hiện và rollback regression.
- [[Offline Evaluation]] vì mỗi prompt version nên gắn eval result.
- [[Output Validation]] vì prompt thường quy định schema output.
- [[AI Agent]] vì agent thường có prompt/profile riêng.

## Liên quan rộng

- Prompt versioning
- AI config management
- Agent profile

## Keywords / Từ khóa tìm kiếm

- Prompt Registry
- prompt version registry
- prompt versioning
- prompt template
- prompt changelog
- prompt rollback
- prompt registry debugging

## Source trace

- OpenAI documentation
- Anthropic prompt engineering docs
