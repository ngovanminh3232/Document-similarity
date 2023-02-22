### Giải thuật Jaccard
Độ tương tự các văn bản được giải thuật Jaccard tính toán như sau: 

<i>Kích thước phần giao điểm chia cho hợp của hai tập hợp.</i>  

![Jaccard](../data/jaccard1.png#center "Jaccard")


Ví dụ như sau:  
Câu 1: AI is our friend and it has been friendly.  
Câu 2: AI and humans have always been friendly.


Để tính toán một cách dễ dàng và chính xác hơn chúng ta sẽ chuẩn hóa các từ về dạng gốc.
Trong trường hợp này là ‘friend’ và ‘friendly’ thành ‘friend’, ‘has’ và ‘have’ sẽ trở thành ‘has’.

![Jaccard](../data/jaccard2.png#center "Jaccard2")

Đối với hai câu trên, chúng tôi nhận được độ tương tự Jaccard trả lại là
5/(5+3+2) = 0.5 là kích thước của giao điểm của các tập hợp chia cho tổng kích thước của tập hợp.  
Ví dụ khác  
Câu 1: President greets the press in Chicago.  
Câu 2: Obama speaks in Illinois.  

![Jaccard](../data/jaccard3.png#center "Jaccard3")

Trong trường hợp này giải thuật Jaccard tỏ ra không hiệu quả và trả về độ tương đồng là 0. Đây là một con số khó chấp nhận được mặc dù hai câu trên là tương tự về mặt ngữ nghĩa.Ở đây cho thấy giải thuật Jaccard không thể nắm bắt ngữ nghĩa của các câu của các từ vựng ở trong câu mà chỉ đơn thuần tính số lần xuất hiện của các từ.

<b>Đây là một lỗ hổng rất lớn và cố hữu khi dữ liệu của chúng ta tăng lên, một số các từ thông dụng sẽ xuất hiện nhiều lên mặc dù chủ đề của chúng là khác nhau.</b>
