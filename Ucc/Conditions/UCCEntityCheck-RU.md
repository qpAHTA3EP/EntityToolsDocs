# **UCCEntityCheck**

Условие сопоставляет с [*референтным значением*](!ref-PropertyValue  "Опция 'PropertyValue'") фактическое значение [*свойства*](#ref-PropertyType "Опция 'PropertyType'") ближайшего к персонажу *Entity*, удовлетворяющего [критериями](#ref-EntityIdentification).<br/>
Результат выполняемой [проверки](#ref-Tested "Заданной группой опций 'Tested'") - логическая величина (истина или ложь).

---

# **Настройки**

| **Наименование** | **Описание** 
|:-----------------|:-------------
|| <a name ="ref-EntityIdentification"></a>**Идентификации *Entity* (категория "Entity")**
|<a name ="ref-EntityID">***EntityID***</a><br/><a name ="ref-EntityIdType">***EntityIdType***</a><br/><a name ="ref-EntityNameType">***EntityNameType***</a><!--<br/><a name ="ref-EntityID">***EntitySetType***</a>--> | Идентификация *Entity* производится сочетанием <!--четырех-->трёх перечисленных слева свойств, которые подробно описаны в разделе [идентификация *Entity*](../../General/EntityIdentification-RU.md).
|| <a name ="ref-Tested"></a> **Проверка (категория "Tested")**
|<a name ="ref-PropertyType">***PropertyType***</a> | Переключатель, определяющий свойство *Entity*, которое должно быть проверено:<br/>- ***Distance*** : Рассточние между персонажем и *Entity*;<br/>- ***HealthPercent*** : величина здоровья *Entity* в процентах с точностью 1%;<br/>- **ZAxis** : Положение *Entity* относительно персонажа по оси Z с точностью 1.0;
|<a name ="ref-PropertyValue">***PropertyValue***</a> | Референтное величина, с которым сравнивается значение свойства *Entity*, заданного опцией [*PropertyType*](#ref-PropertyType).
|<a name ="ref-Sign">***Sign***</a> | Переключатель, который задает соотношение референтного значения [*PropertyValue*](!ref-PropertyValue) со значением свойства *Entity*, заданного опцией [*PropertyType*](#ref-PropertyType):<br/>- ***Equal*** : значение [*PropertyType*](#ref-PropertyType) должно быть РАВНО значению свойства [*PropertyValue*](!ref-PropertyValue);<br/>- ***NotEqual*** : значение [*PropertyType*](#ref-PropertyType) должно быть НЕ РАВНО [*PropertyValue*](!ref-PropertyValue);<br/>- ***Inferior*** : значение [*PropertyType*](#ref-PropertyType) должно быть МЕНЬШЕ значению свойства [*PropertyValue*](!ref-PropertyValue);<br/>- ***Superior*** : значение [*PropertyType*](#ref-PropertyType) должно быть БОЛЬШЕ значению свойства [*PropertyValue*](!ref-PropertyValue).
||**Дополнительные фильтры *Entity* (категория "Optional")**
|<a name ="ref-ReactionRange">***ReactionRange***</a> | Максимальное допустимое расстояние от *Entity* до персонажа. *Entity* на большем расстоянии игнорируются.<br/> Опция отключается при установке значения ``0``.
|<a name ="ref-ReactionZRange">***ReactionZRange***</a> | Максимальная допустимая разница по высоте (ZAxis) между *Entity* и персонажем. *Entity*, находящиеся выше (ниже) заданной величины относительно персонажа, - игнорируются. <br/> Опция отключается при установке значения ``0``. 
|<a name ="ref-RegionCheck">***RegionCheck***</a> | Флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*.<br/>- ***True*** : Поиск *Entity* производится в том же регионе, в котором находится персонаж;<br/>- ***False*** : Проверка региона при поиске *Entity* не производится.
|<a name ="ref-HealthCheck">***HealthCheck***</a> | Дополнительная проверка уровня здоровья *Entity* (HP).<br/>- ***True*** : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг *IsDead*;<br/>- ***False*** : Здоровье *Entity* (HP) не проверяется.
|<a name ="ref-Aura">***Aura***</a> | Комплексная опция, позволяющая указать ауру и количество её экземпляров, которые проверяется на целевой *Entity*:<br/>- <a name ="ref-AuraName">***AuraName***</a> : Идентификатор ауры;<br/>- <a name ="ref-AuraNameType">***AuraNameType***</a> : Переключатель способа интерпретации [*AuraName*](#ref-AuraName) (*Simple* или *Regex*);<br/>- <a name ="ref-Stacks">***Stacks***</a> : Референтное количество экземпляров ауры;<br/>- <a name ="ref-Sign">***Sign***</a> : Переключатель, который задает соотношение референтного значения [*Stacks*](!ref-Stacks) с подсчитанным количеством экземпляров ауры.<br/>Для поиска *Entity*,у которого отсутствует заданная аура достаточно задать:<br/> ```Stacks := 0; Sign := Equals```

<!--|| **Ограничение области подсчета (категория "Location")**
|<a name ="ref-CustomRegions">***CustomRegions***</a> | Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustomRegionSet](../../General/CustomRegionSet-RU.md).
|<a name ="ref-CustomRegionCheck">***CustomRegionCheck***</a>|Переключатель определяющий, в какой части игрового пространства необходимо производить подсчет *Entity*:<br/>- ***Equal*** : подсчет ведется внутри области, заданной [*CustomRegions*](#ref-CustomRegions);<br/>- ***NotEqual*** - подсчет ведется за пределами области, заданной [*CustomRegions*](#ref-CustomRegions).

---

# **Примеры**-->

---

# **Условия - аналоги**
Отсутствуют.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к перечню условий](../EntityTools-UccExtensions-RU.md#Условия)  
[Назад к содержанию](../EntityTools-UccExtensions-RU.md#Команды)