# Содержание
1. [Введение](#1-введение)
   - [Цели](#цели)
   - [Границы применения](#границы-применения)
   - [Термины и аббревиатуры](#термины-и-аббревиатуры)
   - [Ссылки](#ссылки)
   - [Краткий обзор](#краткий-обзор)
2. [Общее описание](#2-общее-описание)
   - [Описание изделия](#описание-изделия)
   - [Функции изделия](#функции-изделия)
   - [Характеристики пользователей](#характеристики-пользователей)
   - [Ограничения](#ограничения)
   - [Предположения и зависимости](#предположения-и-зависимости)
3. [Детальные требования](#3-детальные-требования)
   - [Функциональные требования](#функциональные-требования)
   - [Надежность](#надежность)
   - [Производительность](#производительность)
   - [Ремонтопригодность](#ремонтопригодность)
   - [Ограничения проекта](#ограничения-проекта)
   - [Требования к пользовательской документации](#требования-к-пользовательской-документации)
   - [Используемые компоненты](#используемые-компоненты)
   - [Интерфейсы](#интерфейсы)
   - [Требования лицензирования](#требования-лицензирования)
   - [Применимые стандарты](#применимые-стандарты)
4. [Индекс](#индекс)

---

# История изменений
| Дата       | Версия | Описание         | Автор(ы)      |
|------------|--------|------------------|---------------|
| 2024-10-03 | 0.1    | Начальная ревизия | Вершинина,Ермилова,Константинов,Одинцов |
|2024-10-23  |   0.2  | Начало пункта 3   | Вершинина,Ермилова,Константинов,Одинцов |
|2024-11-07  | 0.3    | Изменение задачи |  Вершинина,Ермилова,Константинов,Одинцов |
|2024-11-19  | 0.4    | Финальная версия |  Вершинина,Ермилова,Константинов,Одинцов |
---

# 1. Введение

## Цели
   Цель данного документа – изложить полную спецификацию требований к программному обеспечению для поддержки принятия решения. Данный документ предназначен для тех, кто будет принимать это решение. 
   
## Границы применения
   Данное программное обеспечение предназначено для менеджмента. Оно обеспечивает взаимодействие между людьми для принятия решения о том, подаваться на конкурс или нет. ПО - инструмент, само решения оно не принимает.


## Термины и аббревиатуры
   Конкурсная документация – документ, в котором неформально прописаны сроки, максимальная стоимость и объем работ.
   Сметчик – человек, формирующий смету работ.
   Смета работ – формальный документ, в котором фигурирует необходимый объем работ. Информация берется из справочника работ.  
   Справочник работ – справочник с описаанием работ, которые выполняет предприятие, их объем и актуальная стоимость.  
   Справочник компаний – список компаний, у которых наше предприятие производит закупку.  


## Ссылки
| Обозначение | Расшифровка           |
|-------------|-----------------------|
| [IEEE-830]  | IEEE Std 830-1998      |

## Краткий обзор
   - Введение - описывает цели документа, его границы применения, термины и аббревиатуры
   - Общее описание - описывает изделие, его верхнеуровневые функции и его ограничения. Также описывает характеристики пользователей.
   - Детальные требования - описывает функциональные требования, характеристики ремонтопригодности, надежности, производительности, тербования к пользовательской документации.
   
---

# 2. Общее описание
   У нас есть технический директор, который получает конкурсную документацию. Технический директор этот документ передает сметчику. Он формирует смету с помощью справочника работ. Если у нас нету данной позиции в справочнике работ, тогда сметчик формирует запрос в компании из определенного списка. Компании присылают ответ в котором они отвечают могут ли они предоставить этот материал или работников и цену. Затем сметчик выбирает каждую позицию с наименьшей ценой. После чего смета с ее стоимостью возвращается техническому директору, который решает, стоит ли подаваться на этот конкурс или нет.
## Описание изделия
- **Интерфейсы системы**: интерфейс технического специалиста. В его функции входит
   - подготовка конкурсной документации, отправление конкурсной документации сметчику,
   - помощь в принятии решения после получения сметы.
  Также есть интерфейс сметчика. В его функции входит:
   - получение конкурсной документации
   - помощь в составлении сметы
   - Отправление запросов необходимых материалов в компании
   - Выборка самых выгодных ресурсов  
   - передача сметы техническому директору
- **Интерфейсы пользователя**: Всего должно быть 2 интерфейса: для технического специалиста и для сметчика. Они должны соответствовать тому, чтобы  технический специалист и сметчик смогли разобраться в своем интерфейсе после небольшого инструктажа.
- **Интерфейсы коммуникаций**: Технический директор и сметчик должны иметь средство защищенной коммуникации по локальной сети или интернету.
- **Ограничения памяти**: отсутствуют
- **Действия**: ПО должно обеспечивать следующие действия: передача техническим директором конкурсной документации сметчику, составление сметчиком сметы, ·	отправление запросов компаниям и выборка самых выгодных позиций, передача сметы техническому директору, принятие техническим директором решения

  
## Функции изделия
Программное обеспечение необходимо для автоматизации принятия решения о том, подаваться в конкурс или нет. Для этого оно должно выполнять следующие функции:
-	Обеспечить передачу конкурсной документации без искажений от технического директора в течении 2-3 часов
-	Обеспечить доступ сметчику к актуальному на текущий день справочнику работ
-	Возможность составления запросов в предопределенный список компаний  
-	Реализовать инструмент, такой чтобы сметчик мог составить смету в течении 1-2 рабочих дней
-	Передача сметы без искажений генеральному директору должна составлять не более 2-3 часов
-	Технический директор при помощи сметы способен принять решение в течении 1-2 рабочих дней


## Характеристики пользователей
   Данное программное обеспечение предназначено для технического специалиста и сметчика предприятия. Соответственно пользователь должен обладать квалификацией технического специалиста или сметчика.


## Ограничения
   Предприятие, которое пользуется нашим продуктом, выполняет одинаковые работы и может без больших затрат и точно определить необходимый объем выполняемых работ.
   У предприятия должен быть справочник работ, в котором записаны его работы, их объем и стоимость.
   У предприятия должен быть человек, который следит за рынком и поддерживает справочник работ в актуальном состоянии.
   У предприятия должен список компаний, в которые они обращаются, если у них нету данного ресурса.  


## Предположения и зависимости
   Окончательное решение всегда зависит от технического директора. Даже если окажется, что сумма затрат превышает прибыль, технический директор может все же подаваться на конкурс, если посчитает это выгодным.


---

# 3. Детальные требования

## Функциональные требования
## 3.1 Общие функции:
   - Хранение статистики принятия решений    
Индификатор: 3.1.1    
Входные данные: результаты прошлых решений  
Операции над данными: хранение результатов и их обработка  
Выходные данные: отчет, в котором храниться процент удачных и неудачных решений  
   - Вычисление прибыли при участии в конкурс    
Индификатор: 3.1.2   
Входные данные: смета, конкурсная документация  
Операции над данными:  высчитывание по смете общее количество затрат, и рассечет прибыли  
Выходные данные: предположение сколько компания получит прибыли, если будет участвовать в конкурсе
   - Автоматическая проверка данных  
Индификатор: 3.1.3    
Входные данные: Конкурсная документация.  
Операции над данными: Проверка наличия всех необходимых данных, выявление ошибок и неточностей.  
Выходные данные: Уведомление о наличии ошибок или подтверждение корректности данных.  
   - Уведомления и оповещения  
Индификатор: 3.1.4  
Входные данные: Статус подготовки сметы, статус принятия решения по тендеру, статус запроса в компании.   
Операции над данными: Автоматическое создание уведомлений и напоминаний о важных сроках.  
Выходные данные: Уведомления для сметчика и технического директора. 
   - Аналитика и прогнозирование  
Индификатор: 3.1.5  
Входные данные: История предыдущих тендеров, данные о текущем тендере.  
Операции над данными: Прогнозирование успешности участия на основе анализа предыдущих данных и рыночной информации.
Выходные данные: Прогноз вероятности успеха в тендере.   
## 3.2 Функции для технического директора: 
   - Регистрация технического директора  
Индификатор: 3.2.1  
Входные данные: имя и пароль технического директора  
Операции над данными: сохранение имени и пароля в системе  
Выходные данные: аккаунт технического директора  
   - Авторизация технического директора  
Индификатор: 3.2.2   
Входные данные: имя и пароль технического директора  
Операции над данными: проверка имени и пароля на достоверность  
Выходные данные: вход  технического директора в свой аккаунт 
   - Помощь в составлении конкурса  
Индификатор: 3.2.3  
Входные данные: конкурсная документация  
Операции над данными: предоставить инструмент, с помощью которого технический директор сможет преобразовать конкурсную документацию для сметчика  
Выходные данные: конкурсная документация
   - Справка  
Индификатор: 3.2.4  
Входные данные: вопрос технического директора о функциональности системы  
Операции над данными: предоставление информации о функциональности системы  
Выходные данные: ответ на вопрос  
   - Отправка задания сметчику  
Индификатор: 3.2.5  
Входные данные: конкурсная документация    
Операции над данными: отправить конкурсную документацию от технического директора сметчику   
Выходные данные: сметчик получает конкурсную документацию  
   - Отслеживание статуса работы  
Индификатор: 3.2.6  
Входные данные: запрос технического директора  
Операции над данными: проверка статуса работы  
Выходные данные: предоставление техническому директору статуса работы  
   - Получение сметы  
Индификатор: 3.2.7  
Входные данные: смета  
Операции над данными: передача сметы техническому директору  
Выходные данные: принятие сметы техническим директором или отправление на доработку  
   - Возможность внесения изменений в процессе работы  
Индификатор: 3.2.8  
Входные данные: изменения внесенные техническим директором в конкурсную документацию  
Операции над данными: передача изменений сметчику  
Выходные данные: сметчик получил изменения от технического директора  
   - Принятие решения  
Индификатор: 3.2.9  
Входные данные: смета  
Операции над данными: анализ сметы и предоставление техническому директору аналитических данных  
Выходные данные: окончательное решение технического директора
   - Оценка рисков  
Индификатор: 3.2.10  
Входные данные: Конкурсная документация, предыдущие решения, рыночные данные.  
Операции над данными: Анализ потенциальных рисков участия в тендере (переплаты, недостаток ресурсов, низкая вероятность выигрыша).  
Выходные данные: Отчет с оценкой рисков и рекомендациями для технического директора.  
   - История решений  
Индификатор: 3.2.11  
Входные данные: Архив предыдущих решений, данные о сметах и результатах тендеров.  
Операции над данными: Хранение и обработка данных о прошлых тендерах, анализ успешности/неуспешности участия.  
Выходные данные: Отчет с процентом успешных решений и результатами предыдущих тендеров.  
   - Интеграция с внешними источниками  
Индификатор: 3.2.12   
Входные данные: Конкурсная документация, импортируемая из внешних систем.  
Операции над данными: Автоматическое получение и сохранение конкурсной документации из внешних источников.  
Выходные данные: Готовая конкурсная документация, доступная для обработки сметчиком.


## 3.3 Функции для сметчика:
   - Регистрация сметчика  
Индификатор: 3.3.1   
Входные данные: имя и пароль сметчика  
Операции над данными: сохранение имени и пароля в системе  
Выходные данные: аккаунт сметчика  
   - Авторизация сметчика  
Индификатор: 3.3.2   
Входные данные: имя и пароль сметчика  
Операции над данными: проверка имени и пароля на достоверность  
Выходные данные: вход  сметчика в свой аккаунт  
   - Проверка даты обновления справочника  
Индификатор: 3.3.3   
Входные данные: справочник работ  
Операции над данными: получение даты справочника работ  
Выходные данные: передача сметчику даты справочника работ  
   - Запрос на обновление справочника  
Индификатор: 3.3.4   
Входные данные: запрос сметчика  
Операции над данными: передача задачи, человеку, который поддерживает справочник  
Выходные данные: обновленный справочник  
   - Запрос на добавление работы  
Индификатор: 3.3.5   
Входные данные: запрос сметчика  
Операции над данными: передача задачи, человеку, который поддерживает справочник  
Выходные данные: обновленный справочник
   - Запрос на добавление компании  
Индификатор: 3.3.6   
Входные данные: запрос сметчика на определенный ресурс, которого нету у нас и у компаний, в которых мы закупаемся  
Операции над данными: поиск компании, которая готова предоставить этот ресурс  
Выходные данные: Добавление этой компании в справочник компаний  
   - Запрос на обновление справочника компаний  
Индификатор: 3.3.7   
Входные данные: запрос сметчика  
Операции над данными: мониторинг рынка, поиск более выгодных предложений  
Выходные данные: обновленный справочник компаний    
   - Проверка даты обновления справочника компаний  
Индификатор: 3.3.8   
Входные данные: справочник компаний  
Операции над данными: получение даты справочника компаний  
Выходные данные: передача сметчику даты справочника компаний  
   - Справка  
Индификатор: 3.3.9   
Входные данные: вопрос сметчика о функциональности системы  
Операции над данными: предоставление информации о функциональности системы  
Выходные данные: ответ на вопрос  
   - Составление сметы  
Индификатор: 3.3.10   
Входные данные: конкурсная документация  
Операции над данными: предоставление инструментов сметчику для составление сметы  
Выходные данные: смета  
   - Контроль ошибок  
Индификатор: 3.3.11   
Входные данные: смета  
Операции над данными: проверка сметы на ошибки  
Выходные данные: предупреждение, если смета не соответствует заложенным в систему требованиям  
   - Отправка сметы  
Индификатор: 3.3.12   
Входные данные: смета  
Операции над данными: передача сметы техническому директору  
Выходные данные: технический директор получил смету  
   - Получение данных из справочника  
Индификатор: 3.3.13   
Входные данные: запрос сметчика  
Операции над данными: обработка запроса, поиск данных в справочнике  
Выходные данные: результат запроса  
   - Возможность уточнения конкурсной документации  
Индификатор: 3.3.14   
Входные данные: запрос сметчика  
Операции над данными: передача запроса техническому директору  
Выходные данные: ответ от технического директора  
   - Автоматическое обновление справочника работ  
Индификатор: 3.3.15   
Входные данные: Данные о текущих ценах на рынке и справочник работ.  
Операции над данными: Сравнение данных с внешними источниками, автоматическое обновление цен в справочнике.  
Выходные данные: Обновленный справочник работ, доступный для сметчика.  
   - Оптимизация расчетов сметы  
Индификатор: 3.3.16   
Входные данные: Конкурсная документация, текущий справочник работ.  
Операции над данными: Автоматическое предложение более экономичных альтернатив для работ и материалов.  
Выходные данные: Смета с предложенными альтернативными вариантами.
   - Формирование запроса в компании  
Индификатор: 3.3.17  
Входные данные: список необходимых ресурсов  
Операции над данными: составление в специальной форме запроса на покупку ресурсов и отсылка по почте их в компании  
Выходные данные: ответ компаний  
   - Выбор выгодных позиций и отправка согласия на покупку по почте  
Индификатор: 3.3.18  
Входные данные: ответ компаний  
Операции над данными: выбор позиций по самой низкой цене и формирования спи ска у какой компании что покупаем  
Выходные данные: покупка у компаний по этому списку ресурсов   

## 3.5 Нефункциональные требования  
   - Скорость обработки данных  
Индификатор: 3.4.1   
Входные данные: Запросы пользователей.  
Операции над данными: Оптимизация времени отклика системы на основе количества запросов.  
Выходные данные: Время отклика не более 1 секунды на каждый запрос.  
   - Маштабируемость  
Индификатор: 3.4.2   
Входные данные: Количество пользователей, объем данных.  
Операции над данными: Оптимизация работы системы для увеличения нагрузки без потери производительности.  
Выходные данные: Система поддерживает многопользовательский режим без снижения производительности.  


## Надежность
   - Все данные с которыми взаимодействует система должны иметь несколько постоянно обновляющихся копий лежащий не на одном сервере  
   - Все соединения должны быть защищены и зашифрованы  
- **Доступность**: В любое рабочее время  
- **MTBF**: раз в 500 часов работы  
- **MTTR**: один рабочий день  
- **Точность**: не требуется  
- **Макс. количество ошибок**: раз в 5000 часов.  

## Производительность
- **Время отклика**: Время отклика системы на запрос пользователя не должно превышать 2 секунд в 95% случаев
- **Пропускная способность**: 100 транзакций в секунду при пиковых нагрузках
- **Утилизация ресурсов**: не требуется

## Ремонтопригодность
   - Система должна уметь улавливать ошибки и исправлять их  
   - Система должна разрабатываться так, чтобы ее можно было потомлегко модифицировать и обновлять и поддерживать  
   - Система должна обладать модульной архитектурой  

## Ограничения проекта
Для полного функционирования проекта у компании должен быть справочник работ и справочник компаний

## Требования к пользовательской документации
Вместе с системой должна предоставляться  пользовательская документация, с которой способны справиться сметчик и технический директор. Также в пользовательских интерфейсах есть справка, с помощью которой пользователь может узнать о функциональности системы.  

## Используемые компоненты
   - Все справочники работ будут находиться на внутренней БД компании  
   - Будут использоваться защищенный каналы передачи данных  

## Интерфейсы
- **Интерфейс пользователя**: В программе 2 интерфейса – интерфейс технического директора и сметчика.  
- **Аппаратные интерфейсы**: нет  
- **Программные интерфейсы**: нет  
- **Интерфейсы коммуникаций**: между техническим директором и сметчиком  

## Требования лицензирования
Выходят за рамки проекта  
 
## Применимые стандарты
IEEE-830   


# Индекс
[Индекс.]
