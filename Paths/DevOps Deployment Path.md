# DevOps Deployment Path

## Mục tiêu

Path này giúp người đọc hiểu cách code đi từ source tới build, release, deploy, monitor và rollback.

## Khi nào dùng path này

- Khi thiết kế CI/CD hoặc deployment workflow.
- Khi debug lỗi deploy, rollback hoặc environment config.
- Khi muốn nối software delivery với reliability.

## 1. Build và validation

- [[CI]] — chạy build/test tự động khi code thay đổi.
- [[Build Pipeline]] — chuỗi bước tạo artifact và validate.
- [[Test Coverage]] — signal về mức code được test chạm tới.
- [[Static Testing]] — kiểm tra code/config trước runtime.
- [[Dependency Scanning]] — kiểm tra dependency rủi ro.

## 2. Artifact và configuration

- [[Container Image]] — artifact phổ biến cho deploy hiện đại.
- [[Container Registry]] — nơi lưu và phát hành image.
- [[Environment Variable]] — config runtime theo environment.
- [[Secret]] — dữ liệu nhạy không nên hard-code.
- [[Infrastructure as Code]] — mô tả hạ tầng bằng file/version control.

## 3. Release và deployment

- [[CD]] — tự động đưa artifact tới environment.
- [[Deployment]] — đưa version mới vào chạy.
- [[Deployment Strategy]] — chọn cách rollout để giảm rủi ro.
- [[Blue-Green Deployment]] — chạy hai environment để switch nhanh.
- [[Canary Release]] — rollout nhỏ trước khi mở rộng.
- [[Feature Flag]] — bật/tắt feature mà không cần deploy lại.

## 4. Runtime operation

- [[Health Check]] — kiểm tra service sống/sẵn sàng.
- [[Graceful Shutdown]] — tắt service không làm rơi request/job.
- [[Monitoring]] — đo system health.
- [[Logging]] — ghi signal để debug.
- [[Alert]] — gọi người xử lý khi signal vượt ngưỡng.

## 5. Reliability loop

- [[SLO]] — mục tiêu reliability đo được.
- [[Error Budget]] — ngân sách lỗi để cân bằng speed và stability.
- [[Incident Response]] — phản ứng khi service ảnh hưởng user.
- [[Rollback]] — quay lui khi release lỗi.
- [[Postmortem]] — học từ incident và tạo action.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Release train
- Deployment approval
- Artifact signing
- Environment promotion
- GitOps

## Related paths

- [[Cloud Infrastructure Path]]
- [[Debugging and Failure Patterns Path]]
- [[Security Engineering Path]]
- [[Backend Engineering Path]]
