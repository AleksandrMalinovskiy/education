1. Как найти файл на серевере с определленой строкой ? 
<details>
  <summary>Ответ</summary>
grep -r -n строка / 
</details>

2. Как удалить сроку из файла начинающуюся с name ?
<details>
  <summary>Ответ</summary>
 sed '/"name"/d'
</details> 

3. Как сделать перенос строки после символа?
<details>
  <summary>Ответ</summary>
 Перенос строки после [
tr "[" "\n"
</details>

4.  Как удалить символ " из файла  ?
<details>
  <summary>Ответ</summary>
sed 's/"//g'
</details>

5. Как удалить все после части строки name ? 
<details>
  <summary>Ответ</summary>
 sed -r 's/ name .+//'
</details>

6. Как заменить слова name в строках ?
<details>
  <summary>Ответ</summary>
 sed -r 's|name .| Test |'
</details>

7. Как вывести первые 50 строк в файле ? 
<details>
  <summary>Ответ</summary>
head -50 namefile 
</details>

7. Как вывести последние 50 строк в файле ?
<details>
  <summary>Ответ</summary>
tail -50 namefile 
</details>

8. Как открыть файл и лестать его построчно ? 
<details>
  <summary>Ответ</summary>
less namefi 
</details>

9. Как посчитать строки в файле ? 
<details>
  <summary>Ответ</summary>
cat namefile | wc -l 
</details>

10. Как сменить пользователя и группу у файла? 
<details>
  <summary>Ответ</summary>
chown new-name:new-grup namefile. 
Если папка с файлами то 
chown -R  new-name:new-grup namedir
</details>

11. Как сменить разрешение на файл ? 
<details>
  <summary>Ответ</summary>
chmod 765 namefile. 
Если папка с файлами то
chmod -R 765 namedir. 


Расшифровка 


-rwxrw-r-x alex admins namefile


7 - чтение запись и выполнение для пользователя alex


6 - чтение и запись для группы admins


5 - чтение и выполнение для остальных пользователей


---------
0 - никаких прав;


1 - только выполнение;


2 - только запись;


3 - выполнение и запись;


4 -  только чтение;


5 - чтение и выполнение;


6 - чтение и запись;


7 - чтение запись и выполнение.


-rwxrw-r-x alex admins namefile

u - владелец файла;

g - группа файла;

o - все остальные пользователи

r - чтение;


w - запись;


x - выполнение;


s - выполнение  от имени суперпользователя (дополнительный);
</details>

12. Как найти файл на сервере по названию?
<details>
  <summary>Ответ</summary>
Find  директория -iname название файла
</details>

13. Как узнать дату последнего изменения файла на Linux
<details>
  <summary>Ответ</summary>
stat filename или если нужна только дата stat -c ‘%y’ filename
</details>

15. Как создать нового пользователя пароль и группу для него?
<details>
  <summary>Ответ</summary>
useradd username - новый пользователь

passwd username - пароль для него 

groupadd name - группа для него

useradd -m username - создать домашнюю директорию для пользователя
</details>

16. Как добавить пользователя в группу ?
<details>
  <summary>Ответ</summary>
usermod -a -G groupname username

Например, чтобы добавить пользователя linuxize в группу sudo , вы должны выполнить следующую команду:

sudo usermod -a -G sudo username
</details>

17. Как посмотреть окрытые порты на сервере ?
<details>
  <summary>Ответ</summary>
ss -ntlp 
</details>

18. Как посомтреть открыт ли порт на удаленном сервере ? 
<details>
  <summary>Ответ</summary>
telnet IP PORT 
nmap IP -p PORT 

</details>

19. Как из линукс тачки сделать роутер?
20. Как посмотреть таблицу маршрутизации?
21. Как посмотреть правила FW ?
22. Чем роутер отличается от свича?
23. Чем trunck отличается от access?
24. Как настроить удаленное подключение во внутреннюю сеть компании?
25. Что такое демон в линукс и зачем нужен?
26. Как посмотреть все запущенные сервисы?
27. Названить пакетные менеджеры для deb/rpm систем
28. Зачем нужны пакетные менеджеры?
29. Как добавить новый репозиторий в линукс?