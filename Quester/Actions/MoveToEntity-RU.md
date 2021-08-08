# **MoveToEntity**
Команда предназначена для патрулирования по *HotSpots* до обнаружения заданного *Entity*, которое может быть принудительно атаковано.
## Общее описание алгоритма
1. Бот перемещается между точками *HotSpots* производя поиск *Entity*, удовлетворяющего критериям поиска. 
1. Патрулирование может производиться в режиме игнорирования боя [*IgnoreCombat*](refIgnoreCombat).
1. Область поиска *Entity* может быть ограничена опцией [*CustomRegions*](refCustomRegions)
1. Когда целевое *Entity* найдено, бот следует к нему.
2. Целевое *Entity* может быть атаковано, если установлен флаг [*AttackTargetEntity*](#refAttackTargetEntity).

***

# **Настройки команды**
## **Настройки идентификации *Entity***
Искомое *Entity* задается комбинацией свойств ***EntityID***, ***EntityIdType***, ***EntityNameType***, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification-RU.md)


## **Дополнительные фильтры *Entity* (категория "Optional")**

- ***ReactionRange*** - Расстояние от персонажа, в пределах которого производится поиск *Entity*. При установке значения равным 0, опция отключается и поиск производится среди всех видимых боту *Entity*.
- ***ReactionZRange*** - Максимальная разница по высоте (ZAxis), в пределах которой производится поиск *Entity*. При установке значения равным 0, опция отключается и поиск производится среди всех видимых боту *Entity*.
- ***RegionCheck*** - Флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*:
  + *True* : Поиск *Entity* производится в том же регионе, в котором находится персонаж;
  + *False* : Проверка региона при поиске *Entity* не производится;
- ***HealthCheck*** - дополнительная проверка уровня здоровья *Entity*:;
  + *True* : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг *IsDead*;
  + *False* : Здоровье *Entity* не проверяется;
- ***HoldTargetEntity*** - Флаг удержания *Entity*
   + *True* : Бот продолжает следовать к найденному *Entity*, даже в том случае, если будет найдено *Entity* ближе;
   + *False* : Бот постоянно производит поиск и следует к ближайшему *Entity*.
- <a name ="refCustomRegions" />***CustomRegions*** - Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustorRegionSet](../../General/CustorRegionSet-RU.md).

## **Опции, модифицирующие поведение (категория "Interruptions")**
### **Управление боем**
- <a name ="refIgnoreCombat" />***IgnoreCombat*** - Enable '***IgnoreCombat***' mode while playing action;
- ***Distance*** - Distance to the *Entity* by which it is necessary to approach. Keep in mind that the distance below 5 is too small to display on the [Mapper](../../Patches/Mapper/Mapper-RU.md).
- ***AbortCombatDistance*** - The battle is aborted outside ***AbortCombatDistance*** radius from the target *entity*. The combat is restored within the ***Distance*** radius. However, this is not performed if the value less than ***Distance*** or ***IgnoreCombat*** is *False*;
- <a name ="refAttackTargetEntity" /> ***AttackTargetEntity*** - 
  + *True* : Clear the list of attackers and attack the target Entity when it is approached. This option is ignored if ***IgnoreCombat*** does not set.
### **Прерывание команды**
- ***StopOnApproached*** - 
  + *True* : Complete an action when the Entity is closer than ***Distance***;
  + *False* : Follow an Entity regardless of its distance.

## **Прочие опции**
- ***ResetCurrentHotSpot*** - Reset current HotSpot after approaching the target *Entity*
