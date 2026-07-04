# ConfigMap

Aliases: Kubernetes ConfigMap, config map

Type: Kubernetes

## Context / Ngữ cảnh

ConfigMap xuất hiện khi Pod cần nhận cấu hình không nhạy cảm như environment variable, config file, feature flag đơn giản, endpoint nội bộ hoặc runtime setting. Nó giúp tách cấu hình khỏi container image để cùng một image có thể chạy ở nhiều môi trường.

## Boundary / Ranh giới

### Nó là gì

ConfigMap là Kubernetes resource lưu key-value hoặc file-like config không nhạy cảm. Pod có thể dùng ConfigMap qua env var, `envFrom`, command argument hoặc volume mount. Nó phù hợp cho cấu hình app, không phù hợp cho password/token/secret.

### Nó không phải là gì

ConfigMap không phải Secret và không nên chứa credential, API key hoặc dữ liệu nhạy cảm. Nó cũng không tự đảm bảo app reload config khi nội dung đổi; tùy cách mount/env và cách app đọc config, có thể cần restart/rollout để config mới có hiệu lực.

## Core Mechanism / Cơ chế lõi

ConfigMap được tạo trong namespace và được Pod tham chiếu trong spec. Nếu dùng env var, giá trị được inject khi container start nên đổi ConfigMap thường không đổi env trong container đang chạy. Nếu mount dạng volume, file có thể update sau một thời gian, nhưng app vẫn phải đọc lại file hoặc restart để áp dụng.

## Project Role / Vai trò trong dự án

ConfigMap ảnh hưởng tới deploy, environment configuration và debug lỗi “local chạy, cluster không chạy”. Khi review Kubernetes app, team phải biết cấu hình nào nằm ở image, values/chart, ConfigMap, Secret và rollout nào cần chạy khi config thay đổi.

## Output / Artifact nên có

- ConfigMap manifest hoặc template tương ứng với từng environment
- Danh sách key config, owner và default/required value
- Mapping Pod dùng config qua env var hay volume mount
- Rollout strategy khi ConfigMap thay đổi
- Validation/test để phát hiện thiếu key hoặc sai format trước production

## Decision Checklist / Câu hỏi kiểm tra

- Config này có nhạy cảm không, có nên chuyển sang Secret không?
- App đọc config qua env var hay file mount?
- Khi ConfigMap đổi, Pod có cần restart/rollout không?
- ConfigMap và Deployment có cùng namespace không?
- Key config có schema/default/validation rõ không?
- Có config nào khác nhau giữa dev/staging/prod cần quản lý bằng Helm/Kustomize không?
- ConfigMap có bị dùng như database mini hoặc chứa quá nhiều logic không?

## Failure Modes / Cách nó gây lỗi

- Đưa secret vào ConfigMap làm lộ credential qua manifest/log/access cluster.
- Đổi ConfigMap nhưng Pod không restart nên app vẫn dùng config cũ.
- Thiếu key hoặc sai format làm container crash lúc startup.
- ConfigMap sai namespace/name khiến Pod không mount được hoặc env rỗng.
- Config quá phân tán giữa image, ConfigMap, Helm values và env làm khó debug.
- Dùng ConfigMap cho file quá lớn hoặc config động phức tạp làm vận hành rối.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ một môi trường có thể bắt đầu với env vars đơn giản trước khi tách nhiều ConfigMap.
- Không nên đưa mọi setting vào ConfigMap nếu chúng là constant của build/image.
- Config thay đổi realtime/phức tạp có thể cần config service hoặc reload mechanism riêng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì ConfigMap là resource cấu hình cơ bản trong Kubernetes.
- [[Deployment]] vì Pod spec trong Deployment thường tham chiếu ConfigMap.
- [[Helm]] vì Helm values thường render ra ConfigMap theo môi trường.
- [[Kubernetes Secret]] vì cần phân biệt rõ config không nhạy cảm và secret.

## Liên quan rộng

- Environment configuration
- Platform operations
- GitOps
- Application startup

## Keywords / Từ khóa tìm kiếm

- ConfigMap
- Kubernetes ConfigMap
- config map
- non-secret config
- envFrom
- config volume mount
- Kubernetes env var
- config rollout
- config reload
- missing config key
- configmap debugging
- Helm values ConfigMap
- Kubernetes configuration

## Source trace

- Kubernetes ConfigMap documentation
