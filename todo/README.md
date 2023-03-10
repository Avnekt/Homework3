### Django приложение `Todo list` список дел.

Данные хранятся в базе данных `db.sqlite3`. Модель данных содержит:
 - `taskName` имя задания - поле, в котором указывается, что нужно сделать;
 - `taskCreatedTime` дата и время создания задачи, проставляется автоматически при создании;
 - `taskCompleted` отметка о выполнении задачи;
 - `taskCompleteTime` дата и время завершения задачи, проставляется автоматически при установке флага о выполнении задачи.

Управление задачами осуществляется через *admin* сайт, а также через соответствующие *view*:
 * `todolist/` - просмотр имеющихся в базе задач;
 * `todoupdate/<int:pk>` - корректировка задачи с идентификатором *pk*;
 * `todocreate/` - создание задач;
 * `tododelete/<int:pk>` - удаление задачи с идентификатором *pk*;
 * `tododetail/<int:pk>` - детальный просмотр задач с идентификатором *pk*.

 Интерфейс `API` построен на `django rest framework` методы:
 * `GET` /api/tasks - получть список всех задач
 * `GET` /api/tasks/{id} - получть одну конкретную задачу
 * `POST` /api/tasks - создать задачу
 * `PUT` (или `PATCH`) /api/tasks/{id} - отредактировать существующую задачу
 * `DELETE` /api/tasks/{id} - удалить одну задачу

 Может быть использована фильтрация:
 * Поиска задачи по заголовку (запрос GET может быть дополнен query-параметром ?title=...)
 * Поиска активных\неактривных задач (запрос GET может быть дополнен query-параметром ?is_active=...)
 * Пагинация при GET-запросе (?page_size=)
 * Могут быть упорядочены результат GET - запроса (запрос GET может быть дополнен query-параметром ?ordering=...)
