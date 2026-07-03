# Paging

Aliases: memory paging, phân trang

Type: Operating System

## Context / Ngữ cảnh

Paging xuất hiện khi OS chia virtual memory thành page để map sang physical memory/storage.

## Boundary / Ranh giới

### Nó là gì

Paging là cơ chế memory management dùng page table để map virtual page sang frame.

### Nó không phải là gì

Nó không phải pagination API hoặc UI paging.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là page table mapping và page fault khi dữ liệu chưa sẵn.

## Project Role / Vai trò trong dự án

Node này giúp hiểu virtual memory, memory pressure và page replacement.

## Output / Artifact nên có

- Page size/table/page-fault note
- Virtual memory behavior liên quan
- Metric page fault/swap nếu performance chậm

## Decision Checklist / Câu hỏi kiểm tra

- Vấn đề này là memory paging hay API pagination?
- Page fault rate có bất thường không?
- Working set có vượt memory vật lý không?

## Failure Modes / Cách nó gây lỗi

- Nhầm paging OS với pagination dữ liệu
- Swap/page fault cao làm latency xấu
- Tối ưu app mà bỏ qua memory pressure

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không có memory/perf symptom
- Dễ over-engineer nếu phân tích paging khi bottleneck là DB/network

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Virtual Memory]] vì paging là cơ chế chính của virtual memory
- [[Page Replacement]] vì page replacement chọn page bị evict

## Liên quan rộng

- Memory management

## Source trace

- Operating Systems Map
