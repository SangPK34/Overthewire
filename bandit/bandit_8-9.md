## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the file data.txt and is the only line of text that occurs only once  

Commands you may need to solve this level  
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit8`, cổng `2220`  
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

ssh thành công, kiểm tra bên trong, ta thấy có tệp data.txt dạng ASCII text.  
Đề bài yêu cầu tìm dòng duy nhất trong file xuất hiện 1 lần.  
Ta dùng lệnh:  
```bash
sort data.txt | uniq -u | grep -m1 .
```
Giải thích: `sort data.txt | uniq -u` đã lọc ra các dòng xuất hiện đúng 1 lần, `| grep -m1 .` in dòng không rỗng đầu tiên rồi dừng.  

<img width="486" height="59" alt="image" src="https://github.com/user-attachments/assets/c7356e04-0211-4076-897c-894d7e909d61" />

Như vậy là thành công.  

>### 🎯 Pass: ***4CKMh1JI91bUIZZPXDqGanal4xvAg0JM***
