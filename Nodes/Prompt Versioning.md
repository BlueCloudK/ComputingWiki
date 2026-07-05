# Prompt Versioning

Aliases: Prompt Versioning, prompt versions

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Prompt Versioning xuất hiện khi prompt trong AI app thay đổi theo thời gian và cần trace được version nào tạo ra behavior nào.

## Boundary / Ranh giới

### Nó là gì

Prompt Versioning là việc lưu, đặt tên, so sánh, promote và rollback prompt/system instruction/template như một artifact có version.

### Nó không phải là gì

Prompt Versioning không phải chỉ copy prompt vào một file. Nếu không có diff, owner, eval result và runtime mapping, rất khó biết version nào đang chạy thật.

## Core Mechanism / Cơ chế lõi

Mỗi prompt có id, version, changelog, variable schema và eval result. Runtime chọn version cụ thể qua config/registry; pipeline so sánh prompt diff và chạy regression trước khi deploy.

## Project Role / Vai trò trong dự án

Dùng node này khi nhiều prompt được dùng trong RAG/agent workflow, cần rollback prompt gây lỗi, hoặc cần audit vì sao output thay đổi sau release.

## Output / Artifact nên có

- Prompt id/version
- Prompt diff/changelog
- Variable schema
- Eval result per version
- Runtime mapping: flow nào dùng version nào

## Decision Checklist / Câu hỏi kiểm tra

- Prompt version nào đang chạy production?
- Prompt đổi vì lý do gì?
- Có eval trước/sau không?
- Variable schema có đổi không?
- Rollback về version cũ có nhanh không?

## Failure Modes / Cách nó gây lỗi

- Prompt bị sửa trực tiếp không có lịch sử.
- Runtime dùng nhầm prompt staging.
- Prompt diff nhỏ nhưng phá output schema.
- Không gắn eval result nên không biết version nào tốt hơn.
- Rollback khó vì prompt nằm rải rác trong code/config.

## Khi nào chưa cần hoặc dễ over-engineer

- Demo một prompt có thể version bằng file và commit trước.
- Không nên xây registry phức tạp nếu chưa có nhiều prompt hoặc regression thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Registry]] vì registry là nơi quản lý prompt version formal hơn.
- [[Prompt Regression]] vì version mới cần kiểm tra regression.
- [[Offline Evaluation]] vì eval giúp so sánh version prompt.
- [[Output Validation]] vì prompt version có thể phá schema output.

## Liên quan rộng

- Prompt artifact
- AI config management
- Rollback

## Keywords / Từ khóa tìm kiếm

- Prompt Versioning
- prompt version
- prompt diff
- prompt rollback
- prompt changelog
- prompt eval
- prompt versioning debugging

## Source trace

- OpenAI documentation
- Anthropic prompt engineering docs
