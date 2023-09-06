#Data_Science 

Boosting есть подход к построению алгоритмов, где каждая последующая модель направленна на то, чтобы компенсировать ошибки предыдущих моделей. Результат выбирается с помощью взвешенного среднего.

$$a(\mathbf{x})=\sum\limits_{i=0}^{n}c_{i}a_{i}(\mathbf{x})$$
Для примера возьмем задачу классификации с помощью [[Градиентный спуск|градиентного спуска]].

Зададим [[Функция невязки|функцию невязки]]:

$$L(a(\mathbf{x})) = (a(\mathbf{x}) - y_{true})^{2}$$

Допустим мы обучили уже некоторое количество алгоритмов $a_{1}, a_{2}, \dots, a_{n}$ и хотим построить алгоритм $a_{n+1}$ так, чтобы он компенсировал ошибку предыдущих итераций.

Соответственно определяем $a(\mathbf{x}) = \sum\limits_{i}^{n}c_{i}a_{i}(\mathbf{x})$.
Из [[Градиентный спуск|метода градиентного спуска]] знаем, что если взять [[Градиент|градиент]] от функции невязки и отнять его с некоторым шагом $\alpha$ можно приблизится к локальному минимуму функции невязки. Соответственно делаем вывод, что:

$$a_{n+1}(\mathbf{x}) = -\text{grad}(L(\mathbf{x})|_{a(\mathbf{x}) = \sum\limits_{i=0}^{n}c_{i}a_{i}(\mathbf{x})})$$
Соответственно для нашей функции невязки получаем:

$$a_{n+1}(\mathbf{x}) = -2(\sum\limits_{i=0}^{n}c_{i}a_{i}(\mathbf{x}) - Y_{true})$$
Дальше алгоритм $a_{n+1}$ подбирается так, чтобы он удовлетворял полученному целевому числу $-2(\sum\limits_{i=0}^{n}c_{i}a_{i}(\mathbf{x}) - Y_{true})$.
