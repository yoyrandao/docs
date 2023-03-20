# Мониторинг состояния Spark-приложений

Чтобы оценить работу Spark-приложений в кластере {{ dataproc-name }}, вы можете проверить:

* [список приложений](#list);
* [логи приложения](#logs);
* [очередь выполнения приложений](#queue);
* [подробную информацию о приложении](#info);
* [выделенные для приложения ресурсы](#resources);
* [кешируемые таблицы](#tables);
* [список и планы SQL-запросов](#sql).

{% note info %}

Убедитесь, что в кластере включены [веб-интерфейсы компонентов](../concepts/interfaces.md). При необходимости, [включите их](./connect-interfaces.md#ui-proxy-enable).

{% endnote %}

## Проверить список приложений {#list}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** перейдите в интерфейс **YARN Resource Manager Web UI**.

Здесь представлена информация обо всех работающих и завершенных приложениях.

## Проверить логи приложения {#logs}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** выберите интерфейс **YARN Resource Manager Web UI**.
1. Найдите нужное приложение и нажмите на его идентификатор в столбце **ID**.

    Откроется окно с информацией о работе приложения и таблицей со списком попыток запуска приложения.

1. Нажмите на ссылку в столбце **Logs** напротив нужной попытки.

## Проверить очередь выполнения приложений {#queue}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** выберите интерфейс **YARN Resource Manager Web UI**.
1. В левом меню перейдите в раздел **Scheduler**.

В разделе **Application Queues** графически представлена очередь выполнения приложений и занимаемые ими ресурсы.

## Проверить подробную информацию о приложении {#info}

{% list tabs %}

* YARN Resource Manager Web UI

    1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера.
    1. В блоке **UI Proxy** выберите интерфейс **YARN Resource Manager Web UI**.
    1. Найдите нужное приложение и перейдите по ссылке в столбце **Tracking UI**. Название ссылки зависит от статуса приложения:

        * **ApplicationMaster** — для запущенных приложений;
        * **History** — для завершенных приложений.

* Spark History Server Web UI

    1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера.
    1. В блоке **UI Proxy** выберите интерфейс **Spark History Server Web UI**.

        Откроется список завершенных приложений. Чтобы перейти к списку запущенных приложений, внизу таблицы нажмите **Show incomplete applications**.

    1. Найдите нужное приложение и перейдите по ссылке в столбце **App ID**.

{% endlist %}

Откроется окно интерфейса **Spark History Server Web UI** с подробной информацией о выбранном приложении:

* **Event Timeline** — история выполнения заданий с отметками о выделении и освобождении [исполнителей](../concepts/spark-sql.md#tasks) (executors).
* **Active Jobs** — список заданий, которые выполняются, либо ожидают начала выполнения.
* **Completed Jobs** — список завершенных заданий.

Для каждого задания в таблице указаны:

* время запуска (**Submitted**);
* продолжительность выполнения (**Duration**);
* количество стадий — завершенных/всего (**Stages: Succeeded/Total**);
* количество операций — завершенных/всего (**Tasks: Succeeded/Total**).

## Проверить выделенные для приложения ресурсы {#resources}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** выберите интерфейс **Spark History Server Web UI**.
1. В верхнем меню перейдите в раздел **Executors**.

В интерфейсе представлено две таблицы:

* **Summary** — обобщенная информация о количестве и состоянии [исполнителей](../concepts/spark-sql.md#tasks) и используемых ресурсах.
* **Executors** — информация по каждому исполнителю.

В таблицах приведено:

* количество доступных для каждого исполнителя ресурсов;
* количество выполняемых и завершенных [операций](../concepts/spark-sql.md#tasks) (tasks);
* продолжительность выполнения задачи (**Task Time**) с указанием времени, затраченного на сборку мусора (**GC Time**).

{% note tip %}

Если сборка мусора занимает много времени:

{% include [gc-time-fix](../../_includes/data-proc/gc-time-fix.md) %}

{% endnote %}

## Проверить кешируемые таблицы {#tables}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** выберите интерфейс **Spark History Server Web UI**.
1. В верхнем меню перейдите в раздел **Storage**.

В интерфейсе представлен список кешируемых таблиц ([RDDs](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds)). Для каждой таблицы приведена информация об используемой оперативной памяти и занимаемом дисковом пространстве, а также прогресс кеширования.

Чтобы посмотреть детальную статистику, нажмите на имя таблицы.

## Проверить список и планы SQL-запросов {#sql}

1. Перейдите на [страницу каталога]({{ link-console-main }}) и выберите сервис **{{ dataproc-name }}**.
1. Нажмите на имя нужного кластера.
1. В блоке **UI Proxy** выберите интерфейс **Spark History Server Web UI**.
1. В верхнем меню перейдите в раздел **SQL**.

В таблице представлен список выполненных SQL-запросов с информацией о времени запуска и продолжительности их выполнения.

Чтобы получить план выполнения запроса, нажмите на текст запроса в столбце **Description**. План выполнения представлен в виде схемы. Чтобы увидеть текстовый вариант плана, нажмите **Details** в нижней части рисунка.

На плане запроса приведена статистика для каждого оператора, которая отражает количество завершенных операций (tasks) и продолжительность их выполнения. Если запрос еще выполняется, отобразится статистика на текущий момент.