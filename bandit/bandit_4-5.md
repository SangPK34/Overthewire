## 🕵️‍♂️ Challenge:  
## Level 4 → Level 
### The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  

Commands you may need to solve this level  
> ls , cd , cat , file , du , find
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit5`, cổng `2220`  
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

ssh thành công, kiểm tra xem có file hay folder nào ko thì thấy có folder `inhere`, vào trong kiểm tra thì thấy có rất nhiều folder khác:  

<img width="1169" height="151" alt="image" src="https://github.com/user-attachments/assets/e22594f0-6827-4e81-ad0e-0c324f030bd2" />



>### 🎯 Pass: ******
