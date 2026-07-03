# Business Workflow

Aliases: Business Workflow, business workflow, workflow nghiệp vụ, luồng nghiệp vụ

Type: Application Engineering

## Context / Ngữ cảnh

Business Workflow xuất hiện khi xây application thật cần chuỗi bước nghiệp vụ từ trigger tới outcome có thể kiểm chứng.

## Boundary / Ranh giới

### Nó là gì

Business Workflow là khái niệm giúp đặt đúng boundary, responsibility và artifact trong application engineering.

### Nó không phải là gì

Nó không phải nhãn chung để gắn vào mọi phần code; nếu không chỉ ra responsibility cụ thể thì dễ làm kiến trúc mơ hồ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định chuỗi bước nghiệp vụ từ trigger tới outcome có thể kiểm chứng, ai sở hữu quyết định đó, input/output là gì, và failure mode xảy ra ở boundary nào.

## Project Role / Vai trò trong dự án

Business Workflow giúp team nối requirement, code, test, deploy và debug bằng cùng một ngôn ngữ thay vì chỉ nhìn từng file rời rạc.

## Output / Artifact nên có

- Decision note hoặc diagram nhỏ cho Business Workflow
- Test hoặc checklist cho behavior quan trọng
- Owner/boundary rõ nếu concept ảnh hưởng nhiều module hoặc service

## Decision Checklist / Câu hỏi kiểm tra

- Business Workflow đang bảo vệ boundary hoặc responsibility nào?
- Có artifact nào giúp người khác review hoặc debug quyết định này không?
- Nếu behavior thay đổi, test/metric/contract nào sẽ báo sớm?

## Failure Modes / Cách nó gây lỗi

- Dùng Business Workflow sai boundary làm code phụ thuộc chéo hoặc khó test
- Không có owner rõ khiến bug bị đẩy qua lại giữa layer/module
- Thiếu test/contract làm lỗi chỉ lộ khi tích hợp hoặc deploy

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Business Workflow nếu app nhỏ, behavior đơn giản và chưa có pain thật
- Dễ over-engineer nếu tạo nhiều layer/process trước khi có boundary hoặc failure mode rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Workflow Orchestration]] vì liên quan trực tiếp tới cách áp dụng Business Workflow
- [[Use Case]] vì liên quan trực tiếp tới cách áp dụng Business Workflow

## Liên quan rộng

- Application engineering
- Project architecture
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Business Workflow
- business workflow
- workflow nghiệp vụ
- luồng nghiệp vụ
- business
- workflow

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
