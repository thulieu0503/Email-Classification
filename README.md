1. Giới thiệu đề tài
1.1 Bài toán
Trong thực tế, email rác (spam) xuất hiện ngày càng nhiều, gây phiền toái cho người dùng và tiềm ẩn nguy cơ lừa đảo, mã độc. Việc tự động phân loại email spam và email thường (ham) là một bài toán quan trọng trong lĩnh vực Xử lý ngôn ngữ tự nhiên (NLP) và Machine Learning.

Bài toán đặt ra:
Cho nội dung một email, hãy xác định email đó là Spam hay Ham.

1.2 Mục tiêu
Xây dựng pipeline Machine Learning cho bài toán phân loại email
Áp dụng các kỹ thuật tiền xử lý văn bản
So sánh hiệu quả của các mô hình học máy phổ biến
Triển khai demo dự đoán email spam/ham

2. Dataset
2.1 Nguồn dữ liệu
Dataset: SMS Spam Collection Dataset
Nguồn: https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset

2.2 Mô tả dữ liệu
Dataset gồm 5.574 mẫu, mỗi mẫu là một tin nhắn/email.

Tên cột	Mô tả
label	Nhãn của email (spam hoặc ham)
text	Nội dung email

Ví dụ:
label = spam → email rác
label = ham → email bình thường

3. Pipeline hệ thống
Pipeline tổng thể của hệ thống gồm các bước sau:

3.1 Tiền xử lý dữ liệu
Chuyển văn bản về chữ thường
Loại bỏ ký tự đặc biệt, số
Tokenization (tách từ)
Loại bỏ stopwords
Lemmatization

Vector hóa văn bản bằng:
Bag of Words (BoW)
TF-IDF

3.2 Huấn luyện mô hình
Chia tập dữ liệu:
Train set: 85%
Test set: 15%

Huấn luyện các mô hình học máy
3.3 Đánh giá mô hình
Đánh giá trên tập test bằng các chỉ số:
Accuracy
Precision
Recall
F1-score
Confusion Matrix

3.4 Inference (Dự đoán)
Nhập nội dung email mới
Tiền xử lý + vector hóa
Dự đoán email là Spam hay Ham
Hiển thị xác suất dự đoán

4. Mô hình sử dụng
4.1 Naive Bayes
Phù hợp với dữ liệu văn bản
Huấn luyện nhanh
Hoạt động tốt với BoW và TF-IDF

4.2 Logistic Regression
Mô hình tuyến tính, dễ giải thích
Hiệu quả cao với dữ liệu chiều cao
Cho phép dự đoán xác suất

4.3 Lý do chọn
Các mô hình trên:
Đơn giản
Phù hợp cho bài toán phân loại nhị phân
Thường cho kết quả tốt với dữ liệu văn bản

5. Kết quả thực nghiệm
5.1 Đánh giá mô hình

Ví dụ kết quả:
Mô hình	               Vector hóa	Accuracy
Naive Bayes	              BoW	     96.25
Naive Bayes	            TF-IDF	     96.64
Logistic Regression	      BoW	     93.28
Logistic Regression	    TF-IDF	     97.80
5.2 Confusion Matrix (mô hình tốt nhất)
	           Dự đoán Ham	 Dự đoán Spam
Thực tế Ham	      TN          	FP
Thực tế Spam	  FN	            TP

Mô hình Logistic Regression với TF-IDF cho kết quả tốt nhất, tỷ lệ dự đoán sai thấp.

6. Hướng dẫn chạy chương trình
6.1 Cài môi trường
Cài các thư viện cần thiết:
pip install numpy pandas scikit-learn nltk streamlit joblib

6.2 Chạy train model
python train.py
Sau khi train xong, model sẽ được lưu vào thư mục model/.

6.3 Chạy demo / inference
streamlit run app.py
Thưc hiện:
+ Nhập nội dung email
+ Chọn mô hình
Xem kết quả dự đoán và xác suất spam/ham

7. Cấu trúc thư mục dự án
email-spam-classification/
│
├── data/
│   └── spam.csv
│
├── model/
│   ├── naive_bayes_bow.pkl
│   ├── naive_bayes_tfidf.pkl
│   ├── logistic_regression_tfidf.pkl
│   ├── logistic_regression_bow.pkl
│
├── train.py
├── app.py
├── preprocessing.py
├── requirements.txt
└── README.md

Họ và tên: Đỗ Thu Liễu
Mã SV: 12423048
Lớp: 12423TN
