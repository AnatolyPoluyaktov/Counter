# Counter 

веб приложение, которое изменяет значения счетчика пользователя от вызова CRUD методов.
- POST /count (с acсess токеном) - увеличит счетчик на один
- GET /count  (с access токеном) вернет значение текущее значение счетчика
- DELETE /count (с access токеном) - уменьшит счетчик на один
- POST /login с  c логином и паролем - вернет refresh и access токен
- POST /token/refresh/ ( refresh токеном) - вернет новые refresh и access токен

Аутентификация проходит по JWT токену

# Ответы на вопросы

### как обратывать ошибки и невалидные данные?
   
1. Если мы вызовем методом login с неправильным логином и паролем, мы получим  ответ в виде json:

  ``` detail": "No active account found with the given credentials" ```

2.Если мы попробуем обратиться к CRUD методам c невалидными данными, то получаем:
 ``` authentication credentials were not provided. ```

3. Если предоставим токен, но будет не валидный:

 ```  Token is invalid or expired ```

4. Как было предположено по условию, счетчик не должен быть меньше 0. В этом случае, если пользователь попытается сделать счетчик отрицательным, то счетчик всегда будет оставаться нулем, пока пользователь не захочет увеличить счетчик

### Инструкция по разворачиванию веб сервера

Перед начало нужно именить на хосте установленные docker и docker-compose:

1. ``` git clone git@github.com:AnatolyPoluyaktov/Counter.git ```
2. ``` docker-compose up -d ```
3. ``` docker exec -it <container_id>  python manage.py createsuperuser ``` (создаем админа)

### Анализ покрытия 

![изображение](https://user-images.githubusercontent.com/41837845/132144500-a8643b67-8052-4605-8510-23a67f2a785f.png)

