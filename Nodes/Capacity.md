# Capacity

Aliases: system capacity, năng lực hệ thống

Type: Performance / Scalability

## Context / Ngữ cảnh

Capacity xuất hiện khi cần biết giới hạn phục vụ của hệ thống trước khi degradation hoặc failure xảy ra.

## Boundary / Ranh giới

### Nó là gì

Capacity là lượng workload hệ thống xử lý được trong điều kiện và SLO cụ thể.

### Nó không phải là gì

Nó không phải throughput đơn lẻ nếu không kèm latency/error target.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là giới hạn bởi bottleneck, resource headroom, dependency limit và scaling policy.

## Project Role / Vai trò trong dự án

Node này giúp trả lời hệ thống chịu được bao nhiêu user/request/event trước khi cần scale.

## Output / Artifact nên có

- Capacity baseline under load
- Peak workload và headroom target
- Dependency/quota limit note

## Decision Checklist / Câu hỏi kiểm tra

- Capacity được đo với latency/error target nào?
- Bottleneck hiện tại là gì?
- Peak load có khác average bao nhiêu?

## Failure Modes / Cách nó gây lỗi

- Nói capacity theo RPS nhưng bỏ latency/error
- Không tính third-party quota
- Scale app nhưng DB đã là limit

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần model sâu khi chưa có traffic thật
- Dễ over-engineer nếu forecast xa hơn dữ liệu sử dụng hiện có

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Capacity Planning]] vì planning dựa trên capacity hiện tại/tương lai
- [[Throughput]] vì throughput là một mặt của capacity

## Liên quan rộng

- Headroom
- Load limits

## Keywords / Từ khóa tìm kiếm

- Capacity
- system capacity
- resource capacity
- traffic capacity
- capacity limit
- capacity planning
- headroom
- sức chứa hệ thống
- dung lượng xử lý

## Source trace

- Google SRE Books
- DDIA Ch01
