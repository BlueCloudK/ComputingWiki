# Threat Modeling

Aliases: threat model, mô hình đe dọa

Type: Security

## Context / Ngữ cảnh

Threat Modeling xuất hiện khi cần hiểu attacker có thể lạm dụng hệ thống như thế nào trước khi chọn control.

## Boundary / Ranh giới

### Nó là gì

Threat Modeling là hoạt động xác định asset, actor, entry point, threat và mitigation.

### Nó không phải là gì

Nó không phải checklist security chung chung và không thay thế test/pentest.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là model hệ thống, hỏi cái gì có thể sai, ưu tiên threat theo impact/likelihood và ghi mitigation.

## Project Role / Vai trò trong dự án

Node này giúp security control đặt đúng chỗ thay vì thêm ngẫu nhiên.

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

- Chưa tách nhánh

## Nối mạnh

- [[Security]] vì threat modeling định hướng control security
- [[API Security]] vì API boundary thường là attack surface lớn

## Liên quan rộng

- STRIDE
- Abuse cases

## Source trace

- OWASP Threat Modeling
- NIST SSDF
