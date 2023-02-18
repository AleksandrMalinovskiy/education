<details>
  <summary>Ответ</summary>
 
</details>

1. Что такое redis ?
<details>
  <summary>Ответ</summary>
 Redis — резидентная система управления базами данных класса NoSQL с открытым исходным кодом, работающая со структурами данных типа «ключ — значение». Используется как для баз данных, так и для реализации кэшей, брокеров сообщений. Ориентирована на достижение максимальной производительности на атомарных операциях. 
</details>

3. Что такое ключи в redis?
<details>
  <summary>Ответ</summary>
Ключи в Redis являются уникальными идентификаторами значений, которые связаны с ними. Значения могут быть различными: целочисленными, строковыми и даже объектами, содержащими другие вложенные значения. Ключи же используются в качестве указателей, обозначающих место хранения данных. Здесь уместно провести аналогию со шкафчиками в магазине, куда покупатели временно складывают вещи. Значение — то, что лежит в этом шкафчике, а доступ к нему осуществляется по ключу с номером.
</details>

3. Что такое строки в redis?
<details>
  <summary>Ответ</summary>
 Строка (string) является базовым типом данных, который содержит в себе все остальные данные. Строки в «Редис» по своим функциям аналогичны строкам в языках программирования. Максимально допустимый размер строки в Redis — 512 МБ.
</details>

4. Что такое списки в redis?
<details>
  <summary>Ответ</summary>
 Список (list) представляет собой последовательности значений, которые располагаются в списке в порядке создания. Чтобы создать список, познакомимся с некоторыми командами. LPUSH добавляет элемент, а LRANGE используется для вывода списка слева.

 LPUSH obj1 element1

(integer) 1

LPUSH obj1 element2

(integer) 2

LPUSH obj1 element3

(integer) 3

LRANGE obj1 0 -1

И получаем следующий вывод:

1) "element3"

2) "element2"

3) "element1"

</details>

5. Что такое хеши в redis?
<details>
  <summary>Ответ</summary>
Суть хешей (hash) или хеш-таблиц будет сразу понятна тем, кто программировал на Python или JavaScript. В Python очень похожими на хеши являются словари, а в JavaScript — объекты. Чтобы записать значение в хеш, в Redis есть команда HSET, а для чтения используется HGET. 

Пример:

HSET obj att1 val1

(integer) 1

HSET obj att2 val2

(integer) 1

HGET obj att1

"val1"

Если же нужно получить все значения, применяем инструкцию HGETALL:

HGETALL obj

1) "att1"

2) "val1"

3) "att2"

4) "val2"

</details>

6. Что такое множества в redis?
<details>
  <summary>Ответ</summary>
Под множеством (set) в «Редис» понимают неупорядоченную коллекцию уникальных элементов. Чтобы добавить туда очередной элемент, введем команду SADD:

SADD objects object1

(integer) 1

SADD objects object2

(integer) 1

SADD objects object3

(integer) 1

SADD objects object1

(integer) 0

Теперь, чтобы получить все элементы, нужно ввести инструкцию SMEMBERS:

SMEMBERS objects

1) "object2"

2) "object3"

3) "object1"

</details>

7. Что такое упорядоченные множества в redis?
<details>
  <summary>Ответ</summary>
Чтобы добавить элемент в упорядоченное множество (sorted set), используют команду ZADD:

ZADD objects 1230 val1

(integer) 1

ZADD objects 1231 val2

(integer) 1

ZADD objects 1232 val3

(integer) 1

Теперь с помощью инструкции ZRANGE получаем срез:

ZRANGE objects 0 -1

1) "val1"

2) "val2"

3) "val3"

</details>

8. Что такое кэширование в redis?
<details>
  <summary>Ответ</summary>
Одной из задач, которые решает Redis, является эффективное кэширование данных. В этом случае он часто работает вместе с реляционными СУБД, например, PostgreSQL. Кэширование позволяет быстро загружать небольшие объекты, которые часто обновляются, и при этом минимизирует риск потерь информации. Redis служит буферной СУБД и, в ответ на запрос пользователя, выполняет проверку по ключу, не затрагивая основную БД. Это в разы снижает нагрузку на ресурсы с высокой посещаемостью (от нескольких тысяч пользователей в час). 
</details>

9. Как получить информацию о redis?
<details>
  <summary>Ответ</summary>
Команда redis-cli -c -h ip -p port -a [ACCESSKEY] info
</details>

10. Как настроить аунтефикацию в redis?
<details>
  <summary>Ответ</summary>
В конфиг файле redis прописать  requirepass пароль 
</details>

11. Как настроить аунтефикацию в redis для мастера при репликации мастер слэйв ?
<details>
  <summary>Ответ</summary>
В конфиг файле redis прописать masterauth пароль
</details>

12. Как проверить статус репликации на одном из серверов redis?
<details>
  <summary>Ответ</summary>
Команда redis-cli -a пароль info replication
</details>

13. Как прописать ключь значение и прочитать его? 
<details>
  <summary>Ответ</summary>
Команда set для того что бы прописать и get для того что бы получить  
</details>

14. Как создать репликацию redis master slave?
<details>
  <summary>Ответ</summary>
На мастер :

- bind ip
- replica-read-only yes
- requirepass  пароль
- masterauth пароль

На славе:

- bind ip
- replica-read-only yes
- requirepass  пароль
- masterauth пароль
- replicaof ipmaster port
</details> 

15. Как настроить автоматическую смену роли в репликации redis ?
<details>
  <summary>Ответ</summary>
Для автоматической смены роли сервера необходимо установить и настроить redis-sentinel. 

На каждом сервере в директории etc/redis/ прописать sentinel.conf со следующим содержанием:

sentinel monitor mymaster ipmaster port 2

sentinel down-after-milliseconds mymaster 60000

sentinel failover-timeout mymaster 60000

sentinel auth-pass mymaster пароль

sentinel parallel-syncs mymaster 1
</details>

16.  Как получить информацию о состоянии redis-sentinel?
<details>
  <summary>Ответ</summary>
Команда redis-cli -p port-sentinel info sentinel
</details>

17. Как при репликации redis мастер слэйв дать разрешение на запись в слайв?
<details>
  <summary>Ответ</summary>
Команда slaveof no one переведет реплику в мастер изапись будет разрешенна. При этом репликации уже не будет.  
</details>

18. Как создать клсатер в redis?
<details>
  <summary>Ответ</summary>
Команда redis-cli --cluster create ip1:port  ip2:port  ip3:port  ip4:port ip5:port ip6:port  --cluster-replicas 1.

Первые 3 адреса — это главные узлы, а следующие 3 адреса — это узлы-реплики. Аргумент --cluster-replicas 1указывает, что у каждого мастера будет 1 реплика.
</details>

19. Как посмотреть состояние кластера redis?
<details>
  <summary>Ответ</summary>
Команда redis-cli -c -h ip -p port -a [ACCESSKEY] CLUSTER NODES
</details>

20. Как добавить новый узел в кластер redis ?
<details>
  <summary>Ответ</summary>
Команда redis-cli --cluster add-node ipmaster:port добавит главный процесс текущего нового сервера в кластер.

Команда redis-cli --cluster reshard ip:port выполнит перераспределение кластера, чтобы равномерно перераспределить слоты ключей между всеми главными процессами кластера Redis, включая новые главные процессы.

Команда redis-cli --cluster add-node ipslave:port ipmaster:port --cluster-slave --cluster-master-id [MASTER_NODE_ID] добавит процесс реплики нового сервера в кластер Redis
</details>

21. Как удалить ноду из кластера redis?
<details>
  <summary>Ответ</summary>
 redis-cli --cluster del-node ip:port `<node-id>`
</details>

22. Как проверить работоспособность кластера redis?
<details>
  <summary>Ответ</summary>
redis-cli --cluster check ip:port
</details>

