## 🕵️‍♂️ Challenge:  
## Level 0 → Level 1
### The password for the next level is stored in a file called --spaces in this filename-- located in the home directory  

Commands you may need to solve this level  
> ls , cd , cat , file , du , find

## 📝 Solution:
Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit2`, cổng `2220`  
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

Khi đã ssh thành công, dùng lệnh `ls` để kiểm tra các file đang có, ta thấy có file `--spaces in this filename--`:  

<img width="296" height="55" alt="image" src="https://github.com/user-attachments/assets/07ee0cbb-e45f-4137-9b87-ff52d7a59161" />

Như phần trước, khi đọc file có tên là `-` ta phải thêm đầy đủ đường dẫn tới file đó thay vì mỗi tên file, bởi nếu ko thêm thì kí tự `-` sẽ được coi là 1 tùy chọn của lệnh.  
Vậy ta thử làm tương tự với bài này:  

<img width="476" height="91" alt="image" src="https://github.com/user-attachments/assets/54e6464e-d0c6-4cb6-a784-029ab18397c7" />

Nhìn output thì ta thấy lệnh cat được dùng nhiều lần với từng từ trong tên file, nguyên nhân là vì tên tệp có chứa dấu cách.  
Vậy bây giờ chỉ cần thêm hai dấu "" hoặc '' bao bọc lấy tên file sẽ được coi là 1 tên file hoàn chỉnh thay vì nhiều file.  
```bash
cat ./'--spaces in this filename--'
```
<img width="493" height="60" alt="image" src="https://github.com/user-attachments/assets/2a13e450-27c5-4604-bd5f-8dab762c23ff" />

Hoặc có thể chèn kí tự \ sau mỗi từ trong tên file thay vì bọc dấu "":  
```bash
cat ./--spaces\ in\ this\ filename--
```

<img width="504" height="42" alt="image" src="https://github.com/user-attachments/assets/358429d9-ac97-4dae-9c2c-d36ddd6dd04a" />

Như vậy là xong, ta đã có pass cho level tiếp theo.  

>### 🎯 Pass: ***MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx***
