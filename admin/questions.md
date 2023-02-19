1. Как найти файл на серевере с определленой строкой ? 
<details>
  <summary>Ответ</summary>
grep строка / 
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