## 🕵️‍♂️ Challenge:
Username: natas3  
Password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH  
URL: http://natas3.natas.labs.overthewire.org  

<img width="1403" height="501" alt="image" src="https://github.com/user-attachments/assets/95918002-3bdc-4093-a6f8-7f2c5a707f73" />


## 📝 Solution: 
Kiểm tra nguồn trang, ta thấy dòng gợi ý: ngay cả Google cũng không tìm thấy.  

<img width="1392" height="494" alt="image" src="https://github.com/user-attachments/assets/79d0cd1e-0f3b-49f6-be1e-80401a06c995" />

Rất có thể có thứ gì đó đã ngăn chặn các công cụ tìm kiếm như Google tìm được.  
Và nhắc tới điều đó thì chúng ta nghĩ tới file `robots.txt`, thử kiểm tra:  

<img width="839" height="204" alt="image" src="https://github.com/user-attachments/assets/a9655062-65c9-4dd7-b64e-0e4f9768da5e" />

Như vậy có đường dẫn đến `/s3cr3t/` ko được cho phép.  
Truy cập vào `.../s3cr3t/`:  

<img width="831" height="430" alt="image" src="https://github.com/user-attachments/assets/88cb4017-b189-48b9-98e0-86a181120769" />

Đọc file txt.  

<img width="949" height="226" alt="image" src="https://github.com/user-attachments/assets/2afa08fd-0620-49f2-9a98-f7deffee1237" />

>### 🎯 Password: ***QryZXc2e0zahULdHrtHxzyYkj59kUxLQ***
