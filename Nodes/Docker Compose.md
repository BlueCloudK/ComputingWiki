# Docker Compose

Aliases: compose file, docker-compose, Docker Compose

Type: DevOps / Tooling

## Context / Ngữ cảnh

Docker Compose xuất hiện khi một project cần khai báo và chạy nhiều container cùng nhau bằng một file cấu hình, thường cho local development, integration test, demo, staging nhỏ hoặc homelab. Nó giúp app, database, cache, queue, reverse proxy và worker chạy thành một stack nhất quán.

## Boundary / Ranh giới

### Nó là gì

Docker Compose là công cụ đọc `compose.yaml` để tạo services, networks, volumes, environment variables, port mappings và dependency rules cho nhiều container. Mỗi service thường dựa trên image/build context và có cấu hình runtime riêng.

### Nó không phải là gì

Docker Compose không phải Kubernetes và không phải orchestrator production đầy đủ cho cluster lớn. `depends_on` không đảm bảo app dependency đã ready về mặt nghiệp vụ, chỉ kiểm soát thứ tự start cơ bản hoặc health condition nếu cấu hình. Compose cũng không tự giải quyết secret, backup, scaling, HA hoặc rollout an toàn.

## Core Mechanism / Cơ chế lõi

Compose tạo một project gồm nhiều service trên network chung, gắn volume, inject env và publish port ra host khi cần. Service có thể giao tiếp nhau bằng service name qua DNS nội bộ. Data bền vững phụ thuộc vào named volume/bind mount; nếu xóa volume hoặc đổi project/name sai, dữ liệu có thể biến mất khỏi stack hiện tại.

## Project Role / Vai trò trong dự án

Docker Compose giúp team tái tạo môi trường chạy local/staging nhẹ và mô tả dependency runtime của app. Khi debug, Compose là nơi kiểm tra service name, port mapping, env var, volume path, healthcheck, log container và thứ tự start giữa app với database/cache/queue.

## Output / Artifact nên có

- `compose.yaml` với service, image/build, ports, networks, volumes, env, healthcheck
- `.env.example` hoặc config note cho biến môi trường cần thiết
- Data volume decision: named volume hay bind mount, backup path nếu có dữ liệu quan trọng
- Startup/debug commands: up/down/logs/exec/ps/config
- Integration test hoặc smoke test sau khi stack chạy

## Decision Checklist / Câu hỏi kiểm tra

- Service trong compose gọi nhau bằng service name hay nhầm `localhost`?
- Port publish ra host có conflict hoặc expose quá rộng không?
- Database/cache data nằm ở named volume hay bind mount nào?
- `.env` có chứa secret thật bị commit không?
- `depends_on` có đủ hay cần healthcheck/wait-for readiness?
- Compose file có khác production quá nhiều làm dev/staging lệch behavior không?
- Khi chạy `docker compose down -v`, dữ liệu nào sẽ mất?

## Failure Modes / Cách nó gây lỗi

- App dùng `localhost` để gọi database nên trong container không kết nối được.
- Port mapping conflict làm service không start hoặc bind nhầm port.
- Volume path sai làm dữ liệu không persist hoặc ghi vào nơi không mong muốn.
- `depends_on` làm app start sau DB container nhưng DB chưa ready, gây crash/retry loop.
- Env var thiếu/sai làm local chạy khác staging/production.
- Commit `.env` chứa secret thật hoặc expose service nội bộ ra host/public interface.

## Khi nào chưa cần hoặc dễ over-engineer

- Một service đơn giản không dependency có thể chạy bằng `docker run` hoặc dev server trước.
- Không nên biến Compose thành production orchestrator phức tạp nếu cần HA, autoscaling, rolling update hoặc multi-node.
- Không nên mirror Kubernetes 1:1 trong Compose nếu mục tiêu chỉ là local dev nhanh và rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Docker]] vì Docker Compose điều phối nhiều Docker containers.
- [[Container]] vì mỗi service compose chạy như container/runtime unit.
- [[Volume]] vì Compose thường gắn named volume hoặc bind mount cho data.
- [[Environment Variable]] vì env là cách phổ biến để cấu hình service trong Compose.
- [[Health Check]] vì healthcheck giúp kiểm soát readiness tốt hơn `depends_on` đơn giản.

## Liên quan rộng

- Local development
- Integration testing
- Homelab deployment
- Developer onboarding

## Keywords / Từ khóa tìm kiếm

- Docker Compose
- compose file
- docker-compose
- compose.yaml
- docker compose up
- docker compose down
- service name DNS
- compose network
- compose volume
- bind mount
- named volume
- depends_on
- compose healthcheck
- port mapping
- docker compose debugging

## Source trace

- Docker Compose documentation
