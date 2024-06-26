---
title: "Правила тарификации для {{ at-full-name }}"
description: "В статье содержатся правила тарификации сервиса {{ at-name }}."
editable: false
---

# Правила тарификации для {{ at-full-name }}

Тарифицируются доставленные события [уровня сервисов](./concepts/events-data-plane.md).

События [уровня конфигурации](./concepts/events.md) в настоящий момент не тарифицируются.

## Цены {#prices}


{% note warning %}

Цены действуют с 1 марта 2024 года.

{% endnote %}


{% include [rub.md](../_pricing/audit-trails/rub.md) %}




### Формула расчета стоимости {#price-formula}

Стоимость доставленных событий уровня сервисов рассчитывается пропорционально их количеству.

Например, стоимость доставки 17 000 событий составит:

> (17 000 / 100 000) × 36 ₽ = 0,17 × 36 ₽ = 6,12 ₽
> 
> 
> 
> Итого: 6,12 ₽

### Примеры расчета стоимости {#price-example}

{% list tabs %}

- Пример 1

  Расчет стоимости доставки событий получения содержимого секрета {{ lockbox-full-name }}, зашифрованного ключом шифрования {{ kms-full-name }}:
  * При каждом обращении к секрету доставляются два события: событие [доступа к содержимому секрета](./concepts/events-data-plane.md#lockbox) {{ lockbox-short-name }} и событие [расшифрования](./concepts/events-data-plane.md#kms) содержимого секрета с помощью ключа {{ kms-short-name }}.
  * Количество обращений к секрету: 7000.

  Расчет стоимости:

  > (2 × 7000 / 100 000) × 36 ₽ = 0,14 × 36 ₽ = 5,04 ₽
  > 
  > 
  > 
  > Итого: 5,04 ₽

  Где:
  * 2 — количество доставляемых событий при одном обращении к секрету.
  * 7000 — количество обращений к секрету.
  * 36 — цена за доставку 100 000 событий.
  * 100 000 — делим, чтобы привести количество событий к единице тарификации.

- Пример 2

  Расчет стоимости доставки событий при работе с бакетами {{ objstorage-full-name }}.

  Общее количество доставленных событий: 25 000. Из них:
  * Количество событий [уровня конфигурации](./concepts/events.md#objstorage), переданных при работе с бакетами: 1000.
      В это число вошли события по созданию и удалению бакетов, изменению политик доступа, настроек ACL и шифрования.

  * Количество событий [уровня сервисов](./concepts/events-data-plane.md#objstorage), переданных при работе с бакетами: 24 000.
      В это число вошли события по созданию объектов в бакетах и изменению тегов объектов.

  Расчет стоимости:

  > ((25 000 - 1000) / 100 000) × 36 ₽ = 0,24 × 36 ₽ = 8,64 ₽
  > 
  > 
  > 
  > Итого: 8,64 ₽

  Где:
  * 25 000 — общее количество доставленных событий {{ objstorage-name }}.
  * 1000 — количество доставленных событий уровня конфигурации, которые не тарифицируются.
  * 36 — цена за доставку 100 000 событий.
  * 100 000 — делим, чтобы привести количество событий к единице тарификации.

{% endlist %}