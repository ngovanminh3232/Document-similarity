# Document-similarity
## Tổng quan dự án
Dự án Document similarity nhằm thực hiện mục đích là so sánh các văn bản tiếng Việt và đưa ra độ tương đồng dựa trên cosine similarity.

Báo cáo: [here](https://colab.research.google.com/drive/19j3lZHpnklFQBIEcSYCdkPbvJ5s1mdai?usp=sharing)  
Slide: [here](https://www.overleaf.com/read/dvbgvdhgfdcf)

## Ứng dụng của dự án
- So sánh các văn bản đưa ra gợi ý.
- So sánh các các bài báo giống nhau đưa ra gợi ý cho người dùng.

## Kết quả
 

### 1. Giải thuật Jaccard  
Top 5 bài báo liên quan  
1. : https://thanhnien.vn/shark-binh-ban-trai-dien-vien-phuong-oanh-len-tieng-ve-thong-tin-chua-ly-hon-vo-post1492270.html  
Độ tương đồng: 32.76%
2. : https://thanhnien.vn/vu-khoi-to-chong-lay-tien-vo-tien-chung-vo-chong-lay-xai-co-phai-xin-phep-post1465717.html  
Độ tương đồng:  16.15%
3. https://thanhnien.vn/vo-kien-co-giao-chu-nhiem-quan-he-bat-chinh-sinh-con-voi-chong-minh-post1434941.html  
Độ tương đồng: 12.44%
4. https://thanhnien.vn/ngay-xoa-bo-bao-luc-doi-voi-phu-nu-rat-it-nguoi-nho-phap-luat-can-thiep-post1525144.html  
Độ tương đồng: 11.66%
5. https://thanhnien.vn/su-that-la-don-ly-hon-vi-vo-khong-cho-dap-chan-cua-cu-ong-u-90-post1432001.html  
Độ tương đồng: 9.6%

Nhận xét: 
- Độ tương đồng quá thấp và chưa sát ngữ nghĩa bài báo kết quả do đây là phương pháp sử dụng so sánh các từ chưa được training để hiểu ngữ nghĩa các câu.
- Có rất nhiều bài báo có độ tương đồng bằng 0 mặc dù văn bản có liên quan tới nhau.

### 2. TF-IDF

Top 5 bài báo liên quan: 
1. https://thanhnien.vn/shark-binh-ban-trai-dien-vien-phuong-oanh-len-tieng-ve-thong-tin-chua-ly-hon-vo-post1492270.html  
Độ tương đồng: 61.16%
2. https://thanhnien.vn/chong-lay-tien-vo-dem-di-bi-khoi-to-tien-nop-cho-vo-giu-lay-xai-phai-xin-phep-post1465717.html  
Độ tương đồng: 46.89%  
3. https://thanhnien.vn/mua-ban-xe-may-cu-phai-co-xac-nhan-doc-than-nguoi-dan-than-bi-hanh-post1018484.html  
Độ tương đồng: 39.98%
4. https://thanhnien.vn/su-that-la-don-ly-hon-vi-vo-khong-cho-dap-chan-cua-cu-ong-u-90-post1432001.html   
Độ tương đồng: 39.75%
5. https://thanhnien.vn/vo-to-co-giao-chu-nhiem-quan-he-bat-chinh-sinh-con-voi-chong-minh-post1434941.html  
Độ tương đồng: 37.49%

Nhận xét:
- TF-IDF là một phương pháp toán học thông thường vẫn chưa được training hiểu được ngữ nghĩa nên độ tương đồng chưa cao là điều dễ hiểu.
- Độ tương đồng chưa cao và văn bản top 3 hoàn toàn không tương đồng với văn bản gốc.

#### 3. Word2Vec
Top 5 bài báo liên quan  
1. https://thanhnien.vn/shark-binh-ban-trai-dien-vien-phuong-oanh-len-tieng-ve-thong-tin-chua-ly-hon-vo-post1492270.html  
Đọ tương đồng: 97.76%  
2. https://thanhnien.vn/me-don-than-viet-cap-ben-hanh-phuc-cung-nguoi-chong-anh-hon-19-tuoi-post1427521.html  
Độ tương đồng: 96.79%
3. https://thanhnien.vn/nsnd-kim-xuan-cuoc-doi-toi-cung-co-nhung-luc-khoc-khong-ra-tieng-post1525997.html  
Độ tương đồng: 966.61%
4. https://thanhnien.vn/nguoi-phu-nu-viet-lo-mot-lan-do-lay-chong-tay-u-70-anh-nhu-chang-trai-16-post1452479.html  
Độ tương đồng: 96.559495%
5. https://thanhnien.vn/elly-tran-toi-ngu-ngoc-khi-chon-hon-nhan-post1522250.html  
Độ tương đồng: 96.55187%

Nhận xét:

- Độ tương đồng rất cao tuy nhiên không tương ứng với ngữ nghĩa của văn bản sai lệch rất nhiều.
- Model Tiếng Việt được phát hành từ FastText còn lỗi nhiều cần cải thiện thêm hoặc dùng model khác.
- Bài báo top 3 không liên quan nhiều và chưa gợi ý được cho người xem.

### 4. BERT (pho-BERT)

Top 5 bài báo liên quan

1. https://thanhnien.vn/shark-binh-ban-trai-dien-vien-phuong-oanh-len-tieng-ve-thong-tin-chua-ly-hon-vo-post1492270.html  
Độ tương đồng: 78.72037%
2. https://thanhnien.vn/mua-ban-xe-may-cu-phai-co-xac-nhan-doc-than-nguoi-dan-than-bi-hanh-post1018484.html  
Độ tương đồng: 74.27565%
3. https://thanhnien.vn/yeu-khong-thanh-quay-mot-vong-me-don-than-viet-van-nen-duyen-cung-chong-an-do-post1518833.html  
Độ tương đồng: 71.51493%
4. https://thanhnien.vn/elly-tran-toi-ngu-ngoc-khi-chon-hon-nhan-post1522250.html  
Độ tương đồng: 71.49129%
5. https://thanhnien.vn/nguoi-phu-nu-viet-lo-mot-lan-do-lay-chong-tay-u-70-anh-nhu-chang-trai-16-post1452479.html  
Độ tương đồng: 70.77005%

Nhận xét:
- Độ tương đồng phù hợp với nội dung bài báo gốc được so sánh
- Model pho-BERT được xử lý tốt để hiểu được nội dung bài báo gốc đồng đồng thời sinh ra các ma trận đủ tốt để ta so sánh.

## Liên hệ
<b> Tác giả: Ngô Minh </b>  
Email:  <ngovanminh3232@gmail.com>

## Nguồn tham khảo:

[Pho-Bert](https://github.com/VinAIResearch/PhoBERT)  
[Transformer ](https://arxiv.org/abs/1706.03762v5)  
[Document simlarity](https://medium.com/analytics-vidhya/best-nlp-algorithms-to-get-document-similarity-a5559244b23b)  
[TF-IDF](https://viblo.asia/p/tf-idf-term-frequency-inverse-document-frequency-JQVkVZgKkyd)  
[Giải thuật Jaccard](https://viblo.asia/p/giai-thuat-jaccard-djeZ1P9GKWz)