---
editable: false
---

{% if audience == "internal" %}

[!INCLUDE [quotas](../_includes/internal/quotas.md)]

{% else %}

# Правила тарификации для [!KEYREF MY]

На стадии Preview использование сервиса [!KEYREF mmy-name] не тарифицируется. Вы можете создавать кластеры баз данных, пользоваться хранилищем и резервными копиями в рамках [квот и лимитов](concepts/limits.md).

Все остальные услуги Облака, например, создание виртуальных машин или выделение внешних IP-адресов для хостов БД, [тарифицируются обычным образом](../billing/pricing.md). Исходящий трафик тарифицируется аналогично другим сервисам управляемых СУБД, например, [Managed Service for PostgreSQL](../managed-postgresql/pricing.md#prices-traffic).

{% endif %}