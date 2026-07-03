# AI Evaluation

Aliases: AI Evaluation, LLM evaluation, Evaluation, đánh giá AI

Type: AI / ML Engineering

## Context / Ngữ cảnh

AI Evaluation xuất hiện khi AI output cần được đo bằng test set, rubric, metric hoặc human review.

## Boundary / Ranh giới

### Nó là gì

AI Evaluation là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của AI Evaluation là golden dataset, eval metric, regression eval, judge model và error taxonomy.

## Project Role / Vai trò trong dự án

AI Evaluation giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- AI Evaluation decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới AI Evaluation
- Failure note ghi rõ AI Evaluation ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- AI Evaluation đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của AI Evaluation không?
- Khi AI Evaluation fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của AI Evaluation làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên AI Evaluation nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu AI Evaluation nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh AI Evaluation trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- AI Evaluation
- LLM evaluation
- Evaluation
- đánh giá AI
- ai evaluation debugging
- ai evaluation design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- OpenAI Evals; ML evaluation references
