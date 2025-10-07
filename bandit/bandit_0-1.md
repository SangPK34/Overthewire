## 🕵️‍♂️ Challenge:  
## Level 0 → Level 1
### The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220.  
The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.  
Commands you may need to solve this level:  
> ssh

## 📝 Solution:
Với thử thách bandit đầu tiên này, mục tiêu của chúng ta là vào được máy chủ bandit của máy chủ overthewire bằng lệnh ssh.  
Với người dùng là `bandit0` và máy chủ `bandit.labs.overthewire.org`, cổng `2220` thì ta dùng lệnh:  
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
Khi được hỏi mật khẩu, ta nhập `bandit0`.  

<img width="768" height="866" alt="image" src="https://github.com/user-attachments/assets/f16918c1-192e-4567-ae1c-3e96905ef736" />

<img width="762" height="848" alt="image" src="https://github.com/user-attachments/assets/d5554925-0133-40f4-879d-fc8ba6be75c8" />

Như vậy là ta đã truy cập thành công remote shell của máy chủ overthewire với người dùng bandit0.  
Tiến hành kiểm tra các file đang tồn tại trên máy bằng lệnh:  
```bash
ls
```
<img width="219" height="92" alt="image" src="https://github.com/user-attachments/assets/e87ad2b5-f0cf-4e13-a2d2-ba5958d71b97" />

Thấy tồn tại file readme, tiến hành kiểm tra loại file bằng lệnh:  
```bash
file readme
```

<img width="281" height="69" alt="image" src="https://github.com/user-attachments/assets/2f915e36-2313-4c12-b526-d7c873414bcb" />

Như vậy là 1 file text, bây giờ đọc nó, ta dùng lệnh:  

```bash
cat readme
```
<img width="775" height="196" alt="image" src="https://github.com/user-attachments/assets/a54884fe-d39f-4e2a-a84c-cd398f925f6e" />

Như vậy ta đã có được password cho level sau.  

>### 🎯 Pass: ***ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If***
