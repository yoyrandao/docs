# Как изменить владельца платежного аккаунта


## Описание сценария {#case-description}

Необходимо передать доступы к управлению платежным аккаунтом {{ yandex-cloud }} другому лицу.

## Решение {#case-resolution}

Для смены администратора платежного аккаунта понадобится [создать новый запрос в техническую поддержку]({{ link-console-support }}).
Перед созданием запроса вы можете создать новый аккаунт Яндекс ID, которому вспоследствии будут переданы права на платежный аккаунт – это ускорит процедуру передачи доступов.

С нового аккаунта Яндекс ID понадобится авторизоваться в {{ yandex-cloud }}, но не создавать платёжный аккаунт. Для этого:

1. Перейдите [по ссылке]({{ link-console-main }});
2. Нажмите кнопку **{{ ui-key.yacloud.mdb.cluster.overview.button_action-connect }}** → «Войти через Яндекс ID»;
3. Зайдите от имени только что зарегистрированного аккаунта Яндекс ID и согласитесь с условием оферты, но не создавайте платёжный аккаунт в {{ yandex-cloud }}.

При создании запроса запросите у специалистов технической поддержки шаблон заявления на смену владельца платежного аккаунта.
Затем распечатайте полученный шаблон, подпишите его, поставьте печать организации и приложитн заполненную скан-копию заявления к уже заведенному в поддержку обращению.
Также к обращению понадобится приложить документ, подтверждающий полномочия подписанта.

{% note info %}

После смены владельца биллинг-аккаунта потребуется самостоятельно отозвать права у старого логина в облаках с ресурсами и облачных организациях,
[следуя соответствующей инструкции](../../../iam/operations/users/delete.md).

Новый аккаунт Яндекс ID не должен использоваться для авторизации в других сервисах Яндекса и иметь представительства в Балансе.

{% endnote %}

После получения подписанной скан-копии заявления специалисты технической поддержки смогут привязать ваш платежный аккаунт к новой учетной записи.