# Управление доступом

Пользователь {{ yandex-cloud }} может выполнять только те операции над ресурсами, которые разрешены назначенными ему ролями. Пока у пользователя нет никаких ролей все операции ему запрещены.

Чтобы разрешить доступ к ресурсам сервиса {{ message-queue-full-name }}, назначьте пользователю нужные роли из приведенного ниже списка. На данный момент роль может быть назначена только на родительский ресурс (каталог или облако), роли которого наследуются вложенными ресурсами.

{% note info %}

Подробнее о наследовании ролей читайте в разделе [Наследование прав доступа](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) документации сервиса {{ resmgr-name }}.

{% endnote %}

## Назначение ролей {#grant-roles}

Для управления очередями пользователь должен иметь соответствующие полномочия в облаке и каталогах, в которых будут выполняться операции.

Чтобы дать пользователю полномочия:

{% include [grant-role-console](../../_includes/grant-role-console.md) %}

## Роли {#roles}

Ниже перечислены все роли, которые учитываются при проверке прав доступа в сервисе {{ service-name }}.

{% include [cloud-roles](../../_includes/cloud-roles.md) %}

### {{ roles-viewer }} {#viewer}
Пользователь с ролью `{{ roles-viewer }}` может смотреть списки облачных очередей и сообщений.

### {{ roles-editor }} {#editor}
Пользователь с ролью `{{ roles-editor }}` может выполнять любые операции с очередями и сообщениями.

Помимо этого роль `{{ roles-editor }}` включает в себя все разрешения роли `{{ roles-viewer }}`.

### {{ roles-admin }} {#admin}
Пользователь с ролью `{{ roles-admin }}` может управлять правами доступа к ресурсам, например, разрешить другим пользователям создавать очереди и сообщения или просматривать информацию о них.

Помимо этого роль `{{ roles-admin }}` включает в себя все разрешения роли `{{ roles-editor }}`.

## См. также {#see-also}

[Структура ресурсов {{ yandex-cloud }}](../../resource-manager/concepts/resources-hierarchy.md)