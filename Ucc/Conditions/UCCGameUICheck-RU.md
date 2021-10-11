# **UCCGameUICheck**

Условие проверяет состояние [внутриигрового элемента интерфейса](#ref-UiGenID "UiGenID") или значение одного из [свойств](#ref-UiGenProperty "Группа опций ''") данного элемента.<br/>
Результат выполняемой проверки - логическая величина (истина или ложь).

---

# **Настройки**

| **Наименование** | **Описание** 
|:-----------------|:-------------
|| <a name ="ref-EntityIdentification"></a>**Идентификации *Entity* (категория "Entity")**
|<a name ="ref-UiGenID">***UiGenID***</a><br/> | Текстовый идентификатор внутриигрового элемента интерфейса.
|<a name ="ref-Check">***Check***</a><br/> | Переключатель, определяющий тип выполняемой проверки:<br/>- ***IsVisible*** : проверка видимости. Условие истинно, если элемент интерфейса отображается в игровом окне. При этом не имеет значение его положение в игровом окне. Он может быть расположен за границами игрового окна, но иметь статус видимого;<br/>- ***IsHidden*** : проверка невидимости. Условие истинно, если элемент интерфейса НЕ отображается (скрыт) в игровом окне.;<br/>- ***Property*** : проверка значения свойства, заданного группой опций[*GuiProperty*](#ref-GuiProperty).
|| <a name ="ref-GuiProperty"></a> **Идентификация свойства элемента интерфейса<br/>(категория "GuiProperty")**
|<a name ="ref-UiGenProperty">***UiGenProperty***</a> | Текстовый идентификатор свойства внутриигрового элемента интерфейса.
|<a name ="ref-UiGenPropertyType">***UiGenPropertyType***</a> | Переключатель способа интерпретации [*UiGenProperty*](#ref-UiGenProperty):<br/>- ***Simple*** : Простая текстовая строка. <br/>В начале и в конце строки допускается использование символа подстановки ``"*"``, заменяющего произвольное число алфавитно-цифровых символов;<br/>- ***Regex*** : Регулярное выражение, составленное по правилам [.Net Framework](https://docs.microsoft.com/ru-ru/dotnet/standard/base-types/regular-expressions).
|<a name ="ref-UiGenPropertyValue">***UiGenPropertyValue***</a> | Референтное значение свойства внутриигрового элемента интерфейса.
|<a name ="ref-PropertySign">***PropertySign***</a> | Переключатель, который задает соотношение референтного значения [*UiGenPropertyValue*](!ref-UiGenPropertyValue) со значением [свойства внутриигрового элемента интерфейса](#ref-UiGenProperty "Опция 'UiGenProperty'"):<br/>- ***Equal*** : значение должно быть РАВНО [*UiGenPropertyValue*](!ref-UiGenPropertyValue);<br/>- ***NotEqual*** : значение должно быть НЕ РАВНО [*UiGenPropertyValue*](!ref-UiGenPropertyValue);<br/>- ***Inferior*** : значение должно быть МЕНЬШЕ [*UiGenPropertyValue*](!ref-UiGenPropertyValue);<br/>- ***Superior*** : значение должно быть БОЛЬШЕ [*UiGenPropertyValue*](!ref-UiGenPropertyValue).

---

# **Условия - аналоги**
Отсутствуют.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к перечню условий](../EntityTools-UccExtensions-RU.md#ref-Conditions)  
[Назад к содержанию](../../index.md)