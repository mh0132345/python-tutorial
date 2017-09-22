# Lists and tuples

## Tại sao lại cần lists (danh sách, mảng)?

Đôi lúc chúng ta gặp phải tình trạng này:

```python
name1 = 'john'
name2 = 'python'
name3 = 'git'
name4 = 'gogogo'
name5 = 'lelouch'

name = input("Nhap ten cua ban: ")
if name == name1 or name == name2 or name == name3 or name == name4 or name == name5:
    print("Toi biet ban!")
else:
    print("Toi khong biet ban la ai :(")
```

Tất nhiên code vẫn chạy được, nhưng có một vấn đề. Biến name phải kiểm tra đi kiểm tra lại, và thêm vào một tên khác nữa thì sẽ còn phải lặp lại nhiều hơn, rất mệt mỏi.

## List

Thay vì tạo thêm biến mới cho mỗi tên mới, có lẽ sẽ tốt hơn nếu chứa tất cả tên chỉ trong một biến. Điều đó có nghĩa là chúng ta cầ một biến chỉ tới nhiều giá trị. Một cách đơn giản là sử dụng list:

```python
names = ['john', 'python', 'git', 'gogogo', 'lelouch']
```

`names` sẽ trỏ tới một list, và list đó sẽ chỉ tới các giá trị.

## Chúng ta có thể làm gì với lists?

MỞ `>>>` prompt và tạo name list.

```python
>>> names = ['john', 'python', 'git', 'gogogo', 'lelouch']
>>> names
['john', 'python', 'git', 'gogogo', 'lelouch']
>>>
```

Có rất nhiều thứ [chúng ta có thể làm với String](string.md), và phần lớn cũng có thể làm được tương tự với lists.

```python
>>> len(names)   # len viết tắt cho length, và chúng ta có 5 tên trong names
5
>>> names + ['Akuli']   # Nối 2 lists lại với nhau
['john', 'python', 'git', 'gogogo', 'lelouch', 'Akuli']
>>> ['john', 'python'] * 2    # Lặp lại nhiều lần
['john', 'python', 'john', 'python']
>>>
```

Khi slice lists chúng ta sẽ được một list mới, và cũng có thể chỉ thẳng đến một phần tử trong list.

```python
>>> names[:2]    # 2 tên đầu tiên: phần tử 0 và 1
['john', 'python']
>>> names[0]     # Phần tử đầu tiên trong names: 0
'john'
>>>
```

Nếu muốn kiểm tra một tên nào đó trong name không ta có thể dùng `in`

```python
>>> 'lol' in names
False
>>> 'python' in names
True
>>>
```

Tuy nhiên thì không thể sử dụng cái này kiểm tra xem list này có nằm trong list khác không

```python
>>> ['john', 'python'] in names
False
>>> ['git'] in names
False
>>>
```

Lists có khá nhiều [methods tiện lợi](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists). Những methods thường được dùng là append, extend và remove.

`append` thêm một phần tử vào cuối list, `extend` thêm nhiều phần tử từ list khác và `remove` để xóa một phần tử.

```python
>>> names
['john', 'python', 'git', 'gogogo', 'lelouch']
>>> names.remove('lelouch') # Bye lelouch
>>> names.remove('john')    # Bye john
>>> names
['python', 'git', 'gogogo']
>>> names.append('vim')	    # Thêm vim vào names
>>> names
['python', 'git', 'gogogo', 'vim']
>>> names.extend(['python', 'marry']) # Thêm vào nhiều hơn từ một list khác
>>> names
['python', 'git', 'gogogo', 'vim', 'python', 'marry']
>>> 

```

Chú ý rằng `remove` chỉ xóa phần tử đầu tiên nó gặp.

```python
>>> names
['python', 'git', 'gogogo', 'vim', 'python', 'marry']
>>> names.remove('python')
>>> names
['git', 'gogogo', 'vim', 'python', 'marry']
>>> 
```

Nếu muốn xóa hết chúng ta cần phải dùng vòng lặp. Chúng ta sẽ nói đến trong phần sau.

```python
>>> names.append('marry')
>>> names
['git', 'gogogo', 'vim', 'python', 'marry', 'marry']
>>> while 'marry' in names:
...     names.remove('marry')
... 
>>> names
['git', 'gogogo', 'vim', 'python']
>>> 
```

Chúng ta cũng có thể slice hoặc thay đổi từng phần tử một:

```python
>>> names
['git', 'gogogo', 'vim', 'python']
>>> names[1] = 'google'
>>> names
['git', 'google', 'vim', 'python']
>>> 
```

Và đó là thay đổi tại chỗ, không phải trả về một bản copy 

```python
>>> names = names.remove('vim')
>>> print(names)     # Kết quả là None vì remove sẽ return None
None
>>>
```

Như đã thấy, list **có thể thay đổi được**. 

## Một số điểm đặc biệt

Bạn có thể nhận ra

```python
>>> a = [1, 2, 3]
>>> b = a
>>> b.append(4)
>>> a    # Thay đổi theo luôn b!
[1, 2, 3, 4]
>>>
```

Điều này có thể hơi khó hiểu vì chúng ta chỉ thêm 4 vào b, không phải a. Tuy nhiên vấn đề ở đây là dòng code `b = a`. Ở đây, b không phải là copy toàn bộ giá trị của a, mà là chỉ vào thẳng nơi lưu trữ giá trị của a. Hay nói cách khác, a và b đều chỉ vào một chỗ, một bộ nhớ chứa list [1, 2, 3]

Từ khóa `is` sử dụng để kiểm tra hai biến có cùng chỉ tới **cùng** một nơi không.

```python
>>> a is b
True
>>>
```

Gõ `[]` tạo ra một list **mới**.

```python
>>> [] is []
False
>>> [1, 2, 3] is [1, 2, 3]
False
>>>
```

Như trên, hai list [1, 2, 3] tuy giống hệt nhau nhưng không chỉ tới cùng chỗ bộ nhớ, nên giá trị là False.

Vậy nếu chúng ta không muốn chỉ tới chung một bộ nhớ, mà muốn **một list mới có dữ liệu giống hệt** thì có thể dùng `copy` method.

```python
>>> a = [1, 2, 3]
>>> b = a.copy()
>>> b is a
False
>>> b.append(4)
>>> b
[1, 2, 3, 4]
>>> a
[1, 2, 3]
>>>
```

Ở đây b không trỏ tới bộ nhớ a, mà chỉ là bản copy. Do đó, khi thay đổi b thì a không thay đổi theo.

## Tuples

Tuples khá giống lists, nhưng các phần tử của chúng không thể thay đổi. Cách tạo khá giống lists, nhưng với dấu `()` thay vì `[]`.

```python
>>> thing = (1, 2, 3)
>>> thing
(1, 2, 3)
>>>
```
Phần tử trong tuples không thay đổi được: 

>>> thing[0] = 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> 

Nếu tạo tuple với 1 phần tử thì cần dùng `(item,)` thay vì `(item)` vì `(item)` sẽ bị xem như phép toán.

```python
>>> (3)
3
>>> (3,)
(3,)
>>> (1 + 2) * 3
9
>>> (1 + 2,) * 3
(3, 3, 3)
>>>
```

Cũng có thể tạo tuples với các phần tử cách nhau dấu phẩy và không có ngoặc như sau

```python
>>> 1, 2, 3
(1, 2, 3)
>>> 'hello',
('hello',)
>>>
```

Tuples không có methods như append, remove, extend

```python
>>> stuff = (1, 2, 3)
>>> stuff.append(4)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'append'
>>>
```

Dù có thể bạn cảm thấy tuple hơi vô dụng nhưng sẽ có rất nhiều trường hợp sẽ hợp với tuple hơn là list.

## Tóm tắt

- List là biến chỉ đến nhiều giá trị.
- Lists có thể thay đổi dễ dàng từng phần tử và cũng có các methods thay đổi chúng tại chỗ như append, extend và remove.
- Slicing list trả về list **mới**, và cũng có thẻ gọi riêng một phần tử trong list.
- `thing = another_thing` sẽ không tạo ra một bản copy của `another_thing`.
- Tuples giống lists, nhưng không thể tự thay đổi các phần tử. Và cả hai được sử dụng tùy trường hợp.

## Chỉnh sửa lại ví dụ lúc đầu

```python
namelist = ['john', 'python', 'git', 'gogogo', 'lelouch']

name = input("Nhap ten cua ban: ")
if name in namelist:
    print("Toi biet ban!")
else:
    print("Toi khong biet ban la ai :(")
```

## Exercises

1. Sửa lỗi:

    ```python
    namelist = ('john', 'python', 'git', 'gogogo', 'lelouch')
    namelist.append('pb123')
    if 'pb123' in namelist:
        print("Now I know pb123!")
    ```

2. Sửa lỗi:

    ```python
    a = [1, 2, 3]
    b = a
    b.append(4)
    print("List ban dau la: ", a)
    print("List sau khi them 4 la: ", b)
    ```

3. Sửa lỗi:

    ```python
    namelist = ['john', 'python', 'git', 'gogogo', 'lelouch']
    namelist = namelist.extend('vim')
    if input("Nhap ten cua ban: ") in namelist:
        print("Toi biet ban!")
    else:
        print("Toi khong biet ban la ai.")
    ```

Câu trả lời ở [đây](answer.md#lists).
