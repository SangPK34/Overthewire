## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  

Commands you may need to solve this level  
> ls , cd , cat , file , du , find

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit4`, cổng `2220`  
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

Kiểm tra file trên máy host, ta thấy có thư mục `inhere`, bên trong chứa các file có dấu `-` ở đầu, giờ hãy kiểm tra xem file nào là file có thể đọc:  
```bash
file ./*
```

<img width="765" height="220" alt="image" src="https://github.com/user-attachments/assets/26c783f6-6663-4308-954a-c11ac79d2c1d" />

Như vậy ta có thể thấy file `-file07` là dạng Ascii text có thể đọc.  

<img width="367" height="67" alt="image" src="https://github.com/user-attachments/assets/662baf3c-589b-43a9-8db8-6ea50c6a8a08" />

Vậy là xong.  

>### 🎯 Pass: ***4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw***
