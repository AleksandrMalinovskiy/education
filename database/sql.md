<details>
  <summary>Ответ</summary>
 
</details>

1. Как создать базу данных? 
<details>
  <summary>Ответ</summary>
create databse namedb;
</details>

2. Как создать юзера? 
<details>
  <summary>Ответ</summary>
CREATE USER nameuser WITH PASSWORD 'Password';
</details>

3. Как назначить права юзеру на использование базы данных?
<details>
  <summary>Ответ</summary>
Даем права на базу командой:

GRANT ALL PRIVILEGES ON DATABASE "dbname" to user;

Теперь подключаемся к базе, к которой хотим дать доступ:

\c dbname;

а) Так мы добавим все права на использование всех таблиц в базе учетной записи:

GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO "username";

б) Также можно дать доступ к базе для определенных таблиц:

GRANT ALL PRIVILEGES ON TABLE nameTable IN SCHEMA public TO "username";

</details>

4. Как сменить пароль юзеру? 
<details>
  <summary>Ответ</summary>
ALTER USER postgres PASSWORD 'password'
</details>

5. Как удалить пользователя ? 
<details>
  <summary>Ответ</summary>
Удаление пользователя выполняется следующей командой:

DROP USER dmosk;

Забрать права:

REVOKE ALL PRIVILEGES ON ALL TABLES IN SCHEMA public FROM "dmosk";
</details>
