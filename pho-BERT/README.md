### Word2Vec
Về tổng quan Word2Vec xây dựng một không gian có số chiều thấp hơn số từ trong từ điển biểu diễn các từ trong từ thông qua từ điển.   
Ý tưởng:  
•	Hai từ gần nhau thường có ý nghĩa gần nhau  
•	Dự đoán được một từ nếu biết các từ xung quanh nó  
Ví dụ: Hà Nội là _ của Việt Nam  
Word2Vec sẽ dự đoán được _ là thủ đô  

![Word2vec](../data/word2vec1.png#center  "Word2vec")

<i>Quá trình training Word2Vec</i>

Với mỗi từ đích trong câu cơ sở, các từ ngữ cảnh sẽ được định nghĩa các từ ngữ cảnh được định nghĩa là các từ xung quanh các từ đích không quá một khoảng là c/2 (c là độ dài câu). Hay nói đơn giản là một từ sẽ có ngữ nghĩa dựa vào các từ xung quanh nó.

Hai mô hình xây dựng lên Word2Vec

1. Mô hình Skip gram (dự đoán ngữ cảnh nếu biết từ đích)
2. Mô hình CBOW (dự đoán từ đích biết ngữ cảnh)

I. Mô hình Skip gram 

Mọi tính toán trong mục này được xây dựng xung quanh một từ ngữ cảnh.
Hàm mất mát tổng sẽ là tổng của các hàm mất mát tại các ngữ cảnh đó.
Việc tối ưu hàm mất mát thông qua Gradient Descent sẽ thực hiện trên từng từ ngữ cảnh.

![Word2vec](../data/word2vec2.png#center  "Word2vec")

VD: Target word: Brown
_ _ brown _ _ -> The quick brown fox jump.
Skip gram sẽ sử dụng xác suất và Gradient Descent để tối các hàm mất mát nhằm cho ra kết quả tốt nhất.

II. Mô hình CBOW

Mọi tính toán trong mục này nhằm tìm ra xác suất xảy ra một từ khi biết ngữ cảnh xung quanh từ đó. Và vì có nhiều từ ngữ cảnh trong các điều kiện nên ta thường đơn giản lấy một ‘trung bình’ làm đại diện.

![Word2vec](../data/word2vec3.png#center  "Word2vec")

VD: The quick _ fox jump -> The quick brown fox jump.

<b>So sánh</b>

|                                  CBOW                                 |                  Skip-gram                  |
|:---------------------------------------------------------------------:|:-------------------------------------------:|
| Phù hợp với dữ liệu lớn, biểu diễn tốt các từ xuất hiện thường xuyên. | Độ chính xác chưa cao so với độ tương đồng  |
| Số từ dự đoán là 1 ít hơn skip gram                                   |                                             |

<b>Tổng kết</b>

Từ hai mô hình CBOW và Skip-gram ta sẽ xây dựng ra được một mạng neural-network đại diện cho các từ.
![Word2vec](../data/word2vec4.png#center  "Word2vec")