# Linux Server Admin Path

## Mục tiêu

Path này giúp người đọc đi qua các khái niệm Linux/server admin cần để deploy, debug và vận hành service.

## Khi nào dùng path này

- Khi chuẩn bị vận hành Linux server.
- Khi debug service chết, log đầy, port không mở hoặc SSH lỗi.
- Khi cần hiểu nền Linux bên dưới Docker, Kubernetes hoặc cloud VM.

## 1. Shell và process

- [[Linux]] — nền hệ điều hành của server.
- [[Shell]] — interface chạy command và script.
- [[Bash]] — shell/script phổ biến.
- [[Process]] — đơn vị chương trình đang chạy.
- [[Process ID]] — định danh process để inspect hoặc signal.
- [[Exit Code]] — signal thành công/thất bại của command.

## 2. Service lifecycle

- [[Systemd]] — service manager phổ biến.
- [[Systemd Service]] — unit quản lý daemon/service.
- [[Journalctl]] — đọc log systemd.
- [[Service Restart]] — restart service có kiểm soát.
- [[Cron]] — chạy job theo lịch.

## 3. Filesystem và permission

- [[Linux Filesystem Hierarchy]] — biết config/log/data nằm đâu.
- [[File Permission]] — kiểm soát read/write/execute.
- [[File Ownership]] — owner/group của file.
- [[Sudo]] — chạy quyền cao theo policy.
- [[Symbolic Link]] — path alias thường gặp trong config/deploy.
- [[Disk Usage]] — tránh đầy disk làm service fail.

## 4. Network và remote access

- [[SSH]] — remote login an toàn.
- [[SSH Key]] — auth bằng key.
- [[Network Interface]] — card/interface nhận traffic.
- [[IP Address]] — địa chỉ host/service.
- [[Listening Port]] — port process đang mở.
- [[Linux Firewall]] — kiểm soát traffic vào/ra.
- [[Curl]] — test endpoint/API từ server.

## 5. Monitoring và debugging

- [[Logging]] — signal cơ bản của service.
- [[Log File]] — nơi event được ghi lại.
- [[Process Monitoring]] — xem process và resource.
- [[CPU Usage]] — kiểm tra CPU pressure.
- [[Memory Usage]] — kiểm tra RAM/swap.
- [[Disk IO]] — kiểm tra storage bottleneck.
- [[Tcpdump]] — bắt packet khi cần debug network sâu.

## 6. Security và maintenance

- [[SSH Hardening]] — giảm rủi ro remote access.
- [[Server Hardening]] — giảm attack surface server.
- [[Security Patch]] — cập nhật lỗ hổng.
- [[Backup Job]] — backup định kỳ.
- [[Restore Drill]] — kiểm tra backup phục hồi được.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- SELinux policy module
- Kernel panic
- Network bonding
- RAID recovery
- Cloud-init

## Related paths

- [[DevOps Deployment Path]]
- [[Cloud Infrastructure Path]]
- [[Debugging and Failure Patterns Path]]
- [[Security Engineering Path]]
