# Training

Aliases: model training, huấn luyện mô hình

Type: AI / ML Engineering

## Context / Ngữ cảnh

Training xuất hiện khi model cần học pattern từ dataset bằng cách tối ưu tham số theo loss function. Nó là giai đoạn tạo hoặc điều chỉnh model trước khi đưa vào inference, evaluation hoặc deployment. Trong thực tế, training có thể là pretraining, fine-tuning, supervised learning, reinforcement learning hoặc training một model nhỏ cho task cụ thể.

## Boundary / Ranh giới

### Nó là gì

Training là quá trình đưa dữ liệu qua model, tính loss, lan truyền gradient, cập nhật tham số bằng optimizer và lặp lại qua batch/epoch cho tới khi đạt mục tiêu. Training cần dataset, split, model architecture, loss, optimizer, hyperparameter, compute, checkpoint và evaluation loop.

### Nó không phải là gì

Training không phải inference. Inference dùng model đã có để tạo output cho input mới; training thay đổi tham số model. Training cũng không tự đảm bảo model hữu ích nếu dataset sai, label nhiễu, metric lệch, data leakage hoặc overfitting không được kiểm soát.

## Core Mechanism / Cơ chế lõi

Pipeline training thường gồm chuẩn bị dataset, chia train/validation/test, chạy forward pass, tính loss, backward pass, optimizer update, log metric, validate định kỳ và lưu checkpoint. Chất lượng phụ thuộc vào data quality, learning rate, batch size, regularization, model capacity, compute stability và cách chọn checkpoint cuối.

## Project Role / Vai trò trong dự án

Training là node cần mở khi team tự train/fine-tune model, debug model không học, overfit, underfit, metric production lệch eval hoặc chi phí compute tăng bất thường. Nó giúp phân biệt lỗi nằm ở data, objective/loss, hyperparameter, architecture, training code hay evaluation.

## Output / Artifact nên có

- Training config: dataset version, model, loss, optimizer, learning rate, batch size, epoch, seed
- Data split và data leakage check
- Training log: train/validation loss, metric, learning curve, resource usage
- Checkpoint/version artifact và model card hoặc release note
- Eval report trước khi đưa model sang inference/deployment
- Reproducibility note: code commit, config, environment, random seed, hardware

## Decision Checklist / Câu hỏi kiểm tra

- Dataset và label có phù hợp target task không?
- Train/validation/test split có leak dữ liệu không?
- Metric validation có phản ánh behavior production cần không?
- Learning curve cho thấy overfitting, underfitting hay training instability không?
- Hyperparameter và seed có được lưu để reproduce không?
- Checkpoint được chọn theo metric nào?
- Sau training có eval/safety test trước khi deploy inference không?

## Failure Modes / Cách nó gây lỗi

- Data leakage làm validation score cao giả nhưng production fail.
- Overfitting làm model nhớ train set và generalize kém.
- Underfitting làm model không học đủ pattern dù train lâu.
- Label noise hoặc schema sai làm model học target sai.
- Learning rate quá cao/thấp làm training diverge hoặc học rất chậm.
- Không version dataset/config/checkpoint làm kết quả không reproduce được.
- Chọn checkpoint theo metric lệch làm model tốt trên score nhưng xấu với user thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Nhiều AI product không cần tự training; prompt/RAG/tooling/eval có thể đủ cho MVP.
- Không nên fine-tune khi lỗi thật nằm ở retrieval, prompt, data quality hoặc product flow.
- Không nên chạy training lớn trước khi có eval dataset và metric rõ để biết model tốt hơn thật không.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dataset]] vì training phụ thuộc trực tiếp vào dữ liệu và label.
- [[AI Evaluation]] vì model sau training cần eval để chọn checkpoint và bắt regression.
- [[Inference]] vì model trained được dùng ở runtime inference.
- [[Overfitting]] vì overfitting là failure mode cốt lõi của training.
- [[Model Versioning]] vì checkpoint/config/dataset cần version để reproduce và rollback.

## Liên quan rộng

- Machine learning lifecycle
- Fine-tuning
- MLOps
- Experiment tracking

## Keywords / Từ khóa tìm kiếm

- Training
- model training
- huấn luyện mô hình
- training loop
- loss function
- optimizer
- epoch
- batch size
- learning rate
- validation loss
- checkpoint
- overfitting
- underfitting
- data leakage
- model training debugging

## Source trace

- Deep Learning Book
- PyTorch documentation
- Google Machine Learning Crash Course
