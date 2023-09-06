#Data_Science 

AUC-ROC (Area Under Curve, Receiver Operating Characteristic curve) есть мера того, как хорошо работает алгоритм классификации. Определяется он величиной площади под графиком. График лежит в квадрате между (0, 0) и (1, 1). Осями графика служат следующие величины: True Positive Rate и False Positive Rate. Определяются они следующим образом:

$$\text{TPR} = \frac{\text{tp}}{\text{tp}+\text{fn}}$$
$$\text{FPR} = \frac{\text{fp}}{\text{fp}+\text{tn}}$$
Лучшим результатом является 1, если вывод равен 0,5 то алгоритм не лучше рандома.
Пример такой кривой приведен ниже.
![[Pasted image 20220831153005.png]]