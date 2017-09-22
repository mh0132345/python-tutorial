# Vòng lặp loops

Đơn giản là làm gì đó nhiều lần.
Có những loại vòng lặp sau:

- [While](#while) lặp lại tới khi điều kiện True.
- [Until](#until) lặp lại tới khi điều kiện False.
- [For](#for) lặp lại cho mỗi phần tử của cái gì đó.

Chúng ta sẽ nói về 3 loại trong phần này.

## While

Chúng ta đã biết về `if`

```python
troi_mua = True
if troi_mua:
    print("Troi dang mua!")
```

Vòng lặp while thực ra khá là giống if.
Lưu ý: Đừng thử vội

```python
troi_mua = True
while troi_mua:
    print("Troi dang mua!")
print("Troi khong mua nua.")
```

Nếu bạn chưa quen thuộc với vòng lặp thì kết quả sẽ là:

    Troi dang mua!
    Troi dang mua!
    Troi dang mua!
    Troi dang mua!
    Troi dang mua!
    (Còn nhiều dòng thế này nữa)

Chương trình sẽ liên tục in ra dòng trên mà không dừng lại. Đó là lý do lưu ý đừng thử vội. 

Trong ví dụ này, `troi_mua` là **điều kiện**. Nếu trong vòng while, `troi_mua` được đổi thành False, vòng while sẽ kết thúc và in ra `Troi khong mua nua.`.

Hãy tạo ra chương trình như thế:

```python
troi_mua = True
while troi_mua:
    print("Troi dang mua!")
    answer = input("Troi con mua khong? (y=yes, n=no) ")
    if answer == 'y':
        print("Oh...")
    elif answer == 'n':
        troi_mua = False     # kết thúc while
    else:
        print("Nhập y hoặc n vào lần tiếp theo.")
print("Troi khong mua nua.")
```

Chạy chương trình sẽ trông như thế này:

    Troi dang mua!
	Troi con mua khong? (y=yes, n=no) y
	Oh...
	Troi dang mua!
	Troi con mua khong? (y=yes, n=no) s
	Nhập y hoặc n vào lần tiếp theo.
	Troi dang mua!
	Troi con mua khong? (y=yes, n=no) n
	Troi khong mua nua.


Vòng while không phải luôn luôn kiểm tra mà chỉ kiểm tra lúc đầu một lần lặp.

```python
>>> troi_mua = True
>>> while troi_mua:
...     troi_mua = False
...     print("Troi khong mua, nhung vong while van chua biet.")
...
Troi khong mua, nhung vong while van chua biet.
>>>
```

Chúng ta cũng có thể dừng vòng lặp kể cả khi điều kiện còn đúng với `break`. 

```python
while True:
    answer = input("Troi co mua khong? (y=yes, n=no) ")
    if answer == 'y':
        print("Troi dang mua!")
    elif answer == 'n':
        print("Troi khong mua nua.")
        break   # kết thúc vòng lặp
    else:
        print("Nhap y hoac n.")
```

Kết quả sẽ như sau

    Troi co mua khong? (y=yes, n=no) f
	Nhap y hoac n.
	Troi co mua khong? (y=yes, n=no) y
	Troi dang mua!
	Troi co mua khong? (y=yes, n=no) n
	Troi khong mua nua.


Không giống như là đưa điều kiện về False để kết thúc vòng lặp, `break` chấm dứt vòng lặp ngay lập tức.

```python
>>> while True:
...     break
...     print("This is never printed.")
...
>>>
```

## Until

Python không có until. Nếu cần until, chúng ta có thẻ dùng `while not`:

```python
troi_mua = False
while not troi_mua:
    print("Troi khong mua.")
    if input("Troi co mua khong? (y/n) ") == 'y':
        troi_mua = True
print("Troi mua!")
```

## For

Hãy tưởng tượng chúng ta có một [list](lists-and-tuples.md) có nhiều thứ muốn in ra. Để in từng phần tử một thì lại phải gõ một đồng lệnh print:

```python
stuff = ['hello', 'hi', 'thanks']

print(stuff[0])
print(stuff[1])
print(stuff[2])
```

The output of the program is like this:

    hello
    hi
    thanks
    
Nhưng đây chỉ là 3 phần tử, nên nếu chúng ta thêm gì vào list thì nó sẽ không được in ra. Hoặc nếu xóa bớt đi với remove từ stuff, sẽ có lỗi báo "list index out of range".

Chúng ta có thể tạo một biến index, và dùng vòng lặp while:

```python
>>> stuff = ['hello', 'hi', 'thanks']
>>> length_of_stuff = len(stuff)	# Số các phần tử trong stuff
>>> index = 0						# Gán biến đếm
>>> while index < length_of_stuff:  # In cho tới khi hết các phần tử, tức biến đếm bằng số phần tử
...     print(stuff[index])			# In ra các phần tử ứng với biến đếm
...     index += 1					# Tăng biến đếm lên một sau mỗi lần in
...
hello
hi
thanks
>>>
```

Nhưng giờ lại có quá nhiều thứ chỉ để in ra cách phần tử riêng lẻ.

Đây là lý do dùng vòng lặp `for`

```python
>>> for thing in stuff:
...     # Vòng lặp cho mỗi phần tử trong stuff
...     # Đầu tiên là stuff[0], rồi stuff[1], rồi stuff[2].
...     print(thing)
...
hello
hi
thanks
>>>
```

Không có comment thì chỉ có 2 dòng để in ra. Nhìn gọn hơn hẳn

```python
>>> for thing in stuff:
...     print(thing)
...
hello
hi
thanks
>>>
```

Chú ý `for thing in stuff:` không phải `for (thing in stuff):`. Từ khóa `in` là một phần của vòng lặp chứ không phải `thing in stuff` để kiểm tra thing có trong stuff hay không. Nếu dùng `for (thing in stuff):` sẽ tạo ra lỗi.

Hiện tại bạn có thể nghĩ rằng vòng while dễ hiểu hơn, nhưng dần bạn sẽ nhận ra vòng for dễ dùng hơn là while với biến đếm. For cũng nhanh hơn một chút so với vòng while và biến đếm.

For không chỉ giới hạn cho mỗi lists. Chúng ta cũng có thể dùng cho string và [tuples](lists-and-tuples.md#tuples). Vòng lặp for cho tuple sẽ cho chúng ta sử dụng các phần tử, còn lặp cho string sẽ cho chúng ta toàn bộ các kí tự của string.

```python
>>> for short_string in 'abc':
...     print(short_string)
...
a
b
c
>>> for item in (1, 2, 3):
...     print(item)
...
1
2
3
>>>
```

Tuy nhiên cũng có một vấn đề khi lặp bằng for qua list. Nếu chúng ta chỉnh sửa list khi đang lặp, kết quả trong một số trường hợp sẽ rất phức tạp:

```python
>>> stuff = ['hello', 'hi', 'thanks']
>>> for thing in stuff:
...     stuff.remove(thing)
...
>>> stuff
['hi']
>>>
```

Thay vào đó chúng ta có thể tạo ra một bản copy của nó và lặp

```python
>>> stuff = ['hello', 'hi', 'thanks']
>>> for thing in stuff.copy():
...     stuff.remove(thing)
...
>>> stuff
[]
>>>
```

Hoặc có thể dùng clear() để xóa sạch list

```python
>>> stuff = ['hello', 'hi', 'thanks']
>>> stuff.clear()
>>> stuff
[]
>>>
```

## Tóm tắt

- Vòng lặp có nghĩa là lặp gì đó nhiều lần.
- Vòng while lặp đi lặp lại khi điều kiện vẫn còn là True, và chỉ kiểm tra đầu mỗi lần lặp.
- Vòng For có thể sử dụng để lặp lại những thứ như list, string.
- `break` dùng để ngắt vòng lặp chứa nó gần nhất bất cứ lúc nào.

## Ví dụ

Lăp lại gì đó liên tục không dừng

```python
message = input("Ban muon toi noi cai gi nao? ")
while True:
    print(message, "!!!")
```

Yêu cầu người dùng nhập vào 3 thứ, cho vào một list rồi in ra

```python
things = []

print("Nhap vao ba thu lan luot: ")
while len(things) < 5:
    thing = input("Nhap vao o day: > ")
    things.append(thing)

print("Ban da nhap vao: ")
for thing in things:
    print(thing)
```

In các số từ 10 tới 19:

```python
for num in range(10,20):
	print(num)
```

Hỏi cho người dùng phát chán

```python
cau_hoi = [
    # [câu hỏi, đáp án], ...
    ["2 + 4 = ", "6"],
    ["2 - 4 = ", "-2"],
    ["2 * 4 = ", "8"],
    ["2 / 4 = ", "0.5"],
	# Đây là list trong list
]

for q in cau_hoi:
    while True:
        if input(q[0]) == q[1]:
            print("Chinh xac!")
            break
        else:
            print("Sai roi...Hay thu lai.")
```

## Bài tập

1. Đoạn code này vốn dùng để in các số trong khoảng 1 và 5. Hãy sửa lại.

    ```python
    things = str([1, 2, 3, 4, 5])
    for thing in things:
        print(thing)
    ```

2. Đoạn code này dùng để in ra `[1, 2, 3, 4, 5, 6]`. Hãy sửa nó mà không thay đổi `ban_dau` list.

    ```python
    ban_dau = [[1, 2], [3, 4], [5, 6]]
    sau_do = []
    for number in ban_dau:
        sau_do.append(number)
    print(sau_do)
    ```

3. Chương trình sau chuyển các phần tử trong input về số nguyên int và tính tổng của chúng. Nên in ra 6  vì `1 + 2 + 3` bằng 6. Hãy sửa lại.

    ```python
    input = ['1', '2', '3']

    for string in input:
        numbers = []
        numbers.append(int(string))

    result = 0
    for n in numbers:
        result + n
    print("Tong la", result)
    ```

4. Chương trình sau muốn in ra `[1, 2, 3]`. Hãy sửa lại.

    ```python
    numbers = ['1', '2', '3']
    for number in numbers:
        number = int(number)
    print(numbers)
    ```

Câu trả lời ở [đây](answer.md#loops).
