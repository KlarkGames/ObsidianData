#Linux 

Разделяемая память представляет собой наиболее быстрый способ обмена данными между независимыми процессами.

С помощью разделяемой памяти различные процессы могут отображать данные в РП в различные участки своего адресного пространства.

![[Pasted image 20221107150158.png]]
По окончании коммуникации через сегмент общей памяти, обычно процесс владелец отвечает за удаление этого сегмента. При этом эти полномочия могут быть делегированы другому процессу.

Ограничения для сегмента разделяемой памяти:
- Максимальный размер сегмента: 1.048.576 Байт
- Минимальный размер сегмента: 1 Байт
- Максимальное число сегментов с системе: 100
- Максимальное число сегментов связанных с процессом: 6

Для создания разделяемой памяти есть системные вызовы **shmget()** и **shmctl()**