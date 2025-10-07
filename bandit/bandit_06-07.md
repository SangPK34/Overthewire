## 🕵️‍♂️ Challenge:  
### The password for the next level is stored somewhere on the server and has all of the following properties:  

owned by user bandit7  
owned by group bandit6  
33 bytes in size  
Commands you may need to solve this level  
> ls , cd , cat , file , du , find , grep

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit6`, cổng `2220`  
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

ssh thành công, ta kiểm tra bên trong xem có những gì:  

<img width="354" height="36" alt="image" src="https://github.com/user-attachments/assets/3c528d5c-6ee0-48af-9f43-b234897d10bc" />

Mục tiêu đề bài, ta cần tìm file thuộc người dùng bandit7, nhóm bandit6 và kích thước 33 bytes, dùng lệnh sau:  

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
Trong đó `2>/dev/null` để bỏ qua lỗi.  

<img width="755" height="59" alt="image" src="https://github.com/user-attachments/assets/91dfbbfb-6c2a-429a-823e-10c76447213d" />

<img width="521" height="53" alt="image" src="https://github.com/user-attachments/assets/ce4bfb76-cbd7-4578-92be-61ad6afe8e4c" />

Vậy là đã tìm được mục tiêu.  

>### 🎯 Pass: ***morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj***
