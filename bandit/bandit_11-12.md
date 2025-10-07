## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions  

Commands you may need to solve this level  
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit11`, cổng `2220`  
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

ssh thành công, ta thấy có file data.txt chứa 1 chuỗi ROT13, cần giải mã nó:  

<img width="447" height="105" alt="image" src="https://github.com/user-attachments/assets/f2a87ded-4c13-45db-bbc4-de79d8202f6e" />

Để giải mã ROT13, ta dùng lệnh:  
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

<img width="553" height="65" alt="image" src="https://github.com/user-attachments/assets/6b8a4bdf-6683-49db-9798-b72ef9f5b3cd" />


>### 🎯 Pass: ***7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4***
