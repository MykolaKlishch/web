# stepik_web_project
Created while attending online course;
stepik web-project (https://stepik.org/lesson/14825/step/11?unit=4174)

# Task 1.8.12
    Отдача статических файлов

1) Установите Web-сервер nginx

2) В директории /home/box (домашняя директория) создайте следующую структуру директорий

        /home/box/web
                    |---public
                    |   |---img
                    |   |---css
                    |   |---js
                    |---uploads
                    |---etc

3) Настройте nginx так что бы:

    Все URL, начинающиеся с /uploads/  (например /uploads/1.jpeg) отдавались из директории /home/box/web/uploads
    Все URL с расширением (например /img/1.jpeg) отдавались из директории /home/box/web/public
    Все URL без расширения (например /question/123)  возвращали HTTP 404

4) Фрагмент конфига nginx который обслуживает ваш проект должен находиться в файле /home/box/web/etc/nginx.conf [/home/box/web/etc/nginx1812.conf] и должен быть включен в основной конфиг [/etc/nginx/sites-enabled/default] с помощью символической ссылки [sudo ln -sf /home/box/web/etc/nginx1812.conf  /etc/nginx/sites-enabled/default].

5) Запустите nginx, так что бы он принимал запросы на порту 80 и обслуживал бы любые домены.

6) Не забудьте закомитить и сохранить на github полученную структуру директорий и конфиги.
------------------------------------------------------------------------------------------------
# Task 1.8.12
    Запуск WSGI приложений

1) Разверните репозиторий со своим проектом в директориию /home/box/web

2) Создайте WSGI приложение в файле /home/box/web/hello.py

WSGI приложение должно возвращать документ с MIME-типом text/plain, содержащий все GET параметры, по одному на каждую строку.

Например при запросе  /?a=1&a=2&b=3 приложение должно вернуть такой текст

a=1
a=2
b=3

3) Настройте Gunicorn таким образом, что бы он запускал приложение  /home/box/web/hello.py , и принимал соединения на IP адресе 0.0.0.0 на порту 8080 .  (Использования IP = 0.0.0.0 необходимо для тестирования). Конфиг разместить в файле [/home/box/etc/gunicorn_conf.py] и подключите его с помощью символической ссылки [sudo ln -sf /home/box/web/etc/gunicorn_conf.py /etc/gunicorn.d/gunicorn_conf]

4) Настройте nginx так что бы location /hello/ проксировался на cервер Guincorn

Таким образом, WSGI приложение должно быть доступно по URL

    http://127.0.0.1/hello/
    http://127.0.0.1:8080/

------------------------------------------------------------------------------------------------
