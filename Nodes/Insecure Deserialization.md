# Insecure Deserialization

Aliases: Insecure Deserialization, insecure deserialization, deserialization attack, deserialize không an toàn

Type: Security

## Context / Ngữ cảnh

Insecure Deserialization xuất hiện khi application deserialize dữ liệu không tin cậy thành object/runtime structure có thể kích hoạt behavior nguy hiểm. Nó thường gặp trong session/token custom, message queue payload, cache object, RPC, file import, plugin system hoặc legacy Java/.NET/PHP/Python serialization.

## Boundary / Ranh giới

### Nó là gì

Insecure Deserialization là lỗi khi dữ liệu serialized từ user/network/storage không tin cậy được parser/runtime biến lại thành object có side effect, gadget chain hoặc type ngoài dự kiến. Impact có thể từ tamper state, privilege escalation, auth bypass tới RCE tùy format/library và classpath.

### Nó không phải là gì

Insecure Deserialization không phải mọi JSON parsing. JSON schema validation vẫn cần, nhưng rủi ro deserialization nghiêm trọng hơn khi runtime tự khởi tạo object/class, chạy magic method, constructor, finalizer hoặc gadget chain. Nó cũng không được fix chỉ bằng base64/signature nếu verify sai hoặc secret lộ.

## Core Mechanism / Cơ chế lõi

App nhận serialized blob, decoder/deserializer đọc metadata/type/value rồi tạo object. Nếu attacker điều khiển blob và runtime có gadget class nguy hiểm, quá trình deserialize có thể chạy method ngoài ý muốn. Control tốt gồm không deserialize untrusted native objects, dùng safe data format, schema allowlist, signature/MAC đúng, versioning và sandbox/least privilege.

## Project Role / Vai trò trong dự án

Insecure Deserialization là node cần mở khi review session state, signed token, cache object, queue event, file import hoặc dependency dùng native serialization. Nó giúp team hỏi dữ liệu serialized đến từ đâu, ai có thể sửa, có verify integrity không và deserializer có allowlist type không.

## Output / Artifact nên có

- Serialization boundary inventory: session, queue, cache, file import, RPC, token
- Format decision: JSON/protobuf/schema format thay vì native object serialization nếu có thể
- Integrity/authenticity control: signature/MAC, key rotation, replay/expiry
- Type allowlist/schema validation và reject unknown type/field nguy hiểm
- Test case cho tampered payload, old version, unexpected type và oversized/deep object

## Decision Checklist / Câu hỏi kiểm tra

- Serialized data đến từ user/network/storage không tin cậy không?
- Deserializer có thể instantiate arbitrary class/type không?
- Có gadget chain/dependency known risk trong runtime không?
- Payload có signature/MAC và verify trước khi deserialize không?
- Có expiry/replay protection cho serialized session/token không?
- Có limit size/depth để tránh resource exhaustion không?
- Có thể đổi sang data-only format với schema allowlist không?

## Failure Modes / Cách nó gây lỗi

- Native Java/.NET/PHP object deserialization từ cookie/request dẫn tới gadget chain RCE.
- Signed serialized token verify sai hoặc secret lộ làm attacker sửa role/user id.
- Queue consumer tin payload nội bộ nhưng attacker hoặc bug đẩy message type ngoài dự kiến.
- Cache object version cũ deserialize sai sau deploy và làm crash/replay state sai.
- Payload quá sâu/lớn làm parser cạn CPU/memory.
- Deserializer cho phép polymorphic type không giới hạn và instantiate class nguy hiểm.

## Khi nào chưa cần hoặc dễ over-engineer

- Data-only JSON với schema validation rõ có risk deserialization thấp hơn native object serialization.
- Không nên dùng native serialization cho dữ liệu qua trust boundary nếu format đơn giản đủ dùng.
- Không nên tự chế signing/serialization protocol nếu framework/protocol chuẩn đã có.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RCE]] vì insecure deserialization có thể dẫn tới remote code execution qua gadget chain.
- [[Input Validation]] vì payload serialized cần schema/type/size validation.
- [[Secret]] vì signed serialized payload phụ thuộc key/secret bảo vệ integrity.
- [[Data Transfer Object]] vì DTO/data-only schema thường an toàn hơn native object graph.
- [[Resource Exhaustion]] vì payload lớn/sâu có thể làm cạn CPU/memory parser.

## Liên quan rộng

- Application security
- Secure serialization
- Message queue safety
- Token/session design

## Keywords / Từ khóa tìm kiếm

- Insecure Deserialization
- insecure deserialization
- deserialization attack
- deserialize không an toàn
- unsafe deserialization
- object deserialization
- gadget chain
- polymorphic deserialization
- serialized payload
- tampered serialized data
- deserialization RCE
- secure serialization
- deserialization debugging

## Source trace

- OWASP Deserialization Cheat Sheet
- OWASP Top 10
