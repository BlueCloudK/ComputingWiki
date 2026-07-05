# React Native

Aliases: React Native

Type: Mobile Development

## Context / Ngữ cảnh

React Native xuất hiện khi team muốn xây mobile app bằng JavaScript/React model nhưng vẫn dùng native platform capability của Android và iOS.

## Boundary / Ranh giới

### Nó là gì

React Native là framework mobile dùng React component model để xây app Android/iOS với native component, JavaScript runtime và native module bridge/runtime architecture.

### Nó không phải là gì

React Native không phải web React chạy nguyên trong browser. Nó target mobile runtime và native platform.

## Core Mechanism / Cơ chế lõi

App dùng component React Native, JavaScript runtime, native module và bridge/runtime để gọi capability của Android/iOS. Build pipeline tạo artifact riêng cho từng platform.

## Project Role / Vai trò trong dự án

Dùng node này khi debug mobile UI, native module, build Android/iOS, navigation, performance bridge/runtime hoặc platform-specific behavior.

## Output / Artifact nên có

- Component/navigation map
- Native module list
- Platform build note
- State/data flow note
- Test checklist theo Android/iOS

## Decision Checklist / Câu hỏi kiểm tra

- Feature này thuần JS hay cần native module?
- Android/iOS behavior có khác nhau không?
- Build artifact cần APK/AAB hay IPA?
- Performance có bị ảnh hưởng bởi bridge/runtime không?
- Native permission/config đã đủ chưa?

## Failure Modes / Cách nó gây lỗi

- Native module thiếu config theo platform.
- Android/iOS behavior lệch nhau.
- Build local pass nhưng release fail.
- State/UI flow giống React web nhưng platform mobile khác expectation.
- Bridge/runtime overhead làm interaction chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- App chỉ là web đơn giản có thể chưa cần native mobile framework.
- Không nên dùng native module nếu API cross-platform có sẵn đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[React]] vì React Native dùng React component model.
- [[APK]] vì Android build có thể tạo APK.
- [[AAB]] vì Android release có thể dùng AAB.
- [[iOS]] vì React Native cũng target iOS.
- [[Xcode]] vì iOS side thường cần Xcode/toolchain.

## Liên quan rộng

- Cross-platform mobile
- Native module
- Mobile UI

## Keywords / Từ khóa tìm kiếm

- React Native
- mobile React
- native module
- Android iOS app
- bridge
- React Native debugging

## Source trace

- React Native documentation
- React documentation
