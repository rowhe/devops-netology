#devops-netology
- Учебный репозиторий для курса DevOps-15

ДЗ 2.4  
***

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.
 - Полный хэш и комментарий этого коммита можно найти при помощи команды `git show aefea` или команды `git log aefea` - Хэш aefead2207ef7e2aa5dc81a34aedf0cad4c32545 и комментарий Update CHANGELOG.md.  
2. Какому тегу соответствует коммит `85024d3`?  
- При выполнение команды `git show 85024d3` можно увидеть тэг коммита - tag: v0.12.23
3. Сколько родителей у коммита `b8d720`? Напишите их хеши.  
- Родителей коммита b8d720 можно узнать командами - `git log --oneline b8d720^1` (первый родитель 56cd7859e) и `git log --oneline b8d720^2` (второй родитель 9ea88f22f). Также можно использовать команду `git log --graph b8d720, там мы наглядно увидим родителей коммита b8d720. И да, у коммита b8d720 два родителя ).
4. Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами  v0.12.23 и v0.12.24.  
- Вывести такой список коммитов с тегами и комментариями можно командой `git log --oneline v0.12.23^..v0.12.24`  
    33ff1c03b (tag: v0.12.24) v0.12.24
    b14b74c49 [Website] vmc provider links  
    3f235065b Update CHANGELOG.md  
    6ae64e247 registry: Fix panic when server is unreachable  
    5c619ca1b website: Remove links to the getting started guide's old location  
    06275647e Update CHANGELOG.md  
    d5f9411f5 command: Fix bug when using terraform login on Windows  
    4b6d06cc5 Update CHANGELOG.md  
    dd01a3507 Update CHANGELOG.md  
    225466bc3 Cleanup after v0.12.23 release
    85024d310 (tag: v0.12.23) v0.12.23
5. Найдите коммит в котором была создана функция `func providerSource`, ее определение в коде выглядит 
так `func providerSource(...)` (вместо троеточего перечислены аргументы).
- Самый первый коммит где упоминается функция `providerSource` можно найти командой `git log --oneline -SproviderSource`  
    Вот этот коммит - 5e06e39fc Use registry alias to fetch providers  
    Подробности о коммите можно узнать командой `git show 5e06e39fc`  
   
6. Найдите все коммиты в которых была изменена функция `globalPluginDirs`.  
- Сначала найдем файл содержащий определение функции `globalPluginDirs` при помощи `git grep -p "func globalPluginDirs("`.  
- Затем находим находим все коммиты содержащие изменение функции `globalPluginDirs` в файле plugins.so при помощи команды `git log -s -L :globalPluginDirs:plugins.go`
7. Кто автор функции `synchronizedWriters`?
- Проследить первое упоминание функции `synchronizedWriters` можно командой `git log -S"func synchronizedWriters(" --pretty="%h %an %ad" --reverse
`. Команда даст следующий вывод:  
    5ac311e2a Martin Atkins Wed May 3 16:25:41 2017 -0700  
    bdfea50cc James Bardin Mon Nov 30 18:02:04 2020 -0500
    Из даты и времени коммита можно сделать вывод, что автором функции является Martin Atkins
