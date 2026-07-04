# Backup

Aliases: data backup, sao lưu

Type: Deployment / Operations

## Context / Ngữ cảnh

Backup xuất hiện khi dữ liệu, config hoặc artifact quan trọng cần được sao lưu để phục hồi sau xóa nhầm, corruption, ransomware, migration lỗi, storage failure hoặc incident vận hành. Nó đặc biệt quan trọng với database, file upload, object storage, secrets/config và persistent volumes.

## Boundary / Ranh giới

### Nó là gì

Backup là bản sao có chủ đích của dữ liệu/trạng thái quan trọng được lưu ở nơi đủ an toàn để restore khi hệ thống chính lỗi. Backup tốt cần định nghĩa dữ liệu nào được sao lưu, tần suất, retention, encryption, access control, storage location và restore procedure.

### Nó không phải là gì

Backup không phải replication. Replication giúp availability nhưng lỗi/xóa nhầm/corruption có thể replicate sang bản sao rất nhanh. Backup cũng không có giá trị nếu chưa từng test restore. “Có file backup” nhưng không restore được thì không phải khả năng phục hồi thật.

## Core Mechanism / Cơ chế lõi

Hệ thống tạo snapshot/dump/copy theo lịch hoặc event, lưu ở storage tách biệt, giữ nhiều phiên bản theo retention policy, mã hóa nếu có dữ liệu nhạy cảm và định kỳ test restore. Hai chỉ số quan trọng là RPO: mất tối đa bao nhiêu dữ liệu, và RTO: phục hồi mất bao lâu.

## Project Role / Vai trò trong dự án

Backup là node cần mở trước khi chạy migration, xóa dữ liệu, vận hành database production hoặc lưu file người dùng. Nó giúp team biết nếu thao tác sai thì phục hồi bằng gì, mất bao lâu, mất bao nhiêu dữ liệu và ai có quyền restore.

## Output / Artifact nên có

- Backup policy: scope, frequency, retention, encryption, storage location
- Restore runbook: bước restore, owner, expected RTO/RPO, validation checklist
- Backup monitoring: job success/fail, backup age, size, checksum, restore test result
- Access control: ai có quyền đọc/restore/xóa backup
- Pre-migration backup checklist nếu thay đổi dữ liệu rủi ro cao

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu nào nếu mất sẽ không thể tái tạo?
- RPO/RTO mong muốn là bao nhiêu?
- Backup nằm cùng hệ thống lỗi hay tách biệt đủ an toàn?
- Backup có được encrypt và kiểm soát quyền truy cập không?
- Restore đã được test gần đây chưa?
- Backup có giữ nhiều version để chống corruption/xóa nhầm không?
- Khi restore xong, validation dữ liệu/service là gì?

## Failure Modes / Cách nó gây lỗi

- Có backup job nhưng fail âm thầm nhiều ngày.
- Backup cùng account/storage với production nên bị xóa hoặc mã hóa cùng lúc.
- Chỉ có replication nên xóa nhầm/corruption lan sang replica.
- Restore quá chậm so với RTO cần thiết.
- Backup không encrypt hoặc quyền quá rộng làm lộ dữ liệu nhạy cảm.
- Không test restore nên tới lúc cần mới phát hiện backup hỏng/thiếu dữ liệu.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu cache/tạm có thể rebuild được thì không cần backup như source of truth.
- Project demo không dữ liệu quan trọng có thể dùng export thủ công nhẹ.
- Không nên backup mọi thứ giống nhau; ưu tiên dữ liệu không thể tái tạo và config quan trọng.

## Gồm những gì

- [[Rollback]]

## Nối mạnh

- [[Persistent Volume]] vì dữ liệu trên PV cần backup/restore strategy riêng.
- [[Database Migration]] vì migration rủi ro cần backup hoặc rollback/forward plan.
- [[Rollback]] vì backup có thể là nền cho rollback dữ liệu khi state bị phá.
- [[Incident]] vì backup/restore thường được dùng trong incident mất dữ liệu.
- [[Deployment]] vì deploy/migration an toàn cần backup trước thay đổi rủi ro.

## Liên quan rộng

- Disaster recovery
- Data retention
- Restore testing
- Storage operations

## Keywords / Từ khóa tìm kiếm

- Backup
- data backup
- sao lưu
- restore
- backup restore
- RPO
- RTO
- backup retention
- snapshot
- database dump
- restore test
- disaster recovery
- backup encryption
- backup monitoring
- backup debugging

## Source trace

- Google SRE Book
- Database operations references
