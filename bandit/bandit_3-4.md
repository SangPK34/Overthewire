## 🕵️‍♂️ Challenge:  
## Level 3 → Level 4 
### The password for the next level is stored in a hidden file in the inhere directory.  

Commands you may need to solve this level  
> ls , cd , cat , file , du , find
## 📝 Solution:  

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit3`, cổng `2220`  
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

Ssh thành công, ta ls để kiểm tra xem có file hay thư mục nào đang tồn tại ko:  

<img width="189" height="43" alt="image" src="https://github.com/user-attachments/assets/29370642-6eaa-4d51-b869-d82528823e37" />

Như vậy là có folder `inhere`, để vào trong folder, nhập:  
```bash
cd inhere
```
Kiểm tra các file đang có trong thư mục này:  

<img width="808" height="44" alt="image" src="https://github.com/user-attachments/assets/73877935-2069-47e8-add3-6408c6fa8b83" />

Ta thấy có rất nhiều file với kí tự `-` đằng trước, vậy để tránh bị hiểu nhầm thành option của lệnh khi cat, ta thêm `--` trước tên file:  
```bash
cat -- -file01
```
<img width="369" height="44" alt="image" src="https://github.com/user-attachments/assets/d46347a7-644f-4bf3-8c3a-5af7592c40db" />

Để đọc tất cả các file cùng lúc, ta nhập:  
```bash
cat -- *
```
<img width="1707" height="102" alt="image" src="https://github.com/user-attachments/assets/432b7e77-b559-4ac7-9d39-b1d66651138e" />

Như vậy là xong, ta đã có được pass của level sau.  

>### 🎯 Pass: ***4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw***
