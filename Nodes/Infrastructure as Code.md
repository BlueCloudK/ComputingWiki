# Infrastructure as Code

Aliases: IaC, hạ tầng dưới dạng code

Type: Deployment / Operations

## Context / Ngữ cảnh

Infrastructure as Code xuất hiện khi resource hạ tầng cần được tạo, thay đổi và review như một phần của delivery thay vì thao tác tay trong console.

## Boundary / Ranh giới

### Nó là gì

Infrastructure as Code là cách mô tả infrastructure bằng file có version để provision/update resource lặp lại được.

### Nó không phải là gì

Nó không phải chỉ là script deploy, không tự bảo đảm architecture tốt, và không loại bỏ nhu cầu review security/cost.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là desired state hoặc imperative steps được lưu trong repo, review qua diff, apply bằng tool và theo dõi drift giữa code với resource thật.

## Project Role / Vai trò trong dự án

IaC làm environment reproducible hơn, giảm manual drift và giúp rollback/review thay đổi hạ tầng. Nó đặc biệt hữu ích khi có nhiều environment hoặc cloud resource.

## Output / Artifact nên có

- IaC module/config cho resource quan trọng
- Plan/diff trước khi apply
- State, secret và drift handling note

## Decision Checklist / Câu hỏi kiểm tra

- Resource nào phải được quản lý bằng code?
- State file và secret được bảo vệ thế nào?
- Change hạ tầng có review/plan trước apply không?
- Drift được phát hiện và xử lý ra sao?
- Module có quá generic so với nhu cầu hiện tại không?

## Failure Modes / Cách nó gây lỗi

- Apply nhầm workspace/environment làm hỏng production
- State leak chứa secret hoặc metadata nhạy cảm
- Console change ngoài IaC tạo drift khó debug
- Module abstraction quá sớm làm change nhỏ trở nên khó hiểu

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần IaC nặng cho một prototype không deploy lâu dài
- Dễ over-engineer nếu viết platform module phức tạp trước khi resource shape ổn định

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cloud Computing]] vì cloud resource rất hợp quản lý qua IaC
- [[Change Control]] vì infrastructure change cần review, impact và rollback
- [[Rollback]] vì IaC giúp quay lại hoặc tái tạo cấu hình hạ tầng

## Liên quan rộng

- Terraform
- CloudFormation
- Pulumi
- Drift detection

## Source trace

- Terraform official docs
- AWS Well-Architected Framework
