# Sử dụng functions - hàm

Chúng ta đã biết in ra màn hình:

```python
>>> 'Hi!'
'Hi!'
>>>
```

Nhưng cách này bao gồm cả dấu `''`. Để hiển thị kí tự ra màn hình không có dấu `''` ta đã biết dùng print function.

```python
>>> print('Hi!')
Hi!
>>>
```

Nhưng chính xác thì print là gì mà lại in ra được. Tại sao không phải write viết ra chẳng hạn?

## Functions là gì?

Để xem gõ `print` mà không có `('Hi!')` thì kết quả sao nhé

```python
>>> print
<built-in function print>
>>>
```

Python trả lời với thông tin trong dấu <>. 

Như vậy, print là một function được xây dựng sẵn trong Python. Function sẽ làm một điều gì đó **khi được gọi ** bằng cách gõ tên của chúng cùng dấu ngoặc đơn `()`. Bên trong dấu ngoặc đơn thì có thể thêm biến vào. Trong function `print("Hi!")` thì function là `print` và nó nhận một biến đó là `"Hi!"`.

Đơn giản là function **làm một điều gì đó khi được gọi**. Function chạy ngay lập tức khi được gọi, do đó kí tự được hiển thị ngay lên màn hình khi ta gọi `print("Hi!")`.

## Giá trị trả về - Function return values

Một function khác ta được biết trong phần trước là input(). Ta đã gán như là name = input("Nhap ten: "). Ở đây, `input` là function và "Nhap ten: " là biến. Sau đó biến này được in ra màn hình. Người dùng nhập dữ liệu vào, và name được gán bằng dữ liệu nhập vào. Nhưng chính xác là dữ liệu đó từ đâu ra?

Giải thích: 

- Vế phải `input("Nhap ten: ")` được thực hiện đầu tiên. Nó gọi input function với biến được đưa vào là "Nhap ten: ".
- Function chạy và hiện ra dòng chữ "Nhap ten: ", sau đó chờ đợi để nhận giá trị người dùng nhập vào.
- Function trả về (return) một giá trị String, và giá trị đó được gán vào biến name. Sau đó, mỗi lần gọi biến name, ta sẽ chỉ tới giá trị đó, chứ không phải là chạy lại fucntion. Nếu nhập vào Marry chẳng hạn, tên đó sẽ được gắn vào giống như name = "Marry", giống như là thay thế đoạn gọi function đó với giá trị function return (trả về)

Ta sẽ thử trường hợp khác là `greeting = print('hello')`

```python
>>> greeting = print('hello')
hello
>>> print(gretting)       
None
>>>
```

Vậy `greeting = print('hello')` gán `greeting` về giá trị None.
None là một giá trị như thể là trạng thái rỗng của biến đó. Nó giống như là chẳng có giá trị gì cả. Có thể giờ nó hơi vô dụng nhưng sau này sẽ cần đến sau. Còn ở đây, print function **returns** None. Tất cả functions cần trả về một cái gì đó, va print trả về None vì nó chẳng cần trả về gì cả. Như vậy, ta có thể tưởng tượng vế phải là None thay vì `print('hello')`, vậy phép gắn là `greeting = None`.

Vậy **return value** là giá trị được trả về khi gọi một function. Khi ta gọi function, Python "thay" `function(arguments)` bằng giá trị được trả về.

Gọi function mà không gán vào biến nào cả (ví dụ như `print('hello')` thay vì `greeting = print('hello')`) đơn giản là bỏ giá trị đó đi. `>>>` prompt sẽ không hiện ra giá trị trả về vì đó là None.
Tất nhiên, `greeting = print('hello')` khá vô dụng so với `print('hello')` vì print luôn trả về None và ta có thể tự gán mà chẳng cần phải print.

Ta cũng có thể tự tạo function theo ý muốn để sử dụng. Đây là một function tính tổng 2 số đơn giản. Ta khai báo tên function là sum, có 2 biến đưa vào là a và b. Sau đó, ta trả về giá trị a+b là tổng 2 số. Ta có thể chạy thử function bằng cách gọi `sum(2,3)`.

```python
>>> def sum(a,b):
	return a+b

>>> sum(2,3)
5
>>> 
```

Tuy nhiên, ta sẽ tìm hiểu sâu hơn về khai báo function trong một bài tiếp theo thay vì bài này.

## Print

In một dòng rỗng bằng cách gọi print() với không có giá trị nào là arguments (biến đưa vào function) được khai báo.

```python
>>> print()

>>>
```

`\n` đại diện cho kí tự xuống dòng. In kí tự đó sẽ xuống dòng, giống như bạn gõ Enter xuống dòng trong Word vậy:

```python
>>> print('Hello\nworld')
Hello
world
>>>
```

Nếu muốn in một dấu gạch chéo `\`, ta phải gõ nó 2 lần. Như ở dưới đây, nó đã in ra dấu gạch chéo và kí tự n.

```python
>>> print('hello\\nworld')
hello\nworld
>>>
```

Chúng ta có thể cho nhiều đoạn kí tự vào print. Nó sẽ in ra với dấu cách xem giữa.

```python
>>> print("Hello", "World!")
Hello World!
>>>
```

Biến đưa vào print không nhất thiết là strings.

```python
>>> print(10, "la ỉnteger, so pi la", 3.14)
42 la integer, so pi la 3.14
>>>
```

## Tóm tắt

- `function()` gọi function với không arguments nào, còn `function(1, 2, 3)` gọi function với 1, 2 and 3 là arguments.
- Khi được gọi, function làm gì đó và trả về (return) giá trị nào đó
- `function(arguments)` sau đó được thay bằng giá trị trả về. Ví dụ, `name = function()` gọi function, sau đó gán name bằng giá trị trả về `name = return_value`.
- Những hàm `print` và `input` là functions được xây dụng sẵn trong Python. Nên tránh đặt tên biến trùng với chúng. 