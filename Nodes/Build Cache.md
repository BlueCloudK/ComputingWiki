# Build Cache

Aliases: Build Cache, build cache

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Build Cache xuất hiện khi build/test/install lặp lại nhiều lần trong local hoặc CI và team muốn giảm thời gian bằng cách tái sử dụng dependency, compiled output, test cache hoặc intermediate artifact. Nó thường dùng trong npm, Gradle, Maven, Docker layer, GitHub Actions cache và monorepo build system.

## Boundary / Ranh giới

### Nó là gì

Build Cache là cơ chế lưu lại kết quả trung gian của build/test/install để lần sau không phải làm lại nếu input không đổi. Cache tốt cần key đúng, restore đúng, invalidate đúng và không làm build mất tính reproducible.

### Nó không phải là gì

Build Cache không phải artifact release chính thức và không nên là source of truth. Cache có thể bị xóa bất cứ lúc nào, stale hoặc sai key. Nếu build chỉ đúng khi có cache, pipeline đang có vấn đề reproducibility.

## Core Mechanism / Cơ chế lõi

Pipeline tính cache key từ input như lockfile, OS, runtime version, compiler version, package manager config hoặc build config. Nếu cache hit, runner restore thư mục cache; nếu miss, build/install chạy lại rồi save cache. Invalidation xảy ra khi key đổi hoặc cache bị evict.

## Project Role / Vai trò trong dự án

Build Cache giúp CI nhanh hơn và dev feedback tốt hơn. Nó cần được thiết kế cẩn thận vì cache sai có thể tạo lỗi rất khó debug: local/CI khác nhau, dependency cũ, build output stale hoặc test pass giả.

## Output / Artifact nên có

- Cache target: dependency, compiler cache, test cache, Docker layer, build output
- Cache key formula gồm lockfile/runtime/OS/config quan trọng
- Restore key fallback nếu dùng
- Cache invalidation/debug note
- Metric: cache hit rate, time saved, cache size, flaky/stale incidents

## Decision Checklist / Câu hỏi kiểm tra

- Cache này lưu dependency hay build output?
- Key có chứa lockfile, runtime version, OS và config quan trọng chưa?
- Cache hit sai có thể tạo build pass giả không?
- Cache miss có làm pipeline vẫn chạy đúng không?
- Cache có bị chia sẻ giữa branch/matrix không phù hợp không?
- Có cách clear/bypass cache khi debug không?
- Cache có đáng cost/complexity so với thời gian tiết kiệm không?

## Failure Modes / Cách nó gây lỗi

- Cache key thiếu lockfile làm dùng dependency cũ.
- Cache dùng chung giữa OS/runtime làm binary/native module sai.
- Cache restore build output stale làm test pass nhưng source mới chưa build đúng.
- Pipeline chỉ xanh khi cache tồn tại, cache miss thì fail.
- Cache quá lớn làm restore/save còn chậm hơn build lại.
- Debug khó vì local clean install khác CI cache hit.

## Khi nào chưa cần hoặc dễ over-engineer

- Pipeline nhỏ chạy nhanh có thể chưa cần cache.
- Không nên cache output nhạy cảm nếu artifact có secret hoặc environment-specific data.
- Không nên thêm cache phức tạp trước khi đo bottleneck pipeline thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì build cache thường dùng để tăng tốc CI pipeline.
- [[GitHub Actions]] vì Actions cache là cơ chế phổ biến trong workflow GitHub.
- [[Matrix Build]] vì cache key phải tách theo matrix variable.
- [[npm]] vì dependency cache/lockfile là case phổ biến.
- [[CD]] vì cache không được thay thế release artifact trong deployment pipeline.

## Liên quan rộng

- Build performance
- Reproducible build
- Dependency install
- CI optimization

## Keywords / Từ khóa tìm kiếm

- Build Cache
- build cache
- CI cache
- dependency cache
- cache key
- restore key
- cache invalidation
- GitHub Actions cache
- Docker layer cache
- npm cache
- build reproducibility
- stale cache
- build cache debugging

## Source trace

- GitHub Actions cache documentation
- Continuous Delivery
