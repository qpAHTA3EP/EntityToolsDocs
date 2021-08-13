# **EntityCount**

Условие подсчитывает количество определенных *Entity* и сравнивает его с заданным значением [*Value*](!ref-Value).

---

# **Настройки условия**

| **Наименование** | **Описание** 
|:-----------------|:-------------
||**Настройки идентификации *Entity* (категория "Entity")**
|<a name ="ref-EntityID">***EntityID***</a><br/><a name ="ref-EntityIdType">***EntityIdType***</a><br/><a name ="ref-EntityNameType">***EntityNameType***</a><br/><a name ="ref-EntityID">***EntitySetType***</a> | Идентификация *Entity* производится сочетанием трех перечисленных слева свойств, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification-RU.md).
||**Дополнительные фильтры *Entity* (категория "Optional")**
|<a name ="ref-ReactionRange">***ReactionRange***</a> | Максимальное допустимое расстояние от *Entity* до персонажа. *Entity* на большем расстоянии игнорируются.<br/> Опция отключается при установке значения ``0``.
|<a name ="ref-ReactionZRange">***ReactionZRange***</a> | Максимальная допустимая разница по высоте (ZAxis) между *Entity* и персонажем. *Entity*, находящиеся выше (ниже) заданной величины относительно персонажа, - игнорируются. <br/> Опция отключается при установке значения ``0``. 
|<a name ="ref-RegionCheck">***RegionCheck***</a> | Флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*.<br/>- ***True*** : Поиск *Entity* производится в том же регионе, в котором находится персонаж;<br/>- ***False*** : Проверка региона при поиске *Entity* не производится.
|<a name ="ref-HealthCheck">***HealthCheck***</a> | Дополнительная проверка уровня здоровья *Entity* (HP).<br/> *True* : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг ***IsDead***;<br/>- ***False*** : Здоровье *Entity* (HP) не проверяется.
|| **(категория "Location")**
|<a name ="ref-CustomRegions">***CustomRegions***</a> | Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustomRegionSet](../../General/CustomRegionSet-RU.md).
|<a name ="ref-CustomRegionCheck">***CustomRegionCheck***</a>|Переключатель определяющий, в какой части игрового пространства необходимо производить подсчет *Entity*:<br/>- ***Equal*** : подсчет ведется внутри области, заданной [*CustomRegions*](#ref-CustomRegions);<br/>- ***NotEqual*** - подсчет ведется за пределами области, заданной [*CustomRegions*](#ref-CustomRegions).
|| **Проверка (категория "Tested")**
|<a name ="ref-Value">***Value***</a> | Значение, с которым сравнивается количество *Entity*.
|<a name ="ref-Sign">***Sign***</a> | Тип сопоставления значения [*Value*](!ref-Value) с количеством *Entity*:<br/>- ***Equal*** : количество *Entity* должно быть РАВНО [*Value*](!ref-Value);<br/>- ***NotEqual*** : количество *Entity* должно быть НЕ РАВНО [*Value*](!ref-Value);<br/>***Inferior*** : количество *Entity* должно быть МЕНЬШЕ [*Value*](!ref-Value);<br/>***Superior*** : количество *Entity* должно быть БОЛЬШЕ [*Value*](!ref-Value).

---

# **Условия - аналоги**
Отсутствуют.


# [Вернуться к содержанию](../../index.md)