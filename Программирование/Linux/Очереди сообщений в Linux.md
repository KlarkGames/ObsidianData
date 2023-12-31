#Linux 

Очередь сообщений, или message queue, это структура, через которую процессы могут обмениваться структурированными сообщениями. Данные в очереди имеют следующие атрибуты:
- Тип сообщения
- Длина сообщения в байтах
- Собственно данные

Процессы могут считывать и записывать данные из разных mq. Процесс, отправивший сообщение в mq, может не дожидаться чтения его другим процессом.

В адресном пространстве ядра очередь сообщений хранится в виде [[Односвязный список|односвязного списка]]. В каждой очереди ядро **msgid_ds** создает заголовок с следующей информацией:
- **msg_perm** о правах доступа к очереди
- **msg_cbytes** о числе байтов и **msg_qnum** о числе сообщений в очереди
- **msg_first** и **msg_last** - указатели на первое и последнее сообщения.

![[Pasted image 20221107144133.png]]
Для того, чтобы поместить сообщение в очередь используется системный вызов **msgsend()**. Получить сообщение - **msgrcv()**. Управление сообщениями осуществляется за счет **msgctl()**.

Для создания message queue есть системные вызовы **msget()** и **msgctl()**