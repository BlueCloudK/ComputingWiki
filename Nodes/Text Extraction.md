# Text Extraction

Aliases: Text Extraction, text extraction

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Text Extraction xuất hiện khi hệ thống RAG/search cần lấy text sạch từ PDF, HTML, DOCX, ảnh OCR, log hoặc file bán cấu trúc trước khi chunk/index.

## Boundary / Ranh giới

### Nó là gì

Text Extraction là bước chuyển source document thành text và metadata có thể xử lý tiếp trong ingestion, retrieval hoặc evaluation.

### Nó không phải là gì

Text Extraction không chỉ là đọc raw bytes. Nếu mất heading, table, page number, code block hoặc metadata, RAG phía sau có thể retrieve sai dù model tốt.

## Core Mechanism / Cơ chế lõi

Pipeline nhận file/source, chọn parser/OCR phù hợp, trích text, normalize layout, giữ metadata như title/page/section, rồi xuất record cho chunking và indexing.

## Project Role / Vai trò trong dự án

Dùng node này khi debug tài liệu ingest bị thiếu chữ, bảng lỗi, citation sai page, OCR nhiễu hoặc chunking không giữ được cấu trúc gốc.

## Output / Artifact nên có

- Extracted text sample
- Metadata schema
- Parser/OCR choice
- Quality check cases
- Failed extraction log

## Decision Checklist / Câu hỏi kiểm tra

- Source format là gì?
- Parser có giữ heading/table/page number không?
- OCR có cần không và độ nhiễu ra sao?
- Metadata nào cần cho citation/filter?
- Extraction có deterministic giữa các lần chạy không?

## Failure Modes / Cách nó gây lỗi

- Mất bảng hoặc cột làm answer sai.
- Page/section metadata sai làm citation sai.
- OCR nhiễu làm embedding/search lệch.
- Parser bỏ qua text trong image hoặc footnote.
- Normalize quá mạnh làm mất cấu trúc quan trọng.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus plain text nhỏ có thể dùng parser đơn giản trước.
- Không nên thêm OCR/layout pipeline nặng nếu tài liệu không cần.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Document Ingestion]] vì extraction là bước đầu trong ingestion.
- [[Chunking Strategy]] vì text extracted quyết định chunk có giữ context không.
- [[RAG Evaluation]] vì extraction change cần đo lại retrieval/answer.
- [[Data Quality]] vì text extraction lỗi làm dữ liệu index bẩn.

## Liên quan rộng

- Document parsing
- OCR
- Metadata extraction
- Layout preservation

## Keywords / Từ khóa tìm kiếm

- Text Extraction
- document text extraction
- PDF parsing
- OCR text
- layout extraction
- table extraction
- text extraction debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
