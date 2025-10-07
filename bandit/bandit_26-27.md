## 🕵️‍♂️ Challenge:  
### Good job getting a shell! Now hurry and grab the password for bandit27!

Commands you may need to solve this level
> ls

## 📝 Solution:
Password lấy từ thử level trước:  
> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

Tiếp tục level trước, ta đã lấy được shell của bandit26, giờ thì xem bên trong có những gì:  

<img width="405" height="143" alt="image" src="https://github.com/user-attachments/assets/86ab0d37-8d23-461e-a8bd-1152339bbd50" />

Có 1 file setuid `bandit27-do` 
Kiểm tra thì thấy nó có thể chạy được trên bandit16 để lấy pass bandit17.  
Dùng lệnh:  
```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

<img width="758" height="83" alt="image" src="https://github.com/user-attachments/assets/c4f38d79-2b40-46c8-9c56-cc9e8e434e40" />

>### 🎯 Pass: ***upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB***
