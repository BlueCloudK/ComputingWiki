# Requirements Baseline

Aliases: Requirements Baseline

Type: Requirements

## Context / Ngữ cảnh

Requirements Baseline là khái niệm xuất hiện trong source map của ComputingWiki và cần có node thật để graph không sinh unresolved link.

## Boundary / Ranh giới

### Nó là gì

Requirements Baseline dùng để đặt tên một vùng kiến thức, artifact, activity hoặc decision trong nhóm Requirements.

### Nó không phải là gì

Nó không phải tutorial dài hoặc tool cụ thể; node này giữ nghĩa canonical để nối map nguồn với wiki chính.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Requirements Baseline đang mô tả boundary nào, tạo artifact gì, và giúp kiểm tra hoặc thiết kế phần nào của hệ thống.

## Project Role / Vai trò trong dự án

Requirements Baseline giúp người đọc tra lại thuật ngữ từ source map, rồi nối sang các node chi tiết hơn trong project workflow.

## Output / Artifact nên có

- Note ngắn định nghĩa Requirements Baseline
- Trace về source map nơi thuật ngữ xuất hiện
- Link tới node liên quan mạnh nếu đã có trong wiki

## Decision Checklist / Câu hỏi kiểm tra

- Requirements Baseline thuộc vùng kiến thức nào trong ComputingWiki?
- Nó là activity, artifact, concept hay quality concern?
- Khi gặp thuật ngữ này trong source, nên nối sang node nào để học/làm tiếp?

## Failure Modes / Cách nó gây lỗi

- Để Requirements Baseline chỉ là ghost link làm graph view có node không tồn tại
- Tạo trùng với canonical node khác mà không xử lý alias
- Dùng thuật ngữ rộng nhưng không có source trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu node chỉ dùng để giữ trace từ Maps
- Dễ over-engineer nếu biến node này thành tutorial thay vì entry ngắn trong wiki

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Source extraction
- Knowledge graph cleanup

## Keywords / Từ khóa tìm kiếm

- Requirements Baseline
- requirements baseline
- Requirements Baseline concept

## Source trace

- Maps\Requirements Engineering Map.md