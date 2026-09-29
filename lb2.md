# Лабораторная работа №2

## Задача 1

**Вопрос:** Напишите функцию `convert_types(data)`, которая принимает список и возвращает новый список, где каждый элемент преобразован: числа в строки, строки в числа (если возможно), остальные элементы — в строковое представление.

**Подсказка:** Используйте `try-except` для безопасного преобразования строк в числа.

**Решение:**

```python
def convert_types(data):
    result = []
    for item in data:
        if type(item) == str:
            try:
                if "." in item:
                    result.append(float(item))
                else:
                    result.append(int(item))
            except ValueError:
                result.append(item)
        else:
            result.append(str(item))
    return result


print(convert_types([1, "2", "hello", 3.5]))  # ['1', 2, 'hello', '3.5']
```

**Ответ:** Функция возвращает преобразованный список.

**Пример:** `convert_types([1, "2", "hello", 3.5])` → `["1", 2, "hello", "3.5"]`

---

## Задача 2

**Вопрос:** Напишите функцию `swap_values(a, b)`, которая меняет значения двух переменных местами **без использования третьей переменной** и возвращает кортеж `(a, b)`.

**Подсказка:** Используйте множественное присваивание Python.

**Решение:**

```python
def swap_values(a, b):
    a, b = b, a
    return a, b


print(swap_values(5, 10))  # (10, 5)
```

**Ответ:** Функция возвращает кортеж с обменянными значениями.

**Пример:** `swap_values(5, 10)` → `(10, 5)`

---

## Задача 3

**Вопрос:** Напишите функцию `bool_transform(value)`, которая возвращает `True`, если значение «истинное» (не 0, не пустое), и `False` иначе, **без использования `bool()`**.

**Подсказка:** Используйте условный оператор.

**Решение:**

```python
def bool_transform(value):
    if not value:
        return False
    else:
        return True


print(bool_transform(5))  # True
print(bool_transform(0))  # False
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `bool_transform(5)` → `True`, `bool_transform(0)` → `False`

---

## Задача 4

**Вопрос:** Напишите функцию `compound_operations(a, b)`, которая выполняет все составные операции (`+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`) над `a` со значением `b` и возвращает список результатов.

**Подсказка:** Создайте копию `a` для каждой операции.

**Решение:**

```python
def compound_operations(a, b):
    results = []
    for op in ["+=", "-=", "*=", "/=", "//=", "%=", "**="]:
        x = a  # отдельная копия для каждой операции
        if op == "+=":
            x += b
        elif op == "-=":
            x -= b
        elif op == "*=":
            x *= b
        elif op == "/=":
            x /= b
        elif op == "//=":
            x //= b
        elif op == "%=":
            x %= b
        elif op == "**=":
            x **= b
        results.append(x)
    return results


print(compound_operations(10, 3))
# [13, 7, 30, 3.3333333333333335, 3, 1, 1000]
```

**Ответ:** Функция возвращает список из 7 результатов операций.

**Пример:** `compound_operations(10, 3)` → `[13, 7, 30, 3.33, 3, 1, 1000]` (значение `3.33` в примере округлено).

---

## Задача 5

**Вопрос:** Напишите функцию `check_type(value, expected_type)`, которая проверяет, соответствует ли тип `value` ожидаемому типу (строка `'int'`, `'float'`, `'str'`, `'list'`, `'bool'`), и возвращает `True` или `False`.

**Подсказка:** Используйте `type()` и `type().__name__`.

**Решение:**

```python
def check_type(value, expected_type):
    actual_name = type(value).__name__
    if actual_name == expected_type:
        return True
    return False


print(check_type(5, 'int'))    # True
print(check_type("5", 'int'))  # False
print(check_type(True, 'int')) # False (bool — отдельный тип)
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `check_type(5, 'int')` → `True`, `check_type("5", 'int')` → `False`

---

## Задача 6

**Вопрос:** Напишите функцию `logical_and(a, b, c)`, которая возвращает `True`, только если все три аргумента «истинные», **без использования оператора `and`**.

**Подсказка:** Используйте вложенные `if`.

**Решение:**

```python
def logical_and(a, b, c):
    if a:
        if b:
            if c:
                return True
            else:
                return False
        else:
            return False
    else:
        return False


print(logical_and(True, 5, "x"))  # True
print(logical_and(True, 0, "x"))  # False
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `logical_and(True, 5, "x")` → `True`, `logical_and(True, 0, "x")` → `False`

---

## Задача 7

**Вопрос:** Напишите функцию `logical_or(a, b, c)`, которая возвращает `True`, если хотя бы один аргумент «истинный», **без использования оператора `or`**.

**Подсказка:** Используйте несколько `if` с ранним возвратом.

**Решение:**

```python
def logical_or(a, b, c):
    for argument in (a, b, c):
        if argument:
            return True
    return False


print(logical_or(0, "", False))  # False
print(logical_or(0, 5, False))   # True
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `logical_or(0, "", False)` → `False`, `logical_or(0, 5, False)` → `True`

---

## Задача 8

**Вопрос:** Напишите функцию `is_between(value, low, high)`, которая проверяет, находится ли `value` между `low` и `high` (включительно), используя **один составной условный оператор**.

**Подсказка:** Используйте `and` в условии `if`.

**Решение:**

```python
def is_between(value, low, high):
    if low <= value and value <= high:
        return True
    else:
        return False


print(is_between(5, 1, 10))   # True
print(is_between(15, 1, 10))  # False
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `is_between(5, 1, 10)` → `True`, `is_between(15, 1, 10)` → `False`

---

## Задача 9

**Вопрос:** Напишите функцию `print_even_numbers(n)`, которая выводит все чётные числа от 1 до `n` включительно, используя цикл `for`.

**Подсказка:** Используйте `range()` с шагом 2 или проверку `% 2`.

**Решение:**

```python
def print_even_numbers(n):
    for number in range(1, n + 1):
        if number % 2 == 0:
            print(number)


print_even_numbers(10)
```

**Ответ:** Функция выводит в консоль чётные числа.

**Пример:** `print_even_numbers(10)` → выведет: `2 4 6 8 10` (каждое с новой строки)

---

## Задача 10

**Вопрос:** Напишите функцию `countdown_while(n)`, которая выводит числа от `n` до 1 в обратном порядке, используя цикл `while`.

**Подсказка:** Уменьшайте счётчик внутри цикла.

**Решение:**

```python
def countdown_while(n):
    current = n
    while current > 0:
        print(current)
        current = current - 1


countdown_while(5)
```

**Ответ:** Функция выводит в консоль числа в обратном порядке.

**Пример:** `countdown_while(5)` → выведет: `5 4 3 2 1` (каждое с новой строки)

---

## Задача 11

**Вопрос:** Напишите функцию `skip_multiples(n, multiple)`, которая выводит числа от 1 до `n`, но **пропускает** числа, делящиеся на `multiple`, используя `continue`.

**Подсказка:** Проверка `if i % multiple == 0: continue`.

**Решение:**

```python
def skip_multiples(n, multiple):
    number = 0
    while number < n:
        number += 1
        if number % multiple == 0:
            continue
        print(number)


skip_multiples(10, 3)
```

**Ответ:** Функция выводит в консоль числа, пропуская кратные.

**Пример:** `skip_multiples(10, 3)` → выведет: `1 2 4 5 7 8 10` (пропущены 3, 6, 9)

---

## Задача 12

**Вопрос:** Напишите функцию `if_elif_else_chain(x)`, которая:

- возвращает `"positive"`, если `x > 0`
- возвращает `"negative"`, если `x < 0`
- возвращает `"zero"`, если `x == 0`

Используйте полную конструкцию `if-elif-else`.

**Подсказка:** Три ветви условия.

**Решение:**

```python
def if_elif_else_chain(x):
    if x == 0:
        answer = "zero"
    elif x > 0:
        answer = "positive"
    else:
        answer = "negative"
    return answer


print(if_elif_else_chain(5))   # positive
print(if_elif_else_chain(-3))  # negative
print(if_elif_else_chain(0))   # zero
```

**Ответ:** Функция возвращает строку.

**Пример:** `if_elif_else_chain(5)` → `"positive"`, `if_elif_else_chain(-3)` → `"negative"`, `if_elif_else_chain(0)` → `"zero"`

---

## Задача 13

**Вопрос:** Напишите функцию `abs_value(x)`, которая возвращает абсолютное значение числа **без использования `abs()`**.

**Подсказка:** Используйте условный оператор.

**Решение:**

```python
def abs_value(x):
    return x if x >= 0 else -x


print(abs_value(-5))  # 5
print(abs_value(3))   # 3
```

**Ответ:** Функция возвращает неотрицательное число.

**Пример:** `abs_value(-5)` → `5`, `abs_value(3)` → `3`

---

## Задача 14

**Вопрос:** Напишите функцию `binary_representation(n)`, которая возвращает двоичное представление числа в виде строки **без использования `bin()`**.

**Подсказка:** Делите на 2 и собирайте остатки.

**Решение:**

```python
def binary_representation(n):
    if n == 0:
        return "0"

    digits = []
    while n > 0:
        digits.append(str(n % 2))
        n = n // 2

    digits.reverse()  # остатки идут с конца, поэтому разворачиваем
    return "".join(digits)


print(binary_representation(10))  # 1010
print(binary_representation(0))   # 0
```

**Ответ:** Функция возвращает строку с двоичным представлением.

**Пример:** `binary_representation(10)` → `"1010"`, `binary_representation(0)` → `"0"`

---

## Задача 15

**Вопрос:** Напишите функцию `custom_round(number, ndigits)`, которая округляет число до `ndigits` знаков после запятой **без использования `round()`**.

**Подсказка:** Умножьте на `10**ndigits`, округлите через `int()`, разделите обратно.

**Решение:**

```python
def custom_round(number, ndigits):
    factor = 10 ** ndigits
    shifted = number * factor
    if shifted >= 0:
        shifted = int(shifted + 0.5)
    else:
        shifted = int(shifted - 0.5)
    return shifted / factor


print(custom_round(3.14159, 2))  # 3.14
print(custom_round(2.5, 0))      # 3.0
```

**Ответ:** Функция возвращает округлённое число.

**Пример:** `custom_round(3.14159, 2)` → `3.14`, `custom_round(2.5, 0)` → `3.0`

---

## Задача 16

**Вопрос:** Напишите функцию `find_max_min(numbers)`, которая возвращает кортеж `(max_value, min_value)` списка **без использования `max()` и `min()`**.

**Подсказка:** Пройдитесь по списку циклом.

**Решение:**

```python
def find_max_min(numbers):
    biggest = numbers[0]
    smallest = numbers[0]
    for num in numbers[1:]:
        if num > biggest:
            biggest = num
        elif num < smallest:
            smallest = num
    return (biggest, smallest)


print(find_max_min([3, 7, 1, 9, 2]))  # (9, 1)
```

**Ответ:** Функция возвращает кортеж из двух чисел.

**Пример:** `find_max_min([3, 7, 1, 9, 2])` → `(9, 1)`

---

## Задача 17

**Вопрос:** Напишите функцию `all_true(iterable)`, которая возвращает `True`, если все элементы «истинные», **без использования `all()`**.

**Подсказка:** Верните `False` при первом «ложном» элементе.

**Решение:**

```python
def all_true(iterable):
    result = True
    for item in iterable:
        if not item:
            result = False
            break
    return result


print(all_true([1, 2, 3]))  # True
print(all_true([1, 0, 3]))  # False
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `all_true([1, 2, 3])` → `True`, `all_true([1, 0, 3])` → `False`

---

## Задача 18

**Вопрос:** Напишите функцию `any_true(iterable)`, которая возвращает `True`, если хотя бы один элемент «истинный», **без использования `any()`**.

**Подсказка:** Верните `True` при первом «истинном» элементе.

**Решение:**

```python
def any_true(iterable):
    found = False
    for item in iterable:
        if item:
            found = True
            break
    return found


print(any_true([0, "", False]))  # False
print(any_true([0, 5, False]))   # True
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `any_true([0, "", False])` → `False`, `any_true([0, 5, False])` → `True`

---

## Задача 19

**Вопрос:** Напишите функцию `custom_enumerate(sequence, start=0)`, которая возвращает список кортежей `(index, element)`, **без использования `enumerate()`**.

**Подсказка:** Используйте счётчик в цикле.

**Решение:**

```python
def custom_enumerate(sequence, start=0):
    pairs = []
    for offset in range(len(sequence)):
        pairs.append((start + offset, sequence[offset]))
    return pairs


print(custom_enumerate(['a', 'b', 'c'], start=1))
# [(1, 'a'), (2, 'b'), (3, 'c')]
```

**Ответ:** Функция возвращает список кортежей.

**Пример:** `custom_enumerate(['a', 'b', 'c'], start=1)` → `[(1, 'a'), (2, 'b'), (3, 'c')]`

---

## Задача 20

**Вопрос:** Напишите функцию `custom_filter(func, iterable)`, которая возвращает список элементов, для которых `func(element)` возвращает `True`, **без использования `filter()`**.

**Подсказка:** Проверяйте каждый элемент в цикле.

**Решение:**

```python
def custom_filter(func, iterable):
    return [element for element in iterable if func(element)]


print(custom_filter(lambda x: x % 2 == 0, [1, 2, 3, 4, 5]))  # [2, 4]
```

**Ответ:** Функция возвращает список отфильтрованных элементов.

**Пример:** `custom_filter(lambda x: x % 2 == 0, [1, 2, 3, 4, 5])` → `[2, 4]`

---

## Задача 21

**Вопрос:** Напишите функцию `custom_map(func, iterable)`, которая применяет `func` к каждому элементу и возвращает список результатов, **без использования `map()`**.

**Подсказка:** Вызывайте функцию для каждого элемента.

**Решение:**

```python
def custom_map(func, iterable):
    return [func(element) for element in iterable]


print(custom_map(lambda x: x * 2, [1, 2, 3]))  # [2, 4, 6]
```

**Ответ:** Функция возвращает список преобразованных элементов.

**Пример:** `custom_map(lambda x: x * 2, [1, 2, 3])` → `[2, 4, 6]`

---

## Задача 22

**Вопрос:** Напишите функцию `custom_zip(list1, list2)`, которая возвращает список кортежей из пар элементов, **без использования `zip()`**.

**Подсказка:** Используйте `min(len(list1), len(list2))` для ограничения.

**Решение:**

```python
def custom_zip(list1, list2):
    limit = min(len(list1), len(list2))
    pairs = []
    i = 0
    while i < limit:
        pairs.append((list1[i], list2[i]))
        i += 1
    return pairs


print(custom_zip([1, 2, 3], ['a', 'b', 'c']))
# [(1, 'a'), (2, 'b'), (3, 'c')]
```

**Ответ:** Функция возвращает список кортежей.

**Пример:** `custom_zip([1, 2, 3], ['a', 'b', 'c'])` → `[(1, 'a'), (2, 'b'), (3, 'c')]`

---

## Задача 23

**Вопрос:** Напишите функцию `custom_reversed(sequence)`, которая возвращает развёрнутый список, **без использования `reversed()`** и срезов `[::-1]`.

**Подсказка:** Идите от конца к началу циклом.

**Решение:**

```python
def custom_reversed(sequence):
    result = []
    for item in sequence:
        result.insert(0, item)  # каждый новый элемент ставим в начало
    return result


print(custom_reversed([1, 2, 3, 4]))  # [4, 3, 2, 1]
```

**Ответ:** Функция возвращает развёрнутый список.

**Пример:** `custom_reversed([1, 2, 3, 4])` → `[4, 3, 2, 1]`

---

## Задача 24

**Вопрос:** Напишите функцию `custom_sorted(iterable, reverse=False)`, которая возвращает отсортированный список, **без использования `sorted()`** и `.sort()`.

**Подсказка:** Реализуйте простую сортировку пузырьком.

**Решение:**

```python
def custom_sorted(iterable, reverse=False):
    items = list(iterable)
    n = len(items)

    for i in range(n):
        for j in range(n - 1 - i):
            if reverse:
                should_swap = items[j] < items[j + 1]
            else:
                should_swap = items[j] > items[j + 1]

            if should_swap:
                items[j], items[j + 1] = items[j + 1], items[j]
    return items


print(custom_sorted([3, 1, 4, 1, 5]))          # [1, 1, 3, 4, 5]
print(custom_sorted([3, 1, 4], reverse=True))  # [4, 3, 1]
```

**Ответ:** Функция возвращает отсортированный список.

**Пример:** `custom_sorted([3, 1, 4, 1, 5])` → `[1, 1, 3, 4, 5]`, `custom_sorted([3, 1, 4], reverse=True)` → `[4, 3, 1]`

---

## Задача 25

**Вопрос:** Напишите функцию `sum_digits(n)`, которая возвращает сумму цифр числа, используя цикл `while`.

**Подсказка:** Извлекайте цифры через `% 10` и `// 10`.

**Решение:**

```python
def sum_digits(n):
    total = 0
    while n > 0:
        digit = n % 10
        total += digit
        n = n // 10
    return total


print(sum_digits(1234))  # 10
print(sum_digits(99))    # 18
```

**Ответ:** Функция возвращает сумму цифр (целое число).

**Пример:** `sum_digits(1234)` → `10`, `sum_digits(99)` → `18`

---

## Задача 26

**Вопрос:** Напишите функцию `count_vowels(text)`, которая подсчитывает количество гласных букв в строке (без учёта регистра).

**Подсказка:** Используйте строку `'aeiouAEIOU'` и цикл `for`.

**Решение:**

```python
def count_vowels(text):
    vowels = "aeiou"
    total = 0
    for letter in text.lower():
        if letter in vowels:
            total += 1
    return total


print(count_vowels("Hello World"))  # 3
print(count_vowels("Python"))       # 1
```

**Ответ:** Функция возвращает количество гласных (целое число).

**Пример:** `count_vowels("Hello World")` → `3`, `count_vowels("Python")` → `1`

---

## Задача 27

**Вопрос:** Напишите функцию `power(base, exp)`, которая возводит `base` в степень `exp`, **без использования `**` и `pow()`**, используя цикл.

**Подсказка:** Умножайте `base` на себя `exp` раз.

**Решение:**

```python
def power(base, exp):
    result = 1
    counter = 0
    while counter < exp:
        result = result * base
        counter += 1
    return result


print(power(2, 5))  # 32
print(power(3, 3))  # 27
```

**Ответ:** Функция возвращает результат возведения в степень (число).

**Пример:** `power(2, 5)` → `32`, `power(3, 3)` → `27`

---

## Задача 28

**Вопрос:** Напишите функцию `is_prime(n)`, которая проверяет, является ли число простым, используя цикл `for`.

**Подсказка:** Проверяйте делители от 2 до `sqrt(n)`.

**Решение:**

```python
import math


def is_prime(n):
    if n < 2:
        return False

    for divisor in range(2, int(math.sqrt(n)) + 1):
        if n % divisor == 0:
            return False
    return True


print(is_prime(17))  # True
print(is_prime(18))  # False
```

**Ответ:** Функция возвращает `True` или `False`.

**Пример:** `is_prime(17)` → `True`, `is_prime(18)` → `False`

---

## Задача 29

**Вопрос:** Напишите функцию `factorial(n)`, которая вычисляет факториал числа, используя цикл `for` или `while`.

**Подсказка:** `n! = 1 * 2 * 3 * ... * n`.

**Решение:**

```python
def factorial(n):
    result = 1
    while n > 1:
        result *= n
        n -= 1
    return result


print(factorial(5))  # 120
print(factorial(0))  # 1
```

**Ответ:** Функция возвращает факториал (целое число).

**Пример:** `factorial(5)` → `120`, `factorial(0)` → `1`

---

## Задача 30

**Вопрос:** Напишите функцию `fibonacci(n)`, которая возвращает n-е число Фибоначчи, используя цикл `for`.

**Подсказка:** Храните два предыдущих числа и обновляйте их.

**Решение:**

```python
def fibonacci(n):
    a = 0
    b = 1
    for _ in range(n):
        temp = a + b
        a = b
        b = temp
    return a


print(fibonacci(10))  # 55
print(fibonacci(0))   # 0
print(fibonacci(1))   # 1
```

**Ответ:** Функция возвращает n-е число Фибоначчи (целое число).

**Пример:** `fibonacci(10)` → `55`, `fibonacci(0)` → `0`, `fibonacci(1)` → `1`
