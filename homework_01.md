# Домашняя работа №1. Журнал событий на сайтах

## №1. Карта событий на сайте Google Analytics Enhanced Ecommerce Demo

**1. Открыл страницу магазина**

`en=page_view`  
`tid=G-ZPZD4SVKC0`  
`dl=https://enhancedecommerce.appspot.com/enhanced-ecommerce/`  
`dt=Enhanced Ecommerce Demo`  
`_et=8356`  
`cid=1144336685.1789152740`  
`sid=1789152740`

**2. Перешёл на страницу GA4**

`en=не указано`  
`tid=G-ZPZD4SVKC0`  
`dl=https://enhancedecommerce.appspot.com/ga4/`  
`dt=Discover the Google Analytics platform`  
`cid=1144336685.1789152740`  
`sid=1789152740`

**3. Перешёл на страницу товара**

`en=page_view`  
`tid=G-ZPZD4SVKC0`  
`dl=https://enhancedecommerce.appspot.com/products/compton-t-shirt/`  
`dt=Enhanced Ecommerce Demo`  
`cid=1144336685.1789152740`  
`sid=1789152740`

**4. Перешёл в Query Explorer**

`en=не указано`  
`tid=G-ZPZD4SVKC0`  
`dl=https://enhancedecommerce.appspot.com/ga4/query-explorer/`  
`dt=GA4 Query Explorer`  
`cid=1144336685.1789152740`  
`sid=1789152740`

**5. Открыл страницу другого товара**

`en=page_view`  
`tid=G-ZPZD4SVKC0`  
`dl=https://enhancedecommerce.appspot.com/products/futuris-t-shirt/`  
`dt=Enhanced Ecommerce Demo`  
`cid=1144336685.1789152740`  
`sid=1789152740`

## №2. Сравнение двух сайтов

Я сравнил Google Analytics Enhanced Ecommerce Demo и учебный сайт из задания.

Google Analytics Enhanced Ecommerce Demo содержит больше типов действий пользователя, потому что это интернет-магазин. Пользователь может переходить между страницами и открывать разные товары.

На учебном сайте события заранее прописаны в коде:

- `page_view` — открытие страницы;
- `select_content` — нажатие на кнопку «Оставить заявку»;
- `form_start` — начало заполнения формы;
- `generate_lead` — отправка заявки;
- `scroll` — прокрутка страницы.

В пойманных запросах Google Analytics Enhanced Ecommerce Demo встречаются параметры `tid`, `dl`, `dt`, `cid`, `sid` и `en`. При этом `en` присутствует не во всех запросах, поэтому по некоторым запросам нельзя точно определить название события.

В итоге учебный сайт больше ориентирован на получение заявки, а Google Analytics Enhanced Ecommerce Demo — на действия пользователя с товарами и страницами магазина.

## №3. Точка разрыва

В качестве точки разрыва я выбрал переход на страницу товара.

При переходе на товар в пойманном запросе передаётся:

`en=page_view`

При этом отдельного события `view_item` в этом запросе нет.

В GA4 `view_item` используется для фиксации просмотра информации о конкретном товаре.

### Как проверить

1. Открыть Google Analytics Enhanced Ecommerce Demo.
2. Открыть инструменты разработчика и перейти во вкладку `Network`.
3. Найти запросы `collect`.
4. Перейти на страницу товара.
5. Найти запрос, который появился после перехода.
6. Посмотреть параметр `en`.
7. Проверить параметр `dl`. В нём будет указан полный адрес страницы товара:

`https://enhancedecommerce.appspot.com/products/compton-t-shirt/`

В результате видно, что переход на страницу товара фиксируется как обычный `page_view`, а отдельного `view_item` в пойманном запросе нет.

### Вывод

Точка разрыва заключается в том, что после перехода на страницу товара фиксируется `page_view`, но отдельное событие `view_item` в пойманном запросе не передаётся.