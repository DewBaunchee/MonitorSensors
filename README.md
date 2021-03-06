# Описание
Проект представляет собой хранилище записей о сохранённых сенсорах. Для просмотра записей необходима авторизация. 
Два предустановленных пользователя имеют различный набор прав. Администратор - способен изменять, добавлять и удалять записи. Пользователю разрешён только просмотр.
# Исходный код
Репозиторий: https://github.com/DewBaunchee/MonitorSensors. 
Репозиторий содержит в себе исходный код клиентской и серверной части.
# База данных
### Необходимо
- MySQL.
### Настройка
- создать базу данных ('CREATE DATABASE {name}; USE {name}');
- использовать в качестве источника 'initScript.sql', расположенного в 'server' ('source {path_to_script}').

# Сервер
### Необходимо
- системная переменная JAVA_HOME, которая указывает на местоположение JDK;
- установить нужные значения в 'server/src/main/resources/application.properties':
    - spring.datasource.url - адрес доступа к базе данных;
    - spring.datasource.username - имя пользователя в СУБД;
    - spring.datasource.password - пароль СУБД;
    - app.jwt.secret - секретный ключ (опционально);
    - app.jwt.token.lifetime.minutes - время жизни сеанса аутентификации в минутах (опционально).
- Maven.
### Запуск
- в консоли перейти в папку 'server' (должен содержать 'pom.xml');
- ввести команду 'mvn spring-boot:run'.
### Размещение
- в консоли перейти в папку 'server';
- ввести команду 'mvn clean install';
- итоговый .war архив будет находиться в папке 'target', название по умолчанию - 'monitor-sensors'. 

# Клиент
### Необходимо
- Angular CLI;
- веб-сервер.
### Размещение
- в файлах 'environment.ts' и 'environment.prod.tx' (папка 'src/environments') в поле 'apiAddress' установить
значение, соответствующее адресу сервиса. По умолчанию сервис будет использовать порт 8080. Если сервис запущен
на той же машине, что и сервер клиентского приложения, то адрес - localhost;
- выполнить команду 'npm install';
- выполнить команду 'ng build --prod --build-optimizer' (необходим Angular CLI);
- скопировать содержимое папки 'client/dist', в хранилище веб-сервера.

# Предуставновленные пользователи
1) Пользователь с ролью VIEWER (только просмотр):
    - username - user;
    - password - user;
2) Пользователь с ролью ADMINISTRATOR (возможность изменения):
    - username - admin;
    - password - admin;
