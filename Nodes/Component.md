# Component

Aliases: software component, UI component, thành phần phần mềm

Type: Architecture / System Design

## Context / Ngữ cảnh

Component xuất hiện khi hệ thống hoặc UI cần chia thành các phần có responsibility rõ. Trong frontend, component là đơn vị UI có props/state/render/event. Trong system design, component là phần hệ thống có boundary, interface, dependency và owner riêng.

## Boundary / Ranh giới

### Nó là gì

Component là một đơn vị cấu trúc có responsibility, input/output và dependency rõ. Với UI, component nhận props/data, có thể giữ state cục bộ, render view và phát event/callback. Với system, component expose interface và che implementation detail bên trong.

### Nó không phải là gì

Component không chỉ là file hoặc class. Nếu một “component” biết quá nhiều việc, gọi quá nhiều dependency hoặc không có interface rõ, nó chỉ là code được đặt tên. Component cũng không tự tạo kiến trúc tốt nếu responsibility và data flow vẫn lẫn lộn.

## Core Mechanism / Cơ chế lõi

Component nhận input qua props/API/interface, xử lý logic thuộc responsibility của nó, dùng dependency được truyền vào hoặc import, rồi trả output qua render/event/return value. Composition ghép component nhỏ thành component lớn. Boundary tốt làm thay đổi bên trong ít ảnh hưởng bên ngoài.

## Project Role / Vai trò trong dự án

Component là node cần mở khi chia UI, refactor module, vẽ architecture diagram hoặc debug ownership. Nó giúp team hỏi component này sở hữu state nào, nhận props gì, phát event gì, phụ thuộc ai và có đang gánh quá nhiều responsibility không.

## Output / Artifact nên có

- Component tree hoặc component diagram cho screen/system chính
- Component API: props/input, event/output, slot/children nếu có
- Responsibility note: component này làm gì và không làm gì
- State ownership: local/shared/server state nào thuộc component này
- Test story: unit/component test cho render, interaction, edge state

## Decision Checklist / Câu hỏi kiểm tra

- Component này có responsibility rõ không?
- Input/output có đủ explicit không?
- State thuộc component này hay nên nâng lên/tách ra store?
- Component có side effect/API call nằm đúng chỗ không?
- Có thể reuse component này mà không kéo theo dependency quá lớn không?
- Component có quá nhiều props hoặc quá nhiều mode không?
- Khi component fail, user/system thấy lỗi gì?

## Failure Modes / Cách nó gây lỗi

- God component gom UI, data fetching, validation, business logic và side effect.
- Props quá nhiều hoặc implicit làm component khó dùng lại.
- State đặt sai chỗ gây stale UI hoặc prop drilling.
- Side effect chạy trong render hoặc lifecycle sai làm loop/race.
- Component coupling với API/global store khiến test khó và reuse thấp.
- Component visual reusable nhưng behavior quá đặc thù làm abstraction rối.

## Khi nào chưa cần hoặc dễ over-engineer

- UI rất nhỏ có thể chưa cần component hierarchy phức tạp.
- Không nên tách component quá sớm nếu boundary chưa rõ và chỉ dùng một lần.
- Không nên tạo design-system-level component cho feature chưa ổn định.

## Gồm những gì

- [[Relationship]]

## Nối mạnh

- [[Frontend Framework]] vì component model là lõi của nhiều frontend framework.
- [[State Management]] vì component boundary quyết định state đặt ở đâu.
- [[CSR]] vì client-rendered UI thường được ghép từ component tree.
- [[Hydration]] vì SSR component phải khớp khi hydrate trên client.
- [[Unit Test]] vì component interaction/render có thể test ở mức unit/component.

## Liên quan rộng

- UI architecture
- System boundary
- Reusability
- Maintainability

## Keywords / Từ khóa tìm kiếm

- Component
- software component
- UI component
- thành phần phần mềm
- component boundary
- component responsibility
- component props
- component state
- component composition
- component tree
- God component
- reusable component
- component testing
- component debugging

## Source trace

- C4 Model
- React documentation
- Vue documentation
