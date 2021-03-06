# Жизненный цикл разработки
Страница с описанием жизненного цикла разработки

<aside>
💡 Следуя правилам и рекомендациям, приведенным в этой странице ты сможешь сделать процесс разработки максимально понятным и простым для себя и всех членов команды
</aside>

---

## Типы задач
`Epic⛰` - крупные части проекта и инициативы
`Task🔨` - отдельные задачи, которые двигают разработку
`Bug🐞` - ошибки, которые нужно исправить или детали, которые нужно поменять или улучшить

## Новая задач
Чтобы взять новую задачу, следуй этим шагам:

1. Выбери задачу со статусом `Not Started` в Kanban Board или создай новую задачу
    
    Если есть множество задач, которые ты можешь взять, то выбирай ту, у которой выше приоритет
    
2. Создай ветку в репозитории с соответствующим тикетом. Если Тикет задачи имеет номер `1703`, то создай такую ветку:
    - Для задачи с типом `Bug🐞` создай ветку `bugfix/TIC-1703`
    - Для задачи с типом `Task🔨` создай ветку `feature/TIC-1703`
    - Для задачи с типом `Epic⛰` создай ветку `epic/TIC-1703`
    Если задача специфична или имеет лаконичное название, то его можно добавить в название ветки: `feature/TIC-1703-AccountSettings`
3. Заполни необходимые свойства у задачи (чем больше, тем лучше)
4. Присвой задаче статус `In Progress`
5. Обнови количество созданных тикетов, чтобы следующий разработчик не ошибся и не создал такой же тикет как и ты

## Система контроля версий
Прочитай как в организации устроена система контроля версий - [Github](https://github.com/Nephew-Ustas/Nephew-Ustas/blob/main/Pages/Github.md).

После того, как задача выполнена, проведены необходимые проверки (например, написаны и пройдены тесты), все изменения нужно добавить в ветку `dev`. Для этого создается **PR** (pull request), в который добавляются проверяющие.

После того, как **PR** будет принят, изменения попадают в общий проект. Теперь можно брать новую задачу!

## Первый запуск
1. Создай подпись для твоих проектов.
    1. Открой любой из уже созданных проектов в Xcode (или создай новый) и открой файл проекта.
    2. Узнай Bundle Identifier Prefix - это строка, которая находится перед названием проекта
        <img width="612" alt="Screenshot 2022-04-01 at 1 23 31 AM" src="https://user-images.githubusercontent.com/51203539/161159752-077cf6a0-a5ba-4c08-b0d4-d506a3c82bfe.png">
    3. Узнать идентификатор development_team: в файле проекта вкладка Build Settings -> поиск -> development_team -> нажать на <имя> (Personal Team) -> other
    4. Далее необходимо добавить эти данные в переменные окружения. Для этого выполни
        ```bash
        open ~/.zshrc || (touch ~/.zshrc && open ~/.zshrc)
        ```
    5. Добавь в файл строки
        ```bash
        # Environment variables for xcodegen:
        export BUNDLE_ID_PREFIX=nephew.ustas
        export DEVELOPMENT_TEAM=ABCDEFGH12
        ```
    6. Чтобы применить изменения, выполни
        ```bash
        source ~/.zshrc
        ```
2. Для начала нужно склонировать репозиторий
    
    ```bash
    git clone https://github.com/Nephew-Ustas/<Project>.git
    ```
    
3. После этого нужно перейти на ветку разработки - `dev`:
    
    ```bash
    git checkout dev
    ```
    
4. Затем необходимо перейти на нужную ветку (например `TIC-1703`):
    
    ```bash
    git checkout TIC-1703
    ```
    
    1. Если необходимо, то сначала создать новую ветку:
        
        ```bash
        git checkout -b TIC-1703
        ```

---

* ⚠️ *Пункты 3-4(i) можно сделать с помощью лишь одного скрипта из* `makefile`*:*

    ```bash
    make tic t=1703
    ```

---

5. После этого в директории проекта необходимо исполнить скрипт из `makefile`:
    
    ```bash
    make init
    ```
    
    или, чтобы сразу открыть проект:
    
    ```bash
    make run
    ```
    
    Для подробной информации о командах `makefile`-a вызвать
    
    ```bash
    make help
    ```
    
## Новая задача
1. Нужно убедится, что ты находишься на ветке `dev`:
    ```bash
    git checkout dev && git pull
    ```
2. Чтобы создать свою ветку используй (например `TIC-1703`)
    ```bash
    make tic t=1703
    ```
3. Теперь можно запускать
    ```bash
    make init
    ```
    или сразу
    ```bash
    make run
    ```
4. Для внесения изменений ветки в репозиторий вызвать
    
    ```bash
    make git t='title' b='body'
    ```
    
    - `title` - Заголовок коммита
    - `body` - Детальное описание коммита *(опционально)*
