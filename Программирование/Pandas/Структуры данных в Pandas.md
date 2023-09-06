
#Pandas 

**Pandas** использует две структуры для хранения информации: **Series** и **Data Frame**. Series является наследованием из одноименной структуры библиотеки [[Numpy]].

```jupyter
import numpy as np
import pandas as pd
```

---

# Series
Series это одномерная структура данных, которая может хранить различные типы: int, float, string etc. 
Создать экземпляр класса можно следующей командой:

```jupyter
s = pd.Series(data, index=index)
```

Где **data** может быть:
- Массивом Python
- Массивом Numpy
- Скаляром

**Index** есть список названий строк, по стандарту это есть численное представление. **Index** должен быть такой же длинны, что и **data**.

Так же можно создать Series из словаря следующим образом:

```jupyter
s = pd.Series(dict)
```

### Примеры

```jupyter
s_simple = pd.Series(5.0, index=["a", "b", "c", "d", "e", "f", "g"])
s_dict = pd.Series({
	"a": 5.0,
	"b": 5.0,
	"c": 5.0,
	"d": 5.0,
	"e": 5.0,
	"f": 5.0,
	"g": 5.0
})
```

---

## Series is ndarray-like
Series в Pandas действуют так же как ndarray в [[Numpy]], что позволяет работать с Series с функциями Numpy. Таким образом у Series наследовался параметр **dtype**:

```jupyter
s_simple.dtype
```

Так же мы можем привести Series к pandas array или numpy array:

```jupyter
s_simple.array
s_simple.to_numpy()
```

Соответственно мы можем индексироваться по Series:

```jupyter
s_simple[1]
s_simple[2:]
s_simple[[1, 3, 5]]
s_simple[s_simple > s_simple.median()]
```

---

## Series is dict-like
Series в Pandas так же работают как словари фиксированного значения, где возможна индексация и изменение по именам индексов.

```jupyter
s_simple["a"] = 5.1
s_simple.get("z", np.nan)
```

---

## Векторные операции над Series
Series поддерживают операции над своими экземплярами как обычные по типу сложения и вычитания, так и использование различных функций:

```jupyter
s = pd.Series([1, 2, 3, 4, 5], index=["A", "B", "C", "D", "E"])
```

```jupyter
s + s
```

```jupyter
s * 2
```

```jupyter
np.exp(s)
```

```jupyter
s[1:] + s[:-1]
```

---

## Name атрибут
У pandas series есть атрибут name, который в частности используемся в [[Структуры данных в Pandas#Data Frame|Data Frame]]

```jupyter
s = pd.Series([1, 2, 3, 4], name="something")
s
```

Атрибут name будет присвоен самостоятельно во многих случаях, например когда берутся первые срезы **Data Frame**, как мы увидим ниже.

Так же можно переименовать series, когда мы того захотим:

```jupyter
s2 = s.rename("different")
s2.name
```

Обратите внимание, что **s** и **s2** - различные экземпляры

---

# Data Frame
**Data Frame** это двухмерная структура данных, состоящая из столбцов и строк, которая, в отличие от Series, может содержать разные типы данных. Как и **Series** **Data Frame** имеет большое количество способов создания экземпляров, например:
- Словарь одномерных ndarray структур (List, array, dict etc)
- Двумерный [[Массив]]
- Ndarray
- Series
- Другая Data Frame

Приведем пару примеров:

```jupyter
df = pd.DataFrame([
	["Moscow", "10:30", "15"],
	["Saint-Petersburt", "19:45", "21"]
],
columns = ["City", "Time", "Number"]
)
```

```jupyter
d = {
    "one": pd.Series([1.0, 2.0, 3.0], index=["a", "b", "c"]),
    "two": pd.Series([1.0, 2.0, 3.0, 4.0], index=["a", "b", "c", "d"]),
}

df = pd.DataFrame(d)
```

```jupyter
data2 = [{"a": 1, "b": 2}, {"a": 5, "b": 10, "c": 20}]

pd.DataFrame(data2)
```