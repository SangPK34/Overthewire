## 🕵️‍♂️ Challenge:
Username: natas10  
Password: t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu  
URL: http://natas10.natas.labs.overthewire.org  

<img width="1411" height="563" alt="image" src="https://github.com/user-attachments/assets/345a1c55-e1d6-4ad5-9381-c4863395a6e5" />


## 📝 Solution: 
Xem nguồn trang:  

<img width="1355" height="929" alt="image" src="https://github.com/user-attachments/assets/5845f24c-4daf-4603-a543-e618e3005747" />

Ta thấy so với thử thách trước, lần này họ đã chặn việc nhập các kí tự `; | &`.  

Tuy nhiên chỉ vậy là chưa đủ, lần này ta sẽ để grep hoạt động thực sự bằng cách nhập chuỗi `.* /etc/natas_webpass/natas11 #`, khi đó câu lệnh sẽ là:  
```bash
grep -i . /etc/natas_webpass/natas11 # dictionary.txt
```
Lệnh `grep` sẽ in toàn bộ nội dung của file `/etc/natas_webpass/natas11`, sau dấu # sẽ được coi là comment, ko thực thi.  
Sau khi nhập, mật khẩu sẽ xuất hiện:  

<img width="1213" height="649" alt="image" src="https://github.com/user-attachments/assets/1b07cbcb-b782-45d8-8922-03b9b70cc931" />


>### 🎯 Password: ***UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk***
