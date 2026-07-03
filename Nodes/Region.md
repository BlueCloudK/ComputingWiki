# Region

Aliases: cloud region, vùng cloud

Type: Deployment / Operations

## Context / Ngữ cảnh

Region xuất hiện khi chọn vị trí địa lý chạy workload cloud.

## Boundary / Ranh giới

### Nó là gì

Region là khu vực địa lý cloud provider đặt datacenter/service.

### Nó không phải là gì

Nó không phải availability zone và không tự đảm bảo latency tốt cho mọi user.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đặt resource trong địa lý cụ thể với latency, compliance, cost và service availability riêng.

## Project Role / Vai trò trong dự án

Node này ảnh hưởng latency, disaster recovery, data residency và cost.

## Output / Artifact nên có

- Region selection record
- Data residency/compliance note
- Latency/cost assumption

## Decision Checklist / Câu hỏi kiểm tra

- User và data chính ở đâu?
- Service cần dùng có available trong region này không?
- Cross-region traffic/cost có chấp nhận không?

## Failure Modes / Cách nó gây lỗi

- Chọn region xa user làm latency cao
- Data residency vi phạm yêu cầu
- Dependency không có ở region đã chọn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần multi-region khi app nhỏ một thị trường
- Dễ over-engineer nếu thêm region trước khi có DR/latency requirement

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cloud Computing]] vì region là primitive cloud cơ bản
- [[Availability Zone]] vì AZ nằm trong region

## Liên quan rộng

- Data residency
- Geographic latency

## Keywords / Từ khóa tìm kiếm

- Region
- cloud region
- geographic region
- data residency
- regional latency
- multi region
- vùng cloud
- khu vực triển khai

## Source trace

- AWS Well-Architected
- Google Cloud Architecture Framework
