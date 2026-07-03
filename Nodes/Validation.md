# Validation

Aliases: data validation, kiểm tra dữ liệu

Type: Requirement / Planning

## Bản chất

Validation là phần làm rõ nhu cầu, phạm vi hoặc tiêu chí chấp nhận trước khi team thiết kế và code. Điểm quan trọng là nó phải đủ đo được: biết ai cần gì, điều kiện nào được xem là đạt, và trace được từ stakeholder sang design/test. Nếu phần này mơ hồ, downstream sẽ sinh tranh luận ở lúc review hoặc QA. Nó nối với các phần liên quan như [[Input Validation]], [[API Contract]].

## Dùng trong dự án để làm gì

Validation ảnh hưởng trực tiếp tới scope, acceptance criteria, test case và ưu tiên triển khai. Trong dự án, nó giúp biến mong muốn mơ hồ thành quyết định có thể kiểm chứng: feature nào làm, feature nào không làm, và thay đổi nào cần cập nhật trace.

## Khi nào cần quan tâm

- Stakeholder dùng từ mơ hồ như nhanh, ổn định, dễ dùng, bảo mật hoặc linh hoạt
- Developer và tester hiểu khác nhau về hành vi cần giao
- Acceptance criteria chưa đo được hoặc chưa có điều kiện pass/fail
- Một thay đổi scope kéo theo design/test nhưng chưa được trace

## Output / artifact nên có

- Acceptance criteria hoặc decision note rõ điều kiện pass/fail
- Trace từ requirement sang design, test và release scope
- Danh sách assumption/open question cần stakeholder xác nhận

## Checklist kiểm tra

- Tiêu chí này có đo được bằng test, metric hoặc review không?
- Ai là stakeholder/consumer chịu ảnh hưởng chính?
- Có acceptance criteria đủ rõ để tester kết luận pass/fail chưa?
- Requirement này có trace tới design và test case liên quan chưa?
- Nếu scope đổi, node nào phải cập nhật theo?

## Lỗi / rủi ro thường gặp

- Build đúng theo suy đoán của dev nhưng sai nhu cầu thật
- Acceptance mơ hồ làm QA không kết luận được
- Scope creep vì không ghi rõ out-of-scope
- Trace thiếu khiến sửa requirement nhưng quên sửa test/design

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal hóa quá mạnh khi chỉ là prototype cá nhân hoặc spike ngắn
- Dễ over-engineer nếu biến mọi ý tưởng nhỏ thành quy trình requirement nặng nề

## Gồm những gì

- [[Input Validation]]
- [[API Contract]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Requirements Engineering Map / OWASP Map
