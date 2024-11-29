# Роботы и действия бизнес-процессов с ожиданием результата bizproc.event.send

{% note warning "Мы еще обновляем эту страницу" %}

Тут может не хватать некоторых данных — дополним в ближайшее время

{% endnote %}

{% if build == 'dev' %}

{% note alert "TO-DO _не выгружается на prod_" %}

Статья про то, как работает ожидание результата от робота и действий бп. Тезисы:

- В каких сценариях нужны такие роботы и действия?
- Какие есть минусы и особенности?
- Как это работает? Вот тут всплывает метод bizproc.event.send в обычном оформлении

{% endnote %}

{% endif %}

> Scope: [`bizproc`](../../scopes/permissions.md)
>
> Кто может выполнять метод: любой пользователь

Метод возвращает действию выходные параметры, заданные в описании действия.

#|
|| Параметр     | Описание  ||
|| **EVENT_TOKEN** | Уникальный ключ, который необходимо использовать при отправке события бизнес-процессу. Значение этого токена получает обработчик робота или действия юизнес-процесса в массиве передаваемых входных данных.    ||
|| **RETURN_VALUES** | Массив возвращаемых значений действия. Также будет появляться в форме _Вставка значения_ во вкладке _Дополнительные результаты_. ||
|#

## Пример

{% include [Сноска о примерах](../../../_includes/examples.md) %}

{% list tabs %}

- JS

    ```javascript
    var params = {
        event_token: '55c1dc1c3f0d75.78875596|A51601_82584_96831_81132|hsyUws1j4XiwqPqN45eH66CcQtEvpUIP.47dd5d888e8e549d2c984713e12a4268e6e87d0208ca1f093ba1075e77f92e90',
        return_values: {
            outputString: '846c55d14f552180874a628d2615e285'
        }
    };

    BX24.callMethod(
        'bizproc.event.send',
        params,
        function(result) {
            if(result.error())
                alert("Error: " + result.error());
            else
                alert("Success: " + result.data());
        }
    );
    ```

{% endlist %}