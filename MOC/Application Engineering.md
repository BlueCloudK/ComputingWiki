# Application Engineering

Aliases: application engineering, applied software engineering, kỹ nghệ ứng dụng

Type: MOC

## Context / Ngữ cảnh

Application Engineering là vùng nối requirement, architecture, code, data, integration, test, release và operation để xây application thật.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các khái niệm thực hành khi biến ý tưởng hoặc requirement thành application có thể chạy, test, deploy và vận hành.

### Nó không phải là gì

Nó không thay thế các MOC Backend, Web, Database hay Security; nó nối các vùng đó theo flow làm project.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là nhìn application qua boundary, responsibility, contract, state, data, delivery và failure mode.

## Project Role / Vai trò trong dự án

MOC này giúp chọn đúng node khi thiết kế feature, chia layer/module, viết test, chuẩn bị release hoặc debug production.

## Output / Artifact nên có

- Application architecture note
- Boundary/module map
- Contract, test và release checklist

## Decision Checklist / Câu hỏi kiểm tra

- Feature này đi qua requirement, API, domain, data, test và deploy thế nào?
- Boundary nào cần rõ để tránh code phụ thuộc chéo?
- Failure mode nào phải có test, log hoặc runbook?

## Failure Modes / Cách nó gây lỗi

- Chỉ có node rời rạc nhưng không có flow project
- Layer/module đặt tên đúng nhưng responsibility mơ hồ
- Thiếu contract/test/release boundary làm lỗi lộ muộn

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ một màn hình có thể chưa cần quá nhiều layer/process
- Dễ over-engineer nếu thêm pattern trước khi có boundary hoặc failure mode thật

## Gồm những gì

- [[Application Architecture]]
- [[Application Service]]
- [[Domain Service]]
- [[Domain Layer]]
- [[Infrastructure Layer]]
- [[Presentation Layer]]
- [[Use Case Interactor]]
- [[Command Handler]]
- [[Query Handler]]
- [[Business Rule]]
- [[Invariant]]
- [[Value Object]]
- [[Aggregate]]
- [[Aggregate Root]]
- [[Entity Identity]]
- [[Domain Boundary]]
- [[Application Boundary]]
- [[Module Boundary]]
- [[Module]]
- [[Package]]
- [[Dependency Boundary]]
- [[Interface Adapter]]
- [[DTO Mapper]]
- [[Exception Mapping]]
- [[Error Taxonomy]]
- [[Application Configuration]]
- [[Configuration Management]]
- [[Request Context]]
- [[Correlation ID]]
- [[API Client]]
- [[External Service Client]]
- [[Third Party Integration]]
- [[Integration Boundary]]
- [[Anti Corruption Layer]]
- [[Ports and Adapters]]
- [[Hexagonal Architecture]]
- [[Clean Architecture]]
- [[Layered Architecture]]
- [[Onion Architecture]]
- [[CQRS]]
- [[Command Query Separation]]
- [[Read Model]]
- [[Write Model]]
- [[Business Workflow]]
- [[Workflow Orchestration]]
- [[State Transition]]
- [[Application State]]
- [[Session State]]
- [[User Account]]
- [[Role]]
- [[Permission]]
- [[Authorization Policy]]
- [[Permission Model]]
- [[Tenant]]
- [[Multi Tenancy]]
- [[Data Isolation]]
- [[Audit Trail]]
- [[Idempotency Key]]
- [[Request Timeout]]
- [[Input Sanitization]]
- [[Output Contract]]
- [[API Schema]]
- [[Schema Validation]]
- [[Contract Test]]
- [[Consumer Driven Contract]]
- [[Smoke Test]]
- [[Test Fixture]]
- [[Seed Data]]
- [[Migration Test]]
- [[Test Environment]]
- [[Staging Environment]]
- [[Production Environment]]
- [[Local Development Environment]]
- [[Feature Rollout]]
- [[Operational Runbook]]
- [[Support Playbook]]
- [[Incident Runbook]]
- [[Observability]]
- [[Metric]]
- [[Log Level]]
- [[Structured Logging]]
- [[Environment Parity]]
- [[Software Dependency]]
- [[Version Pinning]]
- [[Build Artifact]]
- [[Release Candidate]]
- [[Changelog]]
- [[Semantic Versioning]]
- [[Deprecation Policy]]
- [[Compatibility Policy]]
- [[Backward Compatibility]]
- [[Forward Compatibility]]
- [[API Deprecation]]
- [[Data Validation]]
- [[Domain Validation]]
- [[Boundary Validation]]
- [[Attack Surface]]

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Backend Engineering vì application engineering thường đi qua backend/service flow
- Web Development vì nhiều application có browser/UI boundary
- Database Systems vì application state thường nằm trong database
- Security vì application boundary thường là attack surface
- Application architecture
- Product engineering
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Application Engineering
- application architecture
- app engineering
- applied software engineering
- project architecture
- feature delivery
- kỹ nghệ ứng dụng
- kiến trúc ứng dụng

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
