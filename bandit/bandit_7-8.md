## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the file data.txt next to the word millionth  

Commands you may need to solve this level  
> man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit7`, cổng `2220`  
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

ssh thành công, tiến hành kiểm tra các file đang có:  

<img width="305" height="96" alt="image" src="https://github.com/user-attachments/assets/603123a1-b7fc-4dcc-bd2c-2b9398cde6ee" />

Ta thấy có file `data.txt` có định dạng ASCII text.  
Theo đề bài, cần tìm chuỗi password cạnh chuỗi `millionth`, ta dùng lệnh sau:  
```bash
strings data.txt | grep millionth
```

<img width="472" height="61" alt="image" src="https://github.com/user-attachments/assets/5d53a0dd-1dcf-4745-ba1d-68aa395e6119" />

Lệnh sẽ trả về dòng chứa chuỗi ta tìm, và mật khẩu cũng xuất hiện.  

>### 🎯 Pass: ***dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc***
