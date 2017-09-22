# Answers

Đây là câu trả lời của tôi. Nếu chương trình bạn không giống mà vẫn chạy được thì không sao cả, đó có thể là một cách khác.

Do python dựa vào khoảng trắng, tab, dấu cách xác định các đoạn code, bạn nên cẩn thận chú ý khi copy. Bạn có thể sử dụng `CTRl + [` và `CTRL + ]` để tiến và lùi toàn bộ đoạn bôi đen 1 khoảng tab cho phù hợp.

Hãy chú ý đến khoảng trắng thụt vào đầu dòng! Nếu được hãy tự làm hoặc tự gõ lại.

## If, else, elif

1. Vấn đề và cách làm
    - Dòng đầu tiên cần phải là `print("Hello!")` hoặc `print('Hello!')` chứ không phải `print(Hello!)`. `Hello!` là một đoạn kí tự, nên chúng ta cần có dấu nháy bao quanh nó.
    - Dòng thứ hai sẽ tạo ra lỗi báo rằng không có biến `something`. Tuy nhiên ở đây chúng ta đang cố tạo ra biến đó, nên cần phải dùng `=` thay vì `==`. `=` là gán biến, `==` là so sánh. 
    - Tương tự như lỗi đầu tiên, phần bên trong input cần được bao quanh bởi dấu nháy.
    - Dòng cuối phải có dấu phẩy giữa các biến cho vào hàm print, ví dụ như `print('Ban da nhap: ', something)`.
    
    ```python
    print('Chao!')
    something = input('Nhap gi do: ' )
    print('Ban da nhap: ', something)
    ```

2. Khá giống bài 1. Sau đây là các vấn đề:

    - `==` sử dụng để so sánh.
    - Dòng elif thiếu dấu `:` ở cuối.
    - Dùng dấu phẩy ngăn cách trong hàm print.
    
    ```python
    print('Chào!')
    something = input("Nhap gi do: ")
    if something == 'hello':
        print("Chao ban")
    elif something == 'hi':
        print('Chao ban')
    else:
        print("Toi ko biet", something, "la gi dau!")    
    ```
    
3. Hỏi từ đó, cho vào biến word và in ra `word * 10`.

    ```python
    word = input("Moi nhap mot tu: ")
    print(word * 10)
    ```

    Thêm dấu cách ư? Thêm trước khi in là xong

    ```python
    word = input("Moi nhap mot tu: ")
    word += " "
    print(word * 10)
    ```

    Gọn hơn nữa:

    ```python
    word = input("Moi nhap mot tu: ") + " "
    print(word * 10)
    ```
    
4. Như thế này thôi:

    ```python
    first = input("Nhap tu thu nhat: ")
    second = input("Nhap tu thu hai: ")
    words = first + " " + second + " "
    print(words * 10)
    ```

5. Khác biệt là cách đọc số vào biến: 

    ```python
    num1 = int(input("Nhap so thu nhat: "))
    num2 = int(input("Nhap so thu hai: "))

    if num1%2 == 0:
        print(num1, "la so chan")
    else:
        print(num1, "la so le")

    if num2%2 == 0:
        print(num2, "la so chan")
    else:
        print(num2, "la so le")
    
    sum = num1 + num2
    print("Tong hai so la", sum)

    ```

6. 3 lần if. Bạn cũng có thể dùng elif

    ```python
    num = int(input("Chon 1 so (1-3): "))
    if num == 1:
	   print("Ban chon 1.")
    if num == 2:
	   print("Ban chon 2.")
    if num ==3: 
	   print("Ban chon 3.")
    ```
7. Cách làm của tôi. Chú ý `\n` là xuống dòng.

    ```python
    num1 = int(input("Nhap so thu nhat: "))
    num2 = int(input("Nhap so thu hai: "))
    print("(1) +\n(2) -\n(3) *\n(4) /")
    select = int(input("Chon mot so (1-4): "))
    if select==1:
        print("Ket qua la: ", num1+num2)
    elif select==2:
        print("Ket qua la: ", num1 - num2)
    elif select==3:
        print("Ket qua la: ", num1 * num2)
    elif select==4:
        print("Ket qua la: ", num1 / num2)
    else:
        print("Lua chon khong chinh xac")
    ```

## String 

1. Thay dòng cuối thôi: 
    ```python
    print("Ban da nhap {}, {}, {} va {}.".format(word1, word2, word3, word4))
    print("Ban da nhap %s, %s, %s va %s." % (word1, word2, word3, word4))
    ```

   Từ bản 3.6 trở lên thì thế này sẽ tiện hơn đây:

    ```python
    print(f"Ban da nhap {word1}, {word2}, {word3} va {word4}.")
    ```

2.  We have two problems. Đầu tiên, sửa `message.upper` thành `message.upper()`. Và cho giá trị đó vào biến nào đó: 

    ```python
    message = input("Noi gi day? ")
    uppermessage = message.upper()
    print(uppermessage, "!!!")
    print(uppermessage, "!!!")
    print(uppermessage, "!!!")
    ```

    Hoăc là dùng lại biến message.

    ```python
    message = input("Noi gi day? ")
    message = message.upper()
    print(message, "!!!")
    print(message, "!!!")
    print(message, "!!!")
    ```
    
    Hoặc đưa về dòng input luôn:

    ```python
    message = input("Noi gi day? ").upper()
    print(message, "!!!")
    print(message, "!!!")
    print(message, "!!!")
    ```

## Lists

1.  Hãy cẩn thận. `namelist` được tạo bởi `()` thay vì `[]`, nên nó đã thành tuple, không phải list. Bạn không muốn người ta nhìn code và ngạc nhiên nhìn bạn đâu. Thay `()` với `[]` và code sẽ chạy.

2. Hai array được in ra giống hệt nhau! Lý do là dòng code `b = a`. Chỉ việc tạo copy thay vì gắn cho b và a chung bộ nhớ như thế này thôi. Hãy đổi dòng đó thành `b = a.copy()` và kết quả in ra sẽ bình thường. 

3. Tiếp tục là lỗi lạ:

        Nhap ten cua ban: vim
	Traceback (most recent call last):
	  File "test.py", line 3, in <module>
    	if input("Nhap ten cua ban: ") in namelist:
	TypeError: argument of type 'NoneType' is not iterable


    Sửa chương trình để xem thử namelist có gì: 
    `namelist` seems to be None. 
	
    ```python
    namelist = ['john', 'python', 'git', 'gogogo', 'lelouch']
    namelist = namelist.extend('vim')
    print(namelist)
    ```

    Kết quả là None. 
    - Như vây namelist chẳng có gì cả. Lý do là chúng ta đã gắn `namelist = namelist.extend('vim')`. Nó nên được sửa chi còn `namelist.extend('vim')`
    - Giờ namelist lại thành  `['john', 'python', 'git', 'gogogo', 'lelouch', 'v', 'i', 'm']`. Đó là do Python xem `'vim'` là một list nên đã thêm mỗi kí tự của từ đó vào `namelist`. Chúng ta có thể dùng `namelist.append('vim')` hoặc `namelist.extend(['vim'])` để giải quyết.


