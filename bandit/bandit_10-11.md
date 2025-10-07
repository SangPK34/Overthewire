## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the file data.txt, which contains base64 encoded data  
 
Commands you may need to solve this level  
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit10`, cổng `2220`  
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

Kiểm tra thì thấy có file data.txt với nội dung là 1 chuỗi base64:  


<img width="636" height="103" alt="image" src="https://github.com/user-attachments/assets/ed3aef5d-fd0a-4533-a538-947bd8e5523b" />

Dùng lệnh sau để decode nó:  
```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

<img width="448" height="70" alt="image" src="https://github.com/user-attachments/assets/af74eb37-bf4d-4569-80f9-d9a0457661e3" />


>### 🎯 Pass: ***dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr***
