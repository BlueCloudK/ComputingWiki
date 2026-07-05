# CLI Tool

Aliases: CLI Tool, command-line tool, cli tool

Type: Frameworks and Tools

## Context / Ngữ cảnh

CLI Tool xuất hiện khi developer, CI, operator hoặc automation cần điều khiển hệ thống qua terminal/script. Nó thường dùng cho build, test, deploy, migration, scaffold, cloud ops, database admin, codegen hoặc internal developer tooling.

## Boundary / Ranh giới

### Nó là gì

CLI Tool là chương trình chạy qua command line, nhận argument/flag/stdin/env/config, thực hiện action và trả output qua stdout/stderr/exit code/file/artifact. CLI tốt phải scriptable, deterministic, có help rõ, exit code đúng và output đủ cho người/máy đọc.

### Nó không phải là gì

CLI Tool không chỉ là wrapper chạy được một lệnh. Nếu option không rõ, exit code sai, output khó parse, secret bị log hoặc behavior phụ thuộc state ẩn, CLI sẽ khó dùng trong CI/automation. CLI cũng không thay thế API nếu cần integration lâu dài và typed contract ổn định.

## Core Mechanism / Cơ chế lõi

User hoặc script gọi command với subcommand/flag. CLI parse input, validate config/env, thực hiện operation, log progress vào stderr nếu cần, output kết quả chính vào stdout, rồi exit 0/khác 0 theo thành công/thất bại. CLI dùng trong CI cần non-interactive mode và error message rõ.

## Project Role / Vai trò trong dự án

CLI Tool là node cần mở khi thiết kế developer workflow, deploy script, migration runner, benchmark command hoặc internal automation. Nó giúp team chuẩn hóa input/output, idempotency, logging, exit code, config và secret handling.

## Output / Artifact nên có

- Command spec: subcommand, args, flags, env vars, config file
- Help/usage examples và common workflows
- Exit code contract và error message pattern
- Output contract: human-readable, JSON, file artifact hoặc quiet mode
- Security note: secret redaction, confirmation for destructive action, dry-run
- Test case cho missing arg, invalid config, failure path và non-interactive CI

## Decision Checklist / Câu hỏi kiểm tra

- CLI dùng cho người, script hay cả hai?
- Input đến từ args, env, config hay stdin?
- Output chính có cần parse bằng máy không?
- Exit code có phản ánh thành công/thất bại rõ không?
- Command có idempotent hoặc dry-run không?
- Secret/token có bị in ra log/stdout không?
- Destructive action có confirmation hoặc explicit flag không?

## Failure Modes / Cách nó gây lỗi

- Exit code luôn 0 khiến CI tưởng thành công dù command fail.
- Output lẫn log/progress làm script parse sai.
- CLI yêu cầu interactive prompt trong CI và treo pipeline.
- Error message thiếu context nên debug config/env khó.
- In secret/token ra terminal hoặc CI log.
- Destructive command thiếu dry-run/confirmation làm xóa nhầm data.
- Behavior phụ thuộc working directory hoặc hidden global config không document.

## Khi nào chưa cần hoặc dễ over-engineer

- Một lệnh nội bộ dùng một lần có thể là script đơn giản.
- Không nên xây CLI framework lớn nếu chỉ có vài command ổn định.
- Không nên dùng CLI thay API cho integration nhiều consumer cần contract/versioning dài hạn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì CLI thường chạy trong pipeline và cần exit code/log đúng.
- [[Environment Variable]] vì CLI thường nhận config/secret qua env var.
- [[Secret]] vì CLI dễ vô tình in hoặc đọc token nhạy cảm.
- [[Deployment]] vì deploy/migration thường được điều khiển qua CLI.
- [[GitHub Actions]] vì Actions job thường gọi CLI trong step.

## Liên quan rộng

- Developer tooling
- Automation
- Operations workflow
- Scripting

## Keywords / Từ khóa tìm kiếm

- CLI Tool
- command-line tool
- cli tool
- command line interface
- subcommand
- command flags
- exit code
- stdout stderr
- non interactive CLI
- dry run
- CLI automation
- CLI debugging

## Source trace

- POSIX command-line conventions
- Git documentation
- GitHub Actions documentation
