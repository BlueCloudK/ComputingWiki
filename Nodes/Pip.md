# Pip

Aliases: Pip, pip

Type: Frameworks and Tools

## Context / Ngữ cảnh

Pip xuất hiện khi Python project cần cài, quản lý hoặc freeze package dependency.

## Boundary / Ranh giới

### Nó là gì

Pip là package installer cho Python, dùng để cài package từ PyPI hoặc package index khác.

### Nó không phải là gì

Pip không phải Python runtime và không tự quản lý virtual environment nếu không kết hợp với venv/conda/tool khác.

## Core Mechanism / Cơ chế lõi

Pip đọc requirement hoặc package spec, resolve/download/install package vào environment hiện tại. Environment có thể là system Python, virtualenv hoặc container.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Python dependency, virtual environment, requirements file, package version hoặc CI install.

## Output / Artifact nên có

- `requirements.txt` hoặc dependency spec
- Virtual environment note
- Install command
- Python version note
- CI cache/install note

## Decision Checklist / Câu hỏi kiểm tra

- Pip đang cài vào environment nào?
- Python version có khớp project không?
- Dependency có pin rõ không?
- CI có dùng cùng install command không?
- Package index/credential có đúng không?

## Failure Modes / Cách nó gây lỗi

- Cài nhầm system Python thay vì venv.
- Dependency version trôi làm local khác CI.
- Native wheel thiếu làm install fail.
- Package cache cũ làm debug khó.
- Requirements không phản ánh dependency thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Script Python không dependency ngoài có thể chưa cần pip workflow.
- Không nên cài package global nếu project cần reproducible environment.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Python]] vì pip là installer chính trong Python ecosystem.
- [[CI]] vì CI cần install dependency Python reproducibly.
- [[Build Cache]] vì pip cache ảnh hưởng tốc độ install.
- [[CLI Tool]] vì pip thường chạy qua command line.

## Liên quan rộng

- Python packaging
- Virtual environment
- Dependency management

## Keywords / Từ khóa tìm kiếm

- Pip
- pip
- Python package
- requirements.txt
- virtualenv
- pip install
- pip debugging

## Source trace

- pip documentation
- Python packaging documentation
