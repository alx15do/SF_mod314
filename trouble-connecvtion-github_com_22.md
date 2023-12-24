## Решение проблемы "connect to host github.com port 22: Connection refused"

Данное решение действительно для ***ОС Линукс***. Для систем *Виндовс* или *Мак* не тестировалось.

Открыть для редактирования файл ***~/.ssh/config***, например:

```bash=
nano ~/.ssh/config
```
Добавить строки:

```bash=
Host github.com
Hostname ssh.github.com
Port 443
```

Закрыть файл, выполнить команду:

```bash=
ssh -T git@github.com
```

Если соединение не устанавливается, то проблема соединения в чем-то другом, например сетевом экране (брандмауэре). 

Иначе соединение должно быть установлено. Примерное сообщение которое появится:

```bash=
ssh -T git@github.com
The authenticity of host '[ssh.github.com]:443 ([140.82.121.35]:443)' can't be established.
ED25519 key fingerprint is SHA256:НаборРазныхЗнаков.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

> Из соображений безопасности вместо реального ключа ***SHA256*** указана строка: ***НаборРазныхЗнаков***

В этом случае необходимо подтвердить согласие на соединение и добавление ключа в список известных хостов:

```bash=
yes
```

Если всё прошло успешно, появится сообщение:

```bash=
Warning: Permanently added '[ssh.github.com]:443' (ED25519) to the list of known hosts.
Hi ИмяПользователя! You've successfully authenticated, but GitHub does not provide shell access.
```

---
---
> ### Воспроизведение проблемы:
> 
> При попытке клонирования удаленного репозитория на свой компьютер
> 
> ```bash=
> git clone git@github.com:ИмяПользователя/ИмяРепозитория.git
> ```
>
> появляется сообщение об ошибке:
> 
> ```bash=
> ssh: connect to host github.com port 22: Connection refused
> fatal: Не удалось прочитать из внешнего репозитория.
> 
> Удостоверьтесь, что у вас есть необходимые права доступа
> и репозиторий существует.
> ```
> 
---
[[Содержание]](./readme.md)