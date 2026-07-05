# Metadata Extraction

Aliases: Metadata Extraction, metadata extraction

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Metadata Extraction xuất hiện khi ingestion pipeline cần lấy thông tin phụ từ tài liệu như title, author, page, section, timestamp, source URL, permission hoặc document type.

## Boundary / Ranh giới

### Nó là gì

Metadata Extraction là bước trích xuất metadata có cấu trúc để hỗ trợ filtering, citation, access control, retrieval ranking và audit trong RAG/search system.

### Nó không phải là gì

Metadata Extraction không phải chỉ lấy text chính. Metadata sai có thể làm filter/citation/permission sai dù extracted text đúng.

## Core Mechanism / Cơ chế lõi

Parser hoặc model đọc source document, lấy field metadata từ file header, layout, path, markup, database record hoặc inference, rồi normalize theo schema trước khi indexing.

## Project Role / Vai trò trong dự án

Dùng node này khi debug RAG filter không ra tài liệu, citation sai page, permission leak, document routing sai hoặc eval cần phân tích theo source/type/time.

## Output / Artifact nên có

- Metadata schema
- Extraction rule/source field mapping
- Sample extracted records
- Validation rule
- Missing/uncertain metadata handling

## Decision Checklist / Câu hỏi kiểm tra

- Metadata nào bắt buộc cho retrieval/citation/permission?
- Field lấy từ source thật hay suy luận?
- Missing metadata xử lý ra sao?
- Metadata có được normalize cùng format không?
- Filter/ranking có phụ thuộc field này không?

## Failure Modes / Cách nó gây lỗi

- Page/section sai làm citation sai.
- Permission metadata thiếu làm lộ tài liệu không nên retrieve.
- Source/type normalize không nhất quán làm filter fail.
- Timestamp sai làm ranking theo recency lệch.
- Model suy luận metadata nhưng không đánh dấu uncertainty.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus nhỏ, không filter/citation có thể metadata tối thiểu.
- Không nên thêm nhiều metadata nếu không có use case retrieval/debug rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Document Ingestion]] vì metadata extraction nằm trong ingestion pipeline.
- [[Text Extraction]] vì text và metadata thường được extract cùng lúc.
- [[Chunking Strategy]] vì metadata cần propagate xuống chunk.
- [[Authorization]] vì permission metadata có thể ảnh hưởng retrieval boundary.

## Liên quan rộng

- Document metadata
- Source attribution
- Permission filter
- Citation

## Keywords / Từ khóa tìm kiếm

- Metadata Extraction
- metadata extraction
- document metadata
- source metadata
- page metadata
- permission metadata
- metadata extraction debugging

## Source trace

- OpenAI documentation
- Designing Data-Intensive Applications
