# **UCCCheckTimer**

Условие проверяет состояние [именованного таймера](#ref-TimerName "TimerName").<br/>
Результат выполняемой проверки - логическая величина (истина или ложь).

Если [именованный таймер](#ref-TimerName "TimerName") на были запущен, принимаем, что таймаут истек (до окончания 0 мс), а время с момента старта таймера также 0 мс.

---

# **Настройки**

| **Наименование** | **Описание** 
|:-----------------|:-------------
|| **Категория "Timer"**
|<a name ="ref-TimerName">***TimerName***</a><br/> | Название именованного таймера, значение которого проверяется.
|<a name ="ref-TestTimer">***TestTimer***</a> | Переключатель периода времени, сопоставляемого с опцией [*Time*](!ref-Value):<br/>- **Left** : Опция *Time* сравнивается со временем, оставшимся до окончания таймера;<br/>- **Passed** : Опция *Time* сравнивается со временем, прошедшим с момента старта таймера;
|<a name ="ref-Time">***Time***</a><br/> | Референтное значение (мс), сопоставляемое с периодом времени, заданным [*TestTimer*](!ref-TestTimer).
|<a name ="ref-Sign">***Sign***</a><br/> | Тип сопоставления [*Time*](!ref-Value) с периодом времени, заданным [*TestTimer*](!ref-TestTimer):<br/>- ***Equal*** : время [*TestTimer*](!ref-TestTimer) должно быть РАВНО [*Time*](!ref-Value);<br/>- ***NotEqual*** : время [*TestTimer*](!ref-TestTimer) должно быть НЕ РАВНО [*Time*](!ref-Value);<br/>- ***Inferior*** : время [*TestTimer*](!ref-TestTimer) должно быть МЕНЬШЕ [*Time*](!ref-Value);<br/>- ***Superior*** : время [*TestTimer*](!ref-TestTimer) должно быть БОЛЬШЕ [*Time*](!ref-Value).

---

# **Примеры**

Чтобы проверить, что таймер истек, достаточно задать следующие настройки:
```
TestTimer := Left
Time := 0
Sign := Inferrior
```

---

# **Условия - аналоги**
Отсутствуют.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к перечню условий](../EntityTools-UccExtensions-RU.md#Условия)  
[Назад к содержанию](../EntityTools-UccExtensions-RU.md#Команды)