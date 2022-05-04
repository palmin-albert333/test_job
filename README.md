## Тестовое задание

Реализовать систему деплоя движка wordpress.org средствами ansible и docker:
- под деплоем небоходимо понимать ansible роль или плейбук, которая будет уметь зарворачивать новую версию движка на заданном хосте
- окружение должно состоятиь из docker контейнеров
-- nginx
-- php-fpm
-- mysql
- в окружении дложен быть предусмотрен механизм сохранения статических данных
-- данные базы mysql
-- статические данные движка: wp-config.php и /uploads/
-- файлы/папки движка: wp-config.php и /uploads/
-- конфиг виртуального хоста nginx

ps устанавливать на целевом хосте docker/docker-compose не нужно, будем считать что при проверке он там уже установлен

пара уточнений:

1. деплой движка: стоит понимать как выкатка какого-то софта с его репозитория в новую папку релизов на площадке
2. движок wordpress - абсолютно не обязательное условие; можно взять какой-то другой с которым знаком, но желательно чтобы у него была как минимум какая-то БД

-----------------------------------------------------------------------------------------------
## Что выполнено

1) плейбук ansible, реализующий деплой движка wordpress на целевую машину с помощью docker-compose;
2) шаблонизатор jinja не использовал, так как всего один файл конфига;
3) статические данные движка и конфиг nginx сохраняются;
4) используется субд MYSQL;
5) переменные добавлены в .gitignore. Пароль su от сервера скрыт с помощью ansible vault;
6) в директории /roles/deploy/vars/ пример использованных переменных;
7) запустить плэйбук: ansible-playbook deploy.yml.
