# Spring Boot

Aliases: Spring Boot, Spring framework boot, Java backend framework

Type: Framework / Backend

## Context / Ngữ cảnh

Spring Boot là framework Java giúp dựng backend service với auto-configuration, embedded server và hệ sinh thái Spring.

## Boundary / Ranh giới

### Nó là gì

Nó là application framework cho dependency injection, web endpoint, data access, security, configuration và production actuator.

### Nó không phải là gì

Nó không thay thế hiểu biết về HTTP, transaction, thread pool, database hoặc JVM runtime.

## Core Mechanism / Cơ chế lõi

Spring Boot quét component, tạo application context, auto-config bean theo dependency/config và chạy app qua embedded servlet/reactive server.

## Project Role / Vai trò trong dự án

Node này giúp đọc Java backend, debug bean wiring, config profile, endpoint behavior, security filter chain và production health/metrics.

## Output / Artifact nên có

- Application configuration theo profile
- Controller/service/repository boundary rõ
- Actuator health/metrics config cho production

## Decision Checklist / Câu hỏi kiểm tra

- Auto-configuration nào đang được bật do dependency nào?
- Bean conflict hoặc circular dependency có bị che bởi config không?
- Transaction boundary nằm ở service nào?
- Profile dev/staging/prod có khác behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Bean wiring sai làm app fail lúc startup
- Profile/config lệch làm production dùng datasource hoặc secret sai
- Lazy query hoặc transaction boundary sai gây lỗi database khó thấy trong local

## Khi nào chưa cần hoặc dễ over-engineer

- Overkill cho script nhỏ hoặc service rất đơn giản không cần hệ sinh thái Spring
- Dễ over-engineer nếu mọi logic đều bị nhồi annotation/config mà thiếu boundary rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dependency Injection]] vì Spring Boot dựa mạnh vào container và bean lifecycle
- [[Service Layer]] vì đây thường là nơi đặt transaction và business logic

## Liên quan rộng

- Java backend
- Enterprise application
- Web API

## Keywords / Từ khóa tìm kiếm

- Spring Boot
- Spring framework
- Java backend
- auto configuration
- application context
- Spring actuator
- Spring profile
- Java service

## Source trace

- Spring Boot official documentation
