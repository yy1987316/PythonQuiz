# PythonQuiz

## 1.python合并字典，相同key的value相加
> ```python
> x = { 'apple': 1, 'banana': 2 }
> y = { 'banana': 10, 'pear': 11 }
> 需要把两个字典合并，最后输出结果是：
> { 'apple': 1, 'banana': 12, 'pear': 11 }
> ```

```python
from collections import Counter
dict(Counter(x) + Counter(y))
```
