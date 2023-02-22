Nếu như chúng ta làm tiếp tục đánh giá các từ trong câu có độ quan trọng ngang bằng nhau(như ở trên) thì chúng ta có xu hướng đặt quá nhiều trọng số vào một từ hoàn toàn không mang nhiều ngữ nghĩa.TF-IDF sẽ giải quyết vấn đề bằng 2 cách sau đây:  

1.	TF(Tần số): dùng để tính tần số xuất hiện trong một văn bản. Tuy nhiên do độ dài các văn bản là khác nhau nên ta phải tính toán tần số xuất hiện chia cho độ dài của văn bản đó.  
> TF(t, d) = ( số lần từ t xuất hiện trong văn bản d) / (tổng số từ trong văn bản d)

2.	IDF(Trọng số): dùng để đánh giá trọng số của từng từ như thế nào. Khi tính TF thì các từ đều được coi trọng như nhau. Tuy nhiên có một số từ thông dụng được dùng sử dụng nhiều nhưng không quan trọng trong đoạn văn, ví dụ:  
a.	Từ nối: và , nhưng, xuất hiện, vì thế….  
b.	Giới từ: ở, trong, trên…  
c.	Từ chỉ định: ấy, đó, nhỉ…  
Vì vậy cần giảm mức độ quan trọng của những từ bằng cách sử dụng IDF.  
> IDF(t, D) = log_e( Tổng số văn bản trong tập mẫu D/ Số văn bản có chứa từ t )  

Từ phần giải thích về TF, IDF ta có công thức hoàn chỉnh về TF-IDF:
> TF-IDF = TF(t, d) x IDF(t, D)

