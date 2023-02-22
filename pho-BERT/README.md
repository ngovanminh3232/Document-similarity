### 3.3 Mô hình BERT

-	BERT viết tắt bởi Bidirectional Encoder Decoder From Transformer có nghĩa là mô hình biểu diễn từ theo 2 chiều ứng dụng kỹ thuật Transformer. 
-	BERT được thiết kế để huấn luyện trước các từ biểu diễn (pre-train word embedding)
-	Điểm đặc biệt là BERT có thể điều hòa cân bằng bối cảnh theo cả hai chiều phải và trái.

Ứng dụng:  
-	Tìm các từ đồng nghĩa, trái nghĩa, cùng nhóm dựa trên khoảng cách không gian đa chiều  
-	Xây dựng các vector embeddings cho các tác vụ NLP: sentimet analyst, phân loại văn bản, huấn luyện chatbot.   
-	Gợi ý các từ khóa trong hệ thống search.  
-	Xây dựng các ứng dụng seq2seq như robot viết báo, tóm tắt văn bản, sinh câu ngẫu nhiên với ý tương tự.  

Biểu diễn không ngữ cảnh (non-context)
-	Mô hình như Word2Vec, fastext…
-	Ví dụ như mô hình Word2Vec được đào tạo để tìm hiểu các embeddings dự đoán xác suất của một từ trung tâm (Skip-gram) và ngược lại (CBOW). Các từ xung quanh còn được gọi là các từ ngữ cảnh vì chúng xuất hiện quanh từ trung tâm.
-	Ví dụ câu sau: Em đồng ý tăng tiền tiêu vặt lên 500 nghìn đồng.
Đồng (1) và đồng (2) khác nhau về nghĩa.

Biểu diễn ngữ cảnh một chiều (uni- directional)
-	Là các mô hình xuất hiện biểu diễn ngữ cảnh. Các vector kết quả được biểu diễn thông qua các từ liền trước nó.
-	Ví dụ như các mô hình LSTM
-	Ví dụ câu sau : Hôm nay tôi mang 200 tỷ gửi ngân hàng
Từ gửi ở trên được biểu diễn thông qua các từ liền trước nó.

Biểu diễn ngữ cảnh hai chiều (bi-directional)
-	Là các mô hình mà một từ không chỉ biểu diễn một từ liền trước nó mà nó còn được biểu diễn bởi các từ xung quanh nó.
-	Ví dụ như mô hình sử dụng Transformer: BERT, OpenAI GPT,...

1.	Quá trình Fine Turning trong BERT  
Một điểm đặc biệt ở BERT mà các model embedding trước đây chưa từng có đó là kết quả huấn luyện có thể fine-tuning được. Chúng ta sẽ thêm vào kiến trúc model một output layer để tùy biến theo tác vụ huấn luyện.  

![BERT](../data/bert.png#center  "BERT")

Hình ảnh: Toàn bộ tiến trình pre-training và fine-tuning của BERT. Một kiến trúc tương tự được sử dụng cho cả pretrain-model và fine-tuning model. Chúng ta sử dụng cùng một tham số pretrain để khởi tạo mô hình cho các tác vụ down stream khác nhau. Trong suốt quá trình fine-tuning thì toàn bộ các tham số của layers học chuyển giao sẽ được fine-tune. Đối với các tác vụ sử dụng input là một cặp sequence (pair-sequence) ví dụ như question and answering thì ta sẽ thêm token khởi tạo là [CLS] ở đầu câu, token [SEP] ở giữa để ngăn cách 2 câu.  

Masked ML (MLM) Masked ML là một tác vụ cho phép chúng ta fine-tuning lại trên các bộ dữ liệu unsupervised-text bất kỳ. Chúng ta có thể áp dụng Masked ML cho nhiều ngôn ngữ khác nhau để tạo ra các embedding cho chúng. Các dữ liệu của tiếng Anh có kích thước lên tới vài trăm tới vài nghìn GB đều được biểu thị tốt bởi BERT.

![BERT](../data/bert2.png#center  "BERT")
<b>Hình ảnh:</b> Sơ đồ kiến trúc BERT cho các tác vụ Masked ML.

Theo đó:
- Khoảng 15 % các token của câu input được thay thế bởi [MASK] token trước khi truyền vào model đại diện cho những từ bị che dấu (masked). Mô hình sẽ dựa trên các từ không được che (non-masked) dấu xung quanh [MASK] và đồng thời là bối cảnh của [MASK] để dự báo giá trị gốc của từ được che dấu. Số lượng từ được che dấu được lựa chọn là một số ít (15%) để tỷ lệ bối cảnh chiếm nhiều hơn (85%).

- Để tính toán phân phối xác suất cho từ output, chúng ta thêm một Fully connect layer ngay sau Transformer Encoder. Hàm softmax có tác dụng tính toán phân phối xác suất. Số lượng units của fully connected layer phải bằng với kích thước của từ điển.  

- Cuối cùng ta thu được véc tơ nhúng của mỗi một từ tại vị trí MASK sẽ là embedding véc tơ giảm chiều của véc tơ Oi sau khi đi qua fully connected layer như mô tả trên hình vẽ bên phải. 

Code Colab: https://colab.research.google.com/drive/1_7iHE2PtWFsovh1TlvizfgyJGLMsBkxv?usp=sharing