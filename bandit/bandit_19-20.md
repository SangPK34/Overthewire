## 🕵️‍♂️ Challenge:  
### To gain access to the next level, you should use the setuid binary in the homedirectory.  
Execute it without arguments to find out how to use it.  
The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.  

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit19`, cổng `2220`  
```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

Khi ssh thành công, kiểm tra thì thấy 1 file có tên: `bandit20-do`, thử chạy thì nó báo:  

<img width="312" height="99" alt="image" src="https://github.com/user-attachments/assets/7e67f337-dca9-45a4-a567-4c8efa5a20d8" />
<br>
<br>
Vậy thử chạy:  
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

<img width="583" height="86" alt="image" src="https://github.com/user-attachments/assets/d1786da9-88ed-4283-bd14-8b9ec3d5ecbe" />

Xong!  

>### 🎯 Pass: ***0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO***
