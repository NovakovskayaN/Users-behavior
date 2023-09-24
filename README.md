# Users behavior
Анализ поведения пользователей мобильной игры, которые зарегистрировались в 2018 году (с 1 января по 31 декабря 2018 года включительно). 

ЗАДАЧИ ПРОЕКТА:
    1. Определить, насколько обучение сокращает время прохождения этапов игры.
    2. Доказать, что успешное обучение само по себе влияет на оплату и не имеет значения то, каким этапом оно шло.
    3. Определить, насколько прозрачен процесс взаимодействия с игрой.

ФОРМАЛИЗОВАННЫЕ ЗАДАЧИ:
    1.	Сравнить время прохождения различных этапов для пользователей, которые завершили обучение, и пользователей, не начинавших обучение. Если показатель отличается, выяснить, насколько.
    2.	Проверить, существует ли зависимость между вероятностью оплаты вопросов и количеством обучений, которые начинал или завершал пользователь. 
    3.	Выяснить, как часто пользователи начинают обучение после выбора уровня сложности. (Это позволит оценить прозрачность процесса взаимодействия с игрой: если пользователи после выбора уровня сложности обращаются к обучению, значит, работа с приложением непонятна.)

КЛЮЧЕВЫЕ ЭТАПЫ ПУТИ ПОЛЬЗОВАТЕЛЯ:
    1.	Регистрация (registration) — это обязательный этап. Без регистрации пользователь не может пройти на следующие этапы работы с приложением.

    2.	Старт обучения (tutorial start) — опциональный этап. Пользователь после регистрации может перейти к обучению работе с приложением, а может и не перейти. При этом вернуться к обучению можно в любой момент. А ещё можно пройти обучение несколько раз.

    3.	Завершение обучения (tutorial finish) может произойти только в случае, если ранее произошло событие «Старт обучения», но при этом пользователь может не завершить обучение.

    4.	Выбор уровня сложности вопросов (level choice) — это обязательное событие, которое нужно для того, чтобы перейти к выбору пакетов вопросов. Таким образом, пользователь может не пройти обучение или даже не начинать его, но прежде чем начать отвечать, он обязан выбрать уровень сложности.

    5.	Выбор пакетов вопросов (pack choice, другое название training choice) — это этап, на котором пользователь выбирает себе бесплатный набор пакетов вопросов, на которые он будет отвечать.

    6.	Покупка платных пакетов вопросов (purchase) — это факт совершения оплаты за вопросы, которые не доступны в списке бесплатных вопросов.

ИСХОДНЫЕ ДАННЫЕ:

ТАБЛИЦА Event
    Хранит данные о событиях, которые совершают пользователи. По сути, каждое событие — это факт прохождения пользователем какого-либо этапа игры.
    
    - id	            идентификатор события
    - user_id	        уникальный идентификатор пользователя, совершившего событие в приложении
    - start_time	    дата и время события
    - event_type	    тип события (значения: registration — 
                        регистрация; tutorial_start — начало обучения; tutorial_finish — завершение обучения; level_choice — выбор уровня сложности; pack_choice — выбор пакетов вопросов)
    - tutorial_id	    идентификатор обучения (этот идентификатор есть 
                        только у событий обучения)
    - selected_level    выбранный уровень сложности обучения

ТАБЛИЦА purchase
    Хранит данные об оплатах, которые совершают пользователи.

    - id	            идентификатор события
    - user_id	        уникальный идентификатор пользователя, совершившего событие в приложении
    - event_datetime	дата и время события/покупки
    - amount	        сумма оплаты

