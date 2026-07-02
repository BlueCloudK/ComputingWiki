# Node Normalization Report

## Scope

Report này đọc các file trong `Maps/` để chuẩn hóa node trước khi tạo `MOC/` và `Nodes/`.

Chưa tạo MOC mới. Chưa tạo node mới. Chưa sửa map cũ.

## 1. Duplicate Nodes

Các node xuất hiện ở nhiều map hoặc lặp nhiều lần, cần chọn một canonical name.

| Node | Sources | Decision |
|---|---|---|
| Software Engineering | `SWEBOK Map`, `CC2020 Map`, `SEBoK Map` | Giữ canonical. Là MOC cấp cao. |
| Software Architecture | `SWEBOK Map`, `Software Modeling and Design Map`, `C4 Model Map` | Giữ canonical. Là MOC cấp cao. |
| Software Testing / Testing and Verification | `SWEBOK Map`, `Software Testing ISTQB Map` | Dùng Testing and Verification cho MOC; để `Software Testing` làm alias/source term. |
| Requirements / Software Requirements / Requirements Engineering | `SWEBOK Map`, `Requirements Engineering Map` | Dùng Requirements cho MOC/node đọc; giữ source terms làm aliases. |
| Security / Software Security / Application Security / Cybersecurity | `SWEBOK Map`, `OWASP Map`, `CC2020 Map` | Dùng Security cho MOC. Các tên còn lại là alias hoặc node con khi cần. |
| Reliability / System Reliability | `SEBoK Map`, `SRE Map`, `Data Intensive Applications Map` | Dùng Reliability canonical. `System Reliability` là alias/source term. |
| Monitoring | `SRE Map`, `SWEBOK Map` | Giữ canonical Monitoring. |
| Benchmark | `Computer Organization Map`, `SWEBOK Map`, `Algorithms/Performance context` | Giữ canonical Benchmark. |
| Operating System / Operating Systems | `Computer Foundations Map`, `Operating Systems Map` | Dùng singular Operating System canonical. |
| Algorithm / Algorithms | `Algorithms Map`, `Discrete Mathematics Map`, `Computer Foundations Map` | Dùng Algorithms cho MOC, Algorithm cho concept node nếu cần. |
| Graph / Graphs | `Algorithms Map`, `Discrete Mathematics Map` | Dùng singular Graph canonical. |
| Tree / Trees | `Discrete Mathematics Map` | Dùng singular Tree canonical. |
| Input Output / IO / I/O | `Computer Organization Map`, `Operating Systems Map` | Dùng Input Output canonical; `IO`, `I/O` aliases. |
| Data Model / Relational Model / Database Schema | `Database Systems Map`, `Data Intensive Applications Map` | Giữ riêng; quan hệ cha-con cần rõ khi tạo Nodes. |

## 2. Similar Nodes To Merge Or Alias

| Canonical | Merge / Alias | Reason |
|---|---|---|
| Authorization | Access Control, Permission | Cùng vùng kiểm soát quyền; `Permission` có thể là node con nếu cần. |
| Authentication | login, identity verification | Login là use case; Authentication là concept chuẩn. |
| Secret | Secrets Management, API key, token, password | `Secret` là concept; `Secrets Management` là practice/node con. |
| Input Validation | Validation khi nói về untrusted input | `Validation` rộng hơn; `Input Validation` nên nằm dưới Security/API. |
| API Contract | endpoint contract, request/response contract | Dùng một node chính cho thỏa thuận API. |
| Error Handling | Error Response, exception handling | `Error Response` là API-specific; `Error Handling` rộng hơn. |
| Logging | Security Logging, Audit Log, Error Log | `Logging` là MOC/node; các loại log là node con. |
| Monitoring | observability, dashboard, metrics | `Observability` có thể là node sau; ban đầu giữ Monitoring. |
| Incident | Incident Response, incident management | `Incident` là event; `Incident Response` là practice. |
| Deployment | release, rollout | Dùng Deployment cho node chính; release/rollout là alias hoặc node con. |
| Rollback | revert deployment, restore previous version | Dùng Rollback canonical. |
| State Machine | Finite State Machine, state-transition model | Dùng State Machine canonical; FSM alias/source term. |
| Quality Attribute | nonfunctional requirement, quality requirement | Giữ Quality Attribute; liên kết với Requirements và Architecture. |
| Transaction | database transaction, unit of work | Giữ Transaction cho DB concept; Unit of Work là pattern riêng. |
| Cache | Cache Memory, application cache, web cache | Dùng Cache rộng; các loại cache là node con. |

## 3. Broad Nodes For MOC

Các node quá rộng, nên ưu tiên làm MOC thay vì node giải thích đơn lẻ.

| MOC | Why |
|---|---|
| Computing Foundations | Root cho CS/math/OS/network/architecture. |
| Software Engineering | Root cho requirements, design, construction, testing, maintenance. |
| Requirements | Gom elicitation, analysis, specification, validation, management. |
| Software Architecture | Gom C4, architecture views, quality attributes, architecture patterns. |
| Code Design | Gom module, refactor, design pattern, state machine, error handling. |
| Data and Database | Gom ERD, schema, SQL, index, transaction, normalization. |
| API and Integration | Gom API contract, request/response, validation, webhook, integration. |
| Testing and Verification | Gom test levels, test process, test techniques, mock/assertion/test data. |
| Security | Gom auth, authz, input validation, XSS, SQLi, CSRF, secrets, API security. |
| Performance | Gom benchmark, profiling, bottleneck, cache, queue, load test. |
| Deployment and Operations | Gom deployment, logging, monitoring, SLO, incident, rollback, backup. |
| Algorithms | Có thể là MOC riêng dưới Computing Foundations. |
| Operating System | Có thể là MOC riêng dưới Computing Foundations. |
| Computer Networks | Có thể là MOC riêng dưới Computing Foundations. |

## 4. Too Small Or Defer For Later

Các node này chưa nên tạo ngay trong batch đầu, trừ khi có project cần.

| Node | Reason |
|---|---|
| Amdahl Law | Foundation/performance chi tiết; để sau. |
| Little Law | Chi tiết performance/queueing; để sau. |
| BGP | Network-specific sâu; để sau. |
| SMTP | Protocol cụ thể; để sau. |
| Protocol Buffers | Tool/format cụ thể; để Tool/Implementation later. |
| Avro | Format cụ thể; để sau. |
| PCI Express | Hardware-specific; không cần core project library ngay. |
| Magnetic Tape / storage media chi tiết | Quá thấp cho core. |
| Factory Method / từng GoF pattern | Tạo khi đã cần; ban đầu chỉ cần Design Pattern. |
| Table Data Gateway / từng PEAA pattern | Tạo khi làm backend architecture/persistence. |
| Page Controller / Front Controller | Web architecture pattern cụ thể; để sau. |
| System Landscape Diagram | C4 phụ; tạo sau nếu cần architecture docs. |
| K Nearest Neighbors | Không thuộc core software project library ban đầu. |

## 5. Source Trace Issues

| Issue | Example | Fix |
|---|---|---|
| Abbreviation chưa rõ | `RE guide Ch04 / SR Ch06-Ch08` | Trong final node, đổi thành `Requirements Engineering - A Good Practice Guide Ch04 / Software Requirements 3rd Ed Ch06-Ch08`. |
| `source: contents` quá chung | `Computer Foundations Map`, `Computer Organization Map` | Chấp nhận ở map; khi tạo node quan trọng thì lấy chapter cụ thể nếu cần. |
| `source: later chapters` chưa đủ rõ | `Computer Organization Map` | Không dùng các node này trong batch đầu hoặc bổ sung trace trước khi tạo node. |
| Link-only source | OWASP, SRE, Fowler, Refactoring.Guru, C4 | Giữ source URL trong node nếu tạo; không ghi là local PDF. |
| Source term khác canonical | `Software Testing` vs `Testing and Verification` | Node canonical dùng tên chuẩn; aliases ghi source terms. |

## 6. Proposed Canonical MOC List

Batch đầu nên tạo/giữ các MOC này:

| Canonical MOC | Aliases | Source basis |
|---|---|---|
| Computing Foundations | computer science foundations | CC2020, Computer Foundations, Discrete Math |
| Software Engineering | software engineering body of knowledge | SWEBOK, CC2020 |
| Requirements | software requirements, requirements engineering | SWEBOK, Requirements Engineering, Software Requirements |
| Software Architecture | architecture, architectural design | SWEBOK, Gomaa, C4 |
| Code Design | software design, detailed design | SWEBOK, Gomaa, Refactoring.Guru |
| Data and Database | database systems, data systems | Database System Concepts, DDIA |
| API and Integration | API, integration | DDIA, Requirements/Architecture maps |
| Testing and Verification | software testing, testing | SWEBOK, ISTQB |
| Security | application security, software security, cybersecurity | OWASP, SWEBOK, CC2020 |
| Performance | scalability/performance | DDIA, Computer Organization, SRE |
| Deployment and Operations | operations, SRE, production | SWEBOK, SRE |

## 7. Proposed Canonical Node List

Batch đầu nên ưu tiên các node có ích cho project thực tế và xuất hiện trong nhiều nguồn.

| Canonical Node | Parent MOC | Type | Aliases / Merge |
|---|---|---|---|
| Requirement | Requirements | concept | requirement statement |
| Functional Requirement | Requirements | concept | function requirement |
| Nonfunctional Requirement | Requirements | concept | quality requirement |
| Use Case | Requirements | artifact | use case model |
| User Story | Requirements | artifact | agile story |
| Acceptance Criteria | Requirements | artifact | acceptance condition |
| Stakeholder | Requirements | concept | actor/customer/user representative |
| Scope | Requirements | concept/artifact | project boundary |
| Traceability | Requirements | practice | requirement trace |
| Change Control | Requirements | practice | change management |
| Quality Attribute | Software Architecture | quality | nonfunctional requirement |
| C4 Model | Software Architecture | model | C4 architecture model |
| System Context Diagram | Software Architecture | artifact | C4 level 1 |
| Container Diagram | Software Architecture | artifact | C4 level 2 |
| Component Diagram | Software Architecture | artifact | C4 level 3 |
| State Machine | Code Design | model | finite state machine |
| Design Pattern | Code Design | area | GoF pattern |
| Refactor | Code Design | practice | restructuring code |
| Error Handling | Code Design | practice | exception/error response handling |
| ERD | Data and Database | artifact | entity relationship diagram |
| Database Schema | Data and Database | artifact | schema |
| SQL | Data and Database | language/topic | query language |
| Index | Data and Database | artifact/concept | database index |
| Transaction | Data and Database | concept | database transaction |
| Normalization | Data and Database | practice | relational normalization |
| API Contract | API and Integration | artifact | request/response contract |
| Request | API and Integration | concept | API request |
| Response | API and Integration | concept | API response |
| Validation | API and Integration | practice | data/rule checking |
| Unit Test | Testing and Verification | practice | component/unit test |
| Integration Test | Testing and Verification | practice | integration testing |
| E2E Test | Testing and Verification | practice | end-to-end testing |
| Regression Test | Testing and Verification | practice | prevent old bug return |
| Assertion | Testing and Verification | concept | test assertion |
| Mock | Testing and Verification | test double | mock object/function/service |
| Test Coverage | Testing and Verification | metric | coverage |
| Authentication | Security | practice/concept | identity verification |
| Authorization | Security | practice/concept | access control, permission |
| Secret | Security | asset/concept | API key/token/password |
| Input Validation | Security | practice | validate untrusted input |
| XSS | Security | vulnerability | cross-site scripting |
| SQL Injection | Security | vulnerability | SQLi |
| CSRF | Security | vulnerability | cross-site request forgery |
| Benchmark | Performance | practice/artifact | performance measurement |
| Profiling | Performance | practice | locate bottleneck |
| Bottleneck | Performance | concept | limiting part |
| Cache | Performance | concept/practice | caching |
| Queue | Performance | architecture/concept | async queue |
| Load Test | Performance | practice | test under load |
| Deployment | Deployment and Operations | practice | release to environment |
| Environment Variable | Deployment and Operations | config | env var |
| Logging | Deployment and Operations | practice | logs |
| Monitoring | Deployment and Operations | practice | metrics/dashboard/alerts |
| SLO | Deployment and Operations | artifact/concept | service level objective |
| Incident | Deployment and Operations | event | production issue |
| Rollback | Deployment and Operations | practice | revert to previous version |
| Backup | Deployment and Operations | artifact/practice | data backup |

## 8. Recommended Next Step

Next step should be:

1. Create `MOC/` folder.
2. Move broad existing MOC-like node files from `Nodes/` to `MOC/`.
3. Generate only the canonical MOC files first.
4. Generate/normalize batch-one Nodes from the canonical node list.
5. Add aliases in English + Vietnamese.
6. Keep source trace short and English.

Do not generate every map node in one pass.

