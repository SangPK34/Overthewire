## 🕵️‍♂️ Challenge:
Username: natas9  
Password: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t  
URL: http://natas9.natas.labs.overthewire.org  

<img width="1467" height="535" alt="image" src="https://github.com/user-attachments/assets/929a4e70-ad12-4bfc-a851-a12977e1d6af" />


## 📝 Solution: 
Xem source code:  

<img width="1363" height="840" alt="image" src="https://github.com/user-attachments/assets/0ce75a45-bf1f-4134-b028-71ba05998e8f" />

Ta có thể thấy vấn đề:  
Khi chuỗi người dùng nhập vào khác rỗng, `passthru("grep -i $key dictionary.txt");` sẽ chèn trực tiếp giá trị user nhập vào shell command → lỗ hỏng command injection.  
Ta chỉ cần nhập chuỗi ***; cat /etc/natas_webpass/natas9***, khi đó lệnh sẽ trở thành:  
```bash
grep -i ; cat /etc/natas_webpass/natas9 dictionary.txt
```
Điều này sẽ thực hiện 2 lệnh grep và cat riêng biệt, từ đó có thể cat được pass.  

<img width="771" height="297" alt="image" src="https://github.com/user-attachments/assets/666b0ebf-46e9-44aa-bf3c-43df4cf4787d" />

<img width="1607" height="665" alt="image" src="https://github.com/user-attachments/assets/c1add5ea-62e5-42f3-9843-270de15ef7f6" />


>### 🎯 Password: ***t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu***
