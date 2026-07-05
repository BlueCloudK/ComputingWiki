# SWR

Aliases: SWR, stale-while-revalidate

Type: Frontend Framework

## Context / Ngữ cảnh

SWR xuất hiện khi frontend cần lấy server data, cache phía client và cập nhật lại dữ liệu mà không tự viết toàn bộ loading/error/cache logic.

## Boundary / Ranh giới

### Nó là gì

SWR là data fetching/cache library cho React, dựa trên ý tưởng trả dữ liệu cached trước rồi revalidate phía sau.

### Nó không phải là gì

SWR không phải database, không thay thế API contract và không phải global UI state manager cho mọi loại state.

## Core Mechanism / Cơ chế lõi

Component gọi hook với cache key và fetcher. SWR trả data/loading/error từ cache/request hiện tại, tự revalidate theo rule và cập nhật component khi dữ liệu đổi.

## Project Role / Vai trò trong dự án

Dùng node này khi debug data fetching, cache key, stale data, loading/error state, optimistic update hoặc invalidation trong React UI.

## Output / Artifact nên có

- Cache key convention
- Fetcher/error shape
- Loading/error/empty UI state
- Mutation/invalidation rule
- Test cho flow data quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Cache key có đủ parameter phân biệt request không?
- Data này là server state hay client UI state?
- Sau mutation có invalidate/mutate đúng không?
- Loading/error/empty state có render rõ không?
- Revalidation frequency có gây request dư không?

## Failure Modes / Cách nó gây lỗi

- Cache key thiếu parameter làm data lẫn nhau.
- UI dùng data stale sau mutation.
- Fetcher trả shape không khớp component.
- Loading/error state bị bỏ qua.
- Revalidation quá nhiều gây noise hoặc cost.

## Khi nào chưa cần hoặc dễ over-engineer

- Data local đơn giản không cần SWR.
- Không nên dùng SWR để che API contract chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[React]] vì SWR thường dùng trong React app.
- [[State Management]] vì SWR quản lý server state phía client.
- [[Cache]] vì SWR dựa trên cache key và revalidation.
- [[Stale Cache]] vì stale data là failure mode chính.

## Liên quan rộng

- Data fetching
- Frontend cache
- Server state

## Keywords / Từ khóa tìm kiếm

- SWR
- stale-while-revalidate
- React data fetching
- cache key
- server state
- revalidation
- mutate
- SWR debugging

## Source trace

- SWR documentation
- React documentation
