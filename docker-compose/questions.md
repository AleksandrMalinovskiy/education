1. Как можно указать в Doker-compose загрузку docker image в контейнер?
 <details>
  <summary>Ответ</summary>
  Прописать build: и указать путь до dockerfile. Docker соберет его.  
  Прописать image: и указать name image для скачивания из локального или общего регестри.  
</details>

2. Как опредилить или переопредилить аргументы в docker-compose?
<details>
  <summary>Ответ</summary>
Прописать environment: и аргумент например :\
 environment:\
      - POST_DATABASE_HOST=post_db\
      - POST_DATABASE=posts\
</details>

3. Как собрать контейнеры в одну сеть?
<details>
  <summary>Ответ</summary>
 Прописать networks: указав имя сети. Саму сеть необходимо определить вне описания service.\
 Например:\
 networks:\
  - front_net\
</details>

4. Как сохранить данные контейнера на сервер так что бы они не удалялись при удалении контейнера?
<details>
  <summary>Ответ</summary>
Прописать  volumes: можно сразу казать директорию на сервере : директория внутри контейнера, а можно прописать название volume и опредилите его все  service. Тогда место хранения будет в var/lib/docker/volume/\
Например:\
volumes:
  post_db:
</details>

5. Как открыть порт для контейнера запущенного через docker-compose?
<details>
  <summary>Ответ</summary>
Прописать ports: указав порт снаружи : порт внутри контейнера.\
Например:\
ports:\
- "5000:5000"\
</details> 

6. Как прописать запуск контейнера после одно из контейнеров ?
<details>
  <summary>Ответ</summary>
Прописать depends_on: и указать имя контейнера после которого надо запускать его.\
Например:\
 depends_on:\
  - post_db\
</details>

7. Как прописать в docker-compose выполнение команды после того как будет запущен контейнер ?
<details>
  <summary>Ответ</summary>
Прописав command: и указав комманду для выполнения.\
Например:\
command: ["node", "ace", "migration:run", "--force"]
</details>

8. Как прописать в docker-compose перезапуск контейнера в случае перезагрузки сервера ?
<details>
  <summary>Ответ</summary>
Прописать restart: always.\
</details>

9. Как указать env файл для контейнера в docker-compose ?
<details>
  <summary>Ответ</summary>
Прописать env_file: путь до env на сервере. \
Например:\
env_file:\
  - .env
</details>

10. Как указать в docker-compose размер общей памяти ( /dev/shmраздела в Linux), выделенной для сборки образа Docker?
<details>
  <summary>Ответ</summary>
Прописать в build: shm_size: 'размер памяти'\
Например:\
build:\
  shm_size: '2gb'
</details> 
