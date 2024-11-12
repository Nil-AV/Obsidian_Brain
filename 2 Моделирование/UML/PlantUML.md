
```
@startuml

actor User as U
participant Client as C
participant Server as WS
database DB as DB

autonumber

U -> C --++: Открывает страницу
C -> WS --++: GET /endpoint/
WS -> WS: Проверка формата данных
loop
WS -> : Проверка токена
end
WS <- : Успешная проверка
alt Некорректные данные
WS -> C: Code 400
end

WS -> DB --++: Получение данных
DB -> DB: Выборка данных

alt Успешный запрос
DB --> WS ++: Даннные найдены
WS --> C --++: Code 200
C --> U --: Получает данные
else Ошибка сервера
alt
DB --> WS: Даннные не найдены
else
DB --> WS --: Таймаут\n (время запроса превышено)
end
WS --> C --++: Code 500
C --> U --: Получает ошибку
end
@enduml
```

![[../../_Resours/XLFDRjD04BxlKymHL4Mj45mgX2eCuW5An8NBjjb39DUEx0tdnk4dKWwL45Ue12_WLgneJUk-mimRyNdi2ZkArCjwT-QRRxvl9Zd8lSty_2GsnXxxDADnxZAoEOtD38dfyNHc4qzHF7Nu81uDueSk-z3YtnsQYVNsoEQENhr412SuvpvDvYT7BZDcJACN5D5ejBEpJ_n32gxaLDPyoIK7AK.png]]