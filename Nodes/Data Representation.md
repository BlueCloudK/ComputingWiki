# Data Representation

Aliases: data encoding, biểu diễn dữ liệu

Type: Computer Foundation

## Context / Ngữ cảnh

Data Representation xuất hiện khi dữ liệu trong code, memory, file hoặc network phải được mã hóa thành bit/byte.

## Boundary / Ranh giới

### Nó là gì

Data Representation là cách map dữ liệu như số, text, boolean, object hoặc record sang dạng máy lưu/truyền được.

### Nó không phải là gì

Nó không phải database model, UI format, hay guarantee dữ liệu đúng về mặt domain.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là encoding/decoding: layout, type, size, endian, charset hoặc schema biến value thành bytes và ngược lại.

## Project Role / Vai trò trong dự án

Node này giúp debug serialization, file format, protocol payload và mismatch giữa systems.

## Output / Artifact nên có

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- [[Data Type]]
- [[Binary Representation]]

## Nối mạnh

- [[JSON]] vì JSON là một dạng biểu diễn dữ liệu trao đổi
- [[Protocol Buffers]] vì protobuf là biểu diễn schema-based

## Liên quan rộng

- Serialization
- Encoding

## Source trace

- Computer Foundations Map Ch03
