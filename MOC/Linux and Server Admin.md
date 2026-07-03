# Linux and Server Admin

Aliases: Linux operations, server administration, quản trị server Linux

Type: MOC

## Context / Ngữ cảnh

Linux and Server Admin là vùng kiến thức để vận hành server, đọc log, quản lý service, network, quyền, storage và hardening.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node Linux/server admin cần khi deploy, debug và bảo vệ hệ thống.

### Nó không phải là gì

Nó không phải checklist học lệnh rời rạc; trọng tâm là hiểu layer và failure mode của server thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là quan sát và điều khiển process, filesystem, permission, network, service lifecycle, logs và security boundary.

## Project Role / Vai trò trong dự án

MOC này giúp nối DevOps, cloud, backend và debugging với nền Linux thực tế.

## Output / Artifact nên có

- Server runbook
- Service config note
- Debug command checklist
- Hardening checklist

## Decision Checklist / Câu hỏi kiểm tra

- Service chạy bằng user nào và có quyền gì?
- Log, metric và restart path nằm ở đâu?
- Network port nào đang expose ra ngoài?
- Backup/restore và update path có rõ không?

## Failure Modes / Cách nó gây lỗi

- Không hiểu systemd/process làm service chết nhưng không biết restart/debug
- Permission hoặc SSH config sai gây mất access hoặc lộ server
- Log đầy disk hoặc update thiếu làm incident khó xử lý

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào quá sâu nếu chỉ dùng managed PaaS và không chạm server
- Dễ over-engineer nếu hardening quá nhiều mà không có recovery path

## Gồm những gì

- [[Linux]]
- [[Linux Kernel]]
- [[Linux Distribution]]
- [[Shell]]
- [[Bash]]
- [[Terminal]]
- [[Command Line]]
- [[Shell Script]]
- [[POSIX]]
- [[GNU Coreutils]]
- [[Man Page]]
- [[Environment Path]]
- [[Exit Code]]
- [[Standard Input]]
- [[Standard Output]]
- [[Standard Error]]
- [[Pipe]]
- [[Redirection]]
- [[Linux Signal]]
- [[Process ID]]
- [[Parent Process]]
- [[Daemon]]
- [[Fork]]
- [[Exec]]
- [[Zombie Process]]
- [[Orphan Process]]
- [[Cron]]
- [[Systemd]]
- [[Systemd Unit]]
- [[Systemd Service]]
- [[Systemd Timer]]
- [[Journalctl]]
- [[Syslog]]
- [[Logrotate]]
- [[Linux Filesystem Hierarchy]]
- [[Root Directory]]
- [[Home Directory]]
- [[Etc Directory]]
- [[Var Directory]]
- [[Proc Filesystem]]
- [[Sys Filesystem]]
- [[Mount Point]]
- [[Filesystem Mount]]
- [[Fstab]]
- [[Block Device]]
- [[Disk Partition]]
- [[LVM]]
- [[Swap]]
- [[Inode]]
- [[Hard Link]]
- [[Symbolic Link]]
- [[File Permission]]
- [[File Ownership]]
- [[Linux User]]
- [[Linux Group]]
- [[Root User]]
- [[Sudo]]
- [[Umask]]
- [[Linux ACL]]
- [[SSH]]
- [[SSH Key]]
- [[Authorized Keys]]
- [[SSH Agent]]
- [[SCP]]
- [[SFTP]]
- [[Rsync]]
- [[Linux Firewall]]
- [[UFW]]
- [[iptables]]
- [[nftables]]
- [[Port Forwarding]]
- [[DNS Resolver]]
- [[Hosts File]]
- [[Network Interface]]
- [[IP Address]]
- [[Subnet]]
- [[Gateway]]
- [[Routing Table]]
- [[Listening Port]]
- [[ss Command]]
- [[Netstat]]
- [[Curl]]
- [[Wget]]
- [[Ping]]
- [[Traceroute]]
- [[Tcpdump]]
- [[Nmap]]
- [[Package Manager]]
- [[APT]]
- [[DNF]]
- [[Pacman]]
- [[System Update]]
- [[Service Restart]]
- [[Process Monitoring]]
- [[top]]
- [[htop]]
- [[ps Command]]
- [[Kill Command]]
- [[CPU Usage]]
- [[Load Average]]
- [[Memory Usage]]
- [[Disk Usage]]
- [[Disk IO]]
- [[IO Wait]]
- [[File Descriptor]]
- [[Ulimit]]
- [[Cgroup]]
- [[Namespace]]
- [[SELinux]]
- [[AppArmor]]
- [[Fail2ban]]
- [[SSH Hardening]]
- [[Server Hardening]]
- [[Security Patch]]
- [[Backup Job]]
- [[Restore Drill]]
- [[Log File]]
- [[Configuration File]]
- [[System Boot]]
- [[Bootloader]]
- [[Kernel Module]]
- [[Device File]]
- [[TTY]]
- [[Pseudo Terminal]]
- [[Screen]]
- [[Tmux]]
- [[Linux Server]]

## Nối mạnh

- [[Deployment and Operations]] vì Linux là runtime nền của nhiều deployment
- [[Cloud and Infrastructure]] vì cloud VM/container thường chạy trên Linux
- [[Debugging and Failure Patterns]] vì production debugging hay bắt đầu từ logs/process/network
- [[Security]] vì server hardening là security boundary thực tế

## Liên quan rộng

- Server operations
- Linux administration
- Infrastructure debugging

## Keywords / Từ khóa tìm kiếm

- Linux
- server admin
- Linux operations
- systemd
- SSH
- filesystem
- permissions
- networking
- logs
- quản trị server
- vận hành Linux

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
