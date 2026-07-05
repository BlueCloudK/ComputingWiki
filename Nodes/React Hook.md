# React Hook

Aliases: React Hook, Hook

Type: Frontend Framework

## Context / Ngữ cảnh

React Hook xuất hiện khi React function component cần dùng state, side effect, ref, context hoặc logic tái sử dụng mà không viết class component.

## Boundary / Ranh giới

### Nó là gì

React Hook là function đặc biệt trong React cho phép component hoặc custom hook kết nối với React state/lifecycle/context system.

### Nó không phải là gì

React Hook không phải function tiện ích bình thường. Hook phải tuân thủ rule về nơi gọi và thứ tự gọi để React map state/effect đúng giữa các render.

## Core Mechanism / Cơ chế lõi

React lưu hook state theo thứ tự gọi trong component render. Khi component render lại, React dựa vào cùng thứ tự hook để trả đúng state/ref/effect. Custom hook chỉ là cách đóng gói hook logic thành function tái sử dụng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug stale closure, dependency array, rerender loop, custom hook design, useEffect side effect hoặc useRef/useState/useMemo behavior.

## Output / Artifact nên có

- Hook responsibility note
- Dependency array reasoning
- Side effect cleanup rule
- Custom hook API contract
- Test cho behavior hook quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Hook có được gọi ở top-level component/custom hook không?
- Dependency array có đủ giá trị được capture không?
- Effect có cleanup không?
- State này có cần hook hay derive từ props được?
- Custom hook có expose API rõ không?

## Failure Modes / Cách nó gây lỗi

- Gọi hook trong condition/loop làm thứ tự hook sai.
- Dependency array thiếu làm stale closure.
- Effect update state vô hạn gây rerender loop.
- Không cleanup subscription/timer gây leak.
- Custom hook ôm quá nhiều trách nhiệm.

## Khi nào chưa cần hoặc dễ over-engineer

- Logic thuần không cần React state/effect thì viết function thường.
- Không nên tạo custom hook chỉ để đổi tên code chưa có pattern lặp lại.

## Gồm những gì

- [[useRef]]

## Nối mạnh

- [[React]] vì hook là cơ chế lõi trong React function component.
- [[Component]] vì hook chạy trong component/custom hook.
- [[State Management]] vì hook thường quản lý local/component state.
- [[Memory Leak]] vì effect cleanup sai có thể gây leak.

## Liên quan rộng

- useState
- useEffect
- useMemo
- Custom hook

## Keywords / Từ khóa tìm kiếm

- React Hook
- Hook
- useEffect
- useState
- dependency array
- stale closure
- custom hook
- React hook debugging

## Source trace

- React documentation
