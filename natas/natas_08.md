## 🕵️‍♂️ Challenge:
Username: natas8  
Password: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q  
URL: http://natas8.natas.labs.overthewire.org  

<img width="1721" height="543" alt="image" src="https://github.com/user-attachments/assets/659e1cb8-f3b1-426a-8eda-45427a46171a" />


## 📝 Solution: 
Xem source code:  

<img width="1386" height="934" alt="image" src="https://github.com/user-attachments/assets/b75f6590-d5d2-46dc-99f6-93ad0884b7b3" />

Ta thấy có đoạn mã thể hiện cách mã hóa để được xâu secret `3d3d516343746d4d6d6c315669563362`.  
Hàm encodeSecret làm 3 bước theo thứ tự:  

base64_encode($secret) → mã hoá base64.  

strrev(...) → đảo chuỗi kết quả.  

bin2hex(...) → chuyển từng byte ra dạng hex.  

Dựa vào logic mã hóa đó, ta sẽ giải mã ngược lại để lấy chuỗi gốc, bằng cách từ chuối hex → unhex → chuỗi base64 bị đảo → đảo lại → base64-decode → secret:  

```bash
echo -n "3d3d516343746d4d6d6c315669563362" | xxd -r -p | rev | base64 -d
```
<img width="865" height="124" alt="image" src="https://github.com/user-attachments/assets/84cf86d0-a77e-4212-a09b-947fe208cc53" />

Nhập secret này vào:  

<img width="1453" height="549" alt="image" src="https://github.com/user-attachments/assets/0b6742d2-2615-4fbb-bb3d-ba1a50a5d1b5" />

>### 🎯 Password: ***ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t***
