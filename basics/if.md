# If, else và elif

## Sử dụng if

Chúng ta đã biết về True và False ở phần trước.

```python
>>> 1 == 1
True
>>> 1 == 2
False
>>>
>>> troi_mua = True
>>> troi_mua
True
>>>
```

Nhưng nếu chúng ta muốn chạy code phụ thuộc một điều kiện nào đó?
Đây là lúc để dùng câu lệnh `if`

```python
>>> troi_mua = True
>>> if troi_mua:
	print("Troi dang mua")     # Nếu trời mưa là đúng thì in ra trời đang mưa

	
Troi dang mua
>>> troi_mua = False
>>> if troi_mua:
	print("Troi dang mua")     # Chẳng có gì xảy ra vì troi_mua đang là False

	
>>>
```

Prompt chuyển từ `>>>` thành `...`. Nó có nghĩa là Python đang chờ chúng là gõ tiếp vào. Khi hoàn thành, chỉ việc nhấn Enter hai lần. Python sẽ chạy đoạn code và prompt trở thành `>>>`.

Chú ý: Dòng có câu lệnh print được cố tình lùi vào **một khoảng trắng**. Bạn có thể ấn phím Tab, hoặc ấn phím cách khoảng 4 lần. Nhưng trong một chương trình thì nên chọn một trong hai cách là Tab hoặc 4 Spaces.

Đồng thời chú ý rằng `if` chỉ kiểm tra điều kiện duy nhất một lần, nêu sau đó có thể thay đổi điều kiện lại trong vòng if thì câu lệnh vẫn không nhận ra. Nhưng câu lệnh `if` kiểm tra tiếp theo thì sẽ kiểm tra lại đó!

```python
>>> troi_mua = True
>>> if troi_mua:
	troi_mua = False   # Trời được chuyển thành hết mưa
	print("Troi vua het mua, nhung cau lenh print van chay")   #Vẫn in ra màn hình dù đã chuyển thành False

	
Troi vua het mua, nhung cau lenh print van chay
>>> 
```

## Sử dụng else

Thế nếu trời không mưa mà lại muốn in một câu khác thì sao?
Bạn có thể nghĩ tới trường hợp thế này

```python
troi_mua = True                  # Gán troi_mua là True. Bạn có thể đổi lại False nếu thích
troi_ko_mua = not troi_mua       # troi_ko_mua là ngược lại troi_mua. Nếu troi_mua True thì troi_ko_mua là False và ngược lại

if troi_mua:
    print("Troi dang mua!")       # Nếu trời mưa là True thì in ra Trời đang mưa
if troi_ko_mua:
    print("Troi khong mua.")     # Nếu trời không mưa là True thì in ra Trời không mưa
```

Code trong ví dụ này không bắt đầu với `>>>`, nên bạn sẽ phải **lưu vào file và chạy file đó**. 
Bạn có thể chọn File, New File hoặc `Ctrl + N`. `Ctrl + S` để lưu lại và `F5` để chạy file.
Đây là IDLE, bạn có thể thử Notepad++ tại [đây](https://notepad-plus-plus.org/repository/7.x/7.5.1/npp.7.5.1.Installer.exe) hay IDE khác để gõ Tiếng Việt tốt hơn, sau đó vẫn có thể mở file đó ra và chạy bình thường.

Chương trình sẽ in ra màn hình tùy theo giá trị của troi_mua là True hay False.

Chúng ta cũng có thể dùng `not troi_mua` trực tiếp thế này:

```python
troi_mua = True            

if troi_mua:
    print("Troi dang mua!")      
if not troi_mua:                 # nếu như ngược lại với troi_mua là True
    print("Troi khong mua.") 
```

Nhưng tốt hơn là dùng `else`:

```python
troi_mua = False         

if troi_mua:
    print("Troi dang mua")      
else:                           # nếu như điều kiện của if là sai
    print("Troi khong mua.")    # In ra trời không mưa vì troi_mua là False

```

Vòng else đơn giản là nếu kiểm tra ở vòng if là sai. Vòng else không tự kiểm tra lại.

```python
>>> troi_mua = True
>>> if troi_mua:
	troi_mua = False
else:           # Trời mưa đã là False, nhưng if không kiểm tra lại nên không chạy vào else
	print("Troi khong mua, nhung vong else van khong chay") 

	
>>> 
```

Kết hợp else với hàm `input` để đọc dữ liệu từ bàn phím do người dùng nhập vào ta có thể làm một chương trình kiểm tra mật khẩu:

```python
print("Hello")
password = input("Moi nhap mat khau: ")     # Đọc dữ liệu nhập vào từ bàn phím và gán vào biến password

if password == "pass":                      # Nếu nhập vào chính xác mật khẩu (ở đây mật khẩu là pass)
    print("Dang nhap thanh cong!")
else:
    print("Dang nhap that bai.")

```

Chương trình sẽ in ra kết quả khác nhau theo dữ liệu nhập vào.

```
Hello
Moi nhap mat khau: pass
Dang nhap thanh cong!
```

```
Hello
Moi nhap mat khau: g
Dang nhap that bai.
```

Tất nhiên cách này không hiệu quả và không bảo mật. Nhưng đây chỉ là ví dụ, bạn chưa cần quan tâm nhiều về nó.

## Tránh việc lặp lại quá nhiều với elif

Nếu có khá nhiều điều kiện cần kiểm tra thì sao? Ví dụ:

```python
word = input("Nhap gi do vao: ")

if word == "Chao":
    print("Chao ban!")
else:
    if word == "Ban la ai":
        print("Toi la Python")
    else:
        if word == "Dm":
            print("De nghi nhap lai")
        else:
            if word == "Bye":
                print("Bye Bye")
            else:
                print("Toi khong biet", word, "nghia la gi")
```

Một đống lộn xộn. Chúng ta kiểm tra 4 từ, nên có 4 tầng kiểm tra. Nếu nhiều hơn nữa thì sẽ cực rắc rối và khó.

Thay vì gõ `else`, xuống dòng và gõ `if` chúng ta có thể dùng `elif`, viết tắt cho `else if`:

```python
word = input("Nhap gi do vao: ")

if word == "Chao":
    print("Chao ban!")
elif word == "Ban la ai":
    print("Toi la Python")
elif word == "Dm":
    print("De nghi nhap lai")
elif word == "Bye":
    print("Bye Bye")
else:
    print("Toi khong biet", word, "nghia la gi")

```
Chú ý rằng word là biến lưu trữ String được nhập vào, nên phải in ra như dòng cuối.
Giờ thì chương trình dễ đọc hơn rồi!

Thế nếu muốn đọc số vào biến thì làm sao:

```python
num = input("Nhap mot so: ")
if num == 1:
    print("Chinh xac")
```

Thế nhưng khi nhập 1 vào, chương trình lại chẳng in ra gì là sao?
Ở đây, khi bạn nhập từ bàn phím vào, dữ liệu sẽ ở dạng **String**. Vì vậy, '1' sẽ khác với 1 và num == 1 sẽ là False. Do đó, bạn cần chuyển dữ liệu từ String về số. Với số nguyên thì đó là int, viết tắt cho integer. Với số thực thì có thể là float, double. Chúng ta sẽ tìm hiểu sau. Giờ hãy thử lại: 

```python
num = int(input("Nhap mot so: "))
if num == 1:
    print("Chinh xac")
```
Chương trình sẽ in ra `Chinh xac`. Vậy là biến num đã chứa số nguyên 1 rồi đó.

Đoán xem hai đoạn này sẽ in ra gì?

```python
if 1 == 1:
    print("hello")
elif 1 == 2:
    print("False")
else:
    print("world")
```

và 

```python
if 1 == 1:
    print("hello")
if 1 == 2:
    print("False")
else:
    print("world")
```

Chú ý rằng ở đoạn code thứ hai, vòng `else` sẽ gắn liền với vòng if 1 == 2, **không liên quan tới vòng if đầu tiên** do đó sẽ in ra hello world. Còn ở đoạn code thứ nhất khi dùng `elif` sẽ nối với phần trên if 1==1 nên chỉ in ra hello. Như vậy `elif` nhóm nhiều vòng `if` lại với nhau và `else` thuộc về cả nhóm đó.

## Tóm tắt

- Nếu code bắt đầu với `>>>` thì chạy trực tiếp trên prompt. Còn không thì viết vào file rồi chạy file đó.
- Đoạn code thụt vào sau if rất quan trọng. Nó sẽ được chạy nếu điều kiện của if là chính xác.
- Chúng ta cũng có thể dùng else. Đoạn code thụt vào sẽ chạy nếu điều kiện vòng if không phải là True.
- Có thể đọc dữ liệu từ bàn phím và gán vào biến với input. Ví dụ: name = input("Nhap ten: "). 
- Nếu muốn nhập số từ bàn phím thì phải chuyển kiểu dữ liệu từ String thành dạng số như int, float, double.
- elif là viết tắt cho else if.

## Bài tập

1. Chương trình sau có lỗi. Hãy copy vào file và sửa lỗi cho tới khi đoạn code chạy thành công.

    ```python
    print(Chao!)
    something == input('Nhap gi do )
    print('Ban da nhap: ' something)
    ```

2. Sửa lỗi như câu 1:

    ```python
    print('Chào!')
    something = input("Nhap gi do: ")
    if something = 'hello':
        print("Chao ban")
    elif something = 'hi'
        print('Chao ban')
    else:
        print("Toi ko biet" something, "la gi dau!")
    ```

3. Viết một chương trình yêu cầu người dùng nhập vào một từ và in từ đó ra 10 lần. Ví dụ, nhập vào `hi` chương trình in ra `hihihihihi...`. Sau  
đó hãy thử thêm dấu cách giữa cái từ để thành `hi hi hi hi.....`

4. Yêu cầu người dùng nhập vào hai và in ra 2 từ đó mỗi từ 10 lần, cách nhau bởi dấu cách. Ví dụ như nhập `hello` và `hi` thì in ra là: `hello hi hello hi hello hi` ...

5. Tạo một chương trình yêu cầu người dùng nhập vào hai số nguyên. Sau đó, in ra xem hai số đó là số chẵn hay lẻ, rồi in ra tổng của hai số đó. Ví dụ nhập vào 2 và 3 thì lần lượt in ra "2 là so chan", "3 la so le", "Tong hai so la 5".

6. Tạo một chương trình yêu cầu người dùng nhập vào số từ 1 tới 3. Nếu nhập vào 1 thì in ra "Ban chon 1", 2 thì in ra "Ban chon 2", 3 thì in ra "Ban chon 3"

7. Tạo ra một máy tính cơ bản. Chương trình yêu cầu người dùng nhập vào hai số, sau đó lựa chọn một trong bốn phép tính cộng trừ nhân chia và in ra kết quả. Nếu chọn một thì làm phép cộng, 2 thì trừ, 3 là nhân và 4 là chia. Ví dụ
Nhap so thu nhat: 100
Nhap so thu hai: 25
(1) +
(2) -
(3) *
(4) /
Chon mot phep tinh (1-4): 3
Ket qua la: 2500

Bạn có thể tham khảo về print để làm cho thuận tiện hơn ở [đây](functions.md#print)

Đáp án ở [đây](answers.md#if-else-elif).
