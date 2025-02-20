## **📘 What is Typing in Python?**
Typing in Python refers to the way Python handles **data types** and **type hints**.

---

## **1️⃣ Dynamic Typing (Default in Python)**
Python is **dynamically typed**, meaning:
- You **don’t have to declare** a variable's type.
- A variable’s type can **change** at runtime.

### ✅ **Example (Dynamic Typing)**
```python
x = 10     # x is an integer
x = "Hello"  # Now x is a string (allowed in Python)
```

🔹 **Downside:** No type checking at compile time, which can lead to bugs.

---

## **2️⃣ Static Typing with Type Hints (Optional)**
To improve code reliability, Python allows **type hints** using the `typing` module.

### ✅ **Example (Using Type Hints)**
```python
def add(x: int, y: int) -> int:
    return x + y
```
- `x: int, y: int` → Parameters should be **integers**.
- `-> int` → The function **returns an integer**.

⚡ **Key Benefits:**
- **Catches errors early** (with tools like `mypy`).
- **Improves readability**.
- **Helps IDEs with autocompletion**.

---

## **3️⃣ Common Type Hinting Features**
### ✅ **Basic Types**
```python
age: int = 25
name: str = "Alice"
pi: float = 3.14
is_active: bool = True
```

---

### ✅ **Lists, Tuples, Dicts**
```python
from typing import List, Tuple, Dict

numbers: List[int] = [1, 2, 3]
point: Tuple[float, float] = (2.5, 3.8)
person: Dict[str, int] = {"Alice": 30, "Bob": 25}
```

---

### ✅ **Optional Types (Can Be `None`)**
```python
from typing import Optional

def get_name(user_id: int) -> Optional[str]:
    return "Alice" if user_id == 1 else None
```
- `Optional[str]` → The function can return a `str` **or** `None`.

---

### ✅ **Union (Multiple Possible Types)**
```python
from typing import Union

def process(value: Union[int, float]) -> float:
    return float(value) * 2
```
- `Union[int, float]` → The function accepts **both** `int` and `float`.

---

### ✅ **Callable (Function as Argument)**
```python
from typing import Callable

def execute(fn: Callable[[int, int], int], a: int, b: int) -> int:
    return fn(a, b)

def add(x: int, y: int) -> int:
    return x + y

print(execute(add, 2, 3))  # Output: 5
```
- `Callable[[int, int], int]` → A function that takes two `int` and returns an `int`.

---

## **4️⃣ Advanced Typing (Since Python 3.9 & 3.10)**
Python 3.9+ introduced **simpler syntax** for type hints.

### ✅ **Before (Python 3.8 and earlier)**
```python
from typing import List, Dict

numbers: List[int] = [1, 2, 3]
data: Dict[str, int] = {"Alice": 30}
```

### ✅ **Now (Python 3.9+)**
```python
numbers: list[int] = [1, 2, 3]
data: dict[str, int] = {"Alice": 30}
```

### ✅ **Python 3.10+: Union `|` instead of `Union`**
```python
def process(value: int | float) -> float:
    return float(value) * 2
```

---

## **5️⃣ Summary**
✅ **Typing in Python can be dynamic or static** (via type hints).  
✅ **Type hints improve code clarity and help catch errors early.**  
✅ **Use `typing` module for complex type definitions.**  
✅ **Newer Python versions make typing syntax simpler!**

