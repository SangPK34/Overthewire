## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in a file called readme located in the home directory.  
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.  

Commands you may need to solve this level  
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit9`, cổng `2220`  
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

ssh thành công, ta kiểm tra thì thấy bên trong có file data.txt dạng ASCII text.  
Theo đề bài, ta cần tìm dòng bắt đầu bằng một số ký tự '='  
```bash
strings data.txt | grep =
```

<img width="466" height="318" alt="image" src="https://github.com/user-attachments/assets/5458b955-6999-4236-8e85-91bcf6a5d769" />

Vậy là xong.  

>### 🎯 Pass: ***FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey***
