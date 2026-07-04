# Split Brain

Aliases: split-brain, não tách đôi

Type: Failure Pattern / Distributed Systems

## Context / Ngữ cảnh

Split Brain xuất hiện khi hệ thống phân tán bị network partition, coordination lỗi hoặc heartbeat timeout sai làm nhiều node/partition cùng tin mình là leader/primary. Nó thường gặp ở database cluster, distributed lock, failover system, message broker, storage cluster hoặc control plane có leader election.

## Boundary / Ranh giới

### Nó là gì

Split Brain là failure pattern trong đó quyền lãnh đạo hoặc quyền ghi bị chia đôi. Hai hoặc nhiều node cùng nhận quyền xử lý write/decision dù hệ thống chỉ nên có một leader/primary. Hậu quả thường là dữ liệu diverge, double processing, conflict khó merge hoặc mất consistency.

### Nó không phải là gì

Split Brain không phải mọi network partition. Partition chỉ trở thành split brain khi nhiều phía vẫn tiếp tục hành động như primary/leader. Nếu hệ thống dùng quorum/fencing đúng và một phía tự dừng write, đó là partition được xử lý an toàn hơn.

## Core Mechanism / Cơ chế lõi

Khi node mất liên lạc, mỗi phía có thể suy luận phía kia chết. Nếu leader election không dựa trên quorum, lease/fencing token không an toàn, clock/timeout sai hoặc failover manual nhầm, hai phía có thể cùng phục vụ write. Quorum, consensus, fencing token và STONITH giúp ngăn old leader tiếp tục ghi sau khi leader mới được bầu.

## Project Role / Vai trò trong dự án

Split Brain là node cần mở khi thiết kế cluster/failover, database primary-replica, distributed lock hoặc job scheduler chỉ được có một worker active. Nó giúp team hỏi: ai được quyền write, quyền đó được chứng minh bằng quorum/fencing nào, và khi partition xảy ra thì bên nào dừng.

## Output / Artifact nên có

- Leader/failover design note: quorum, election, heartbeat, timeout, lease/fencing
- Write authority map: node nào được write vào resource nào trong trạng thái bình thường/failure
- Partition test hoặc chaos scenario cho network split và old leader recovery
- Recovery runbook: detect divergence, stop old primary, reconcile data, restore quorum
- Monitoring: leader count, quorum status, fencing failure, replication lag, conflicting writes

## Decision Checklist / Câu hỏi kiểm tra

- Hệ thống có bao giờ cho phép hơn một leader/primary không?
- Leader election có cần quorum majority không?
- Old leader bị chặn write bằng fencing token/lease/STONITH hay chỉ tin vào heartbeat?
- Timeout heartbeat có quá ngắn khiến false failover không?
- Khi network partition, phía minority có tự dừng write không?
- Nếu dữ liệu diverge, có recovery/reconciliation path không?
- Manual failover có checklist tránh khởi động hai primary cùng lúc không?

## Failure Modes / Cách nó gây lỗi

- Hai primary cùng nhận write làm dữ liệu diverge và không merge tự động được.
- Distributed lock hết lease nhưng old worker vẫn tiếp tục xử lý job.
- Failover manual kích hoạt node mới trong khi node cũ vẫn sống và ghi dữ liệu.
- Heartbeat timeout quá nhạy làm false leader election dưới network jitter.
- Quorum config sai làm minority partition vẫn phục vụ write.
- Recovery thiếu fencing làm old leader quay lại và ghi đè dữ liệu mới.

## Khi nào chưa cần hoặc dễ over-engineer

- Single-node dev hoặc workload stateless không có leader/write authority thì chưa cần xử lý split brain sâu.
- Không nên tự build consensus/leader election nếu có thể dùng database/coordination system đã được kiểm chứng.
- Không nên dùng clock/timeout đơn giản làm bằng chứng quyền write cho dữ liệu quan trọng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed System]] vì split brain là failure pattern của hệ thống phân tán.
- [[Consensus]] vì quorum/consensus giúp tránh nhiều leader cùng lúc.
- [[Leader Election]] vì leader election sai là nguồn split brain phổ biến.
- [[Replication]] vì split brain thường làm dữ liệu replica/primary diverge.

## Liên quan rộng

- High availability
- Failover design
- Cluster operations
- Data consistency

## Keywords / Từ khóa tìm kiếm

- Split Brain
- split-brain
- não tách đôi
- network partition
- multiple leaders
- dual primary
- quorum
- fencing token
- leader election
- failover
- STONITH
- distributed lock
- primary replica
- data divergence
- split brain debugging

## Source trace

- Designing Data-Intensive Applications Ch09
- ZooKeeper documentation
