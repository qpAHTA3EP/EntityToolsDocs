# **MoveToEntity**

Команда предназначена для патрулирования по *HotSpots* и поиска заданного *Entity*.

## Краткое описание алгоритма команды
1. Бот перемещается между точками *HotSpots* производя поиск ближайшего *Entity*, удовлетворяющего критериям поиска. <br/>
   - Патрулирование может производиться в режиме игнорирования боя [*IgnoreCombat*](#ref-IgnoreCombat).<br/>
   - Область поиска *Entity* может быть ограничена опциями [*CustomRegions*](#ref-CustomRegions),  [*ReactionRange*](#ref-ReactionRange) и [*ReactionZRange*](#ref-ReactionZRange).

2. Когда целевое *Entity* найдено, бот следует к нему по кратчайшему пути.
   - Целевое *Entity* может быть принудительно атаковано, если установлен флаг [*AttackTargetEntity*](#ref-AttackTargetEntity). При этом игнорируется список *Blacklist* выполняемого quester-профиля.

3. После исчезновения (уничтожения) всех *Entity*, удовлетворяющих критериям поиска, бот возобновляет патрулирование.


# **Настройки команды**

## **Настройки идентификации *Entity***
Искомое *Entity* задается комбинацией свойств ***EntityID***, ***EntityIdType***, ***EntityNameType***, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification-RU.md)


## **Дополнительные фильтры *Entity* (категория "Optional")**

- <a name ="ref-ReactionRange"></a>***ReactionRange*** - максимальное допустимое расстояние от *Entity* до персонажа. *Entity* на большем расстоянии игнорируются.<br/>
Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.

- <a name ="ref-ReactionZRange"></a>***ReactionZRange*** - максимальная допустимая разница по высоте (ZAxis) между *Entity* и персонажем. *Entity*, находящиеся выше (ниже) заданной величины относительно персонажа, - игнорируются. <br/>
Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.

- <a name ="ref-RegionCheck"></a>***RegionCheck*** - флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*.
  + *True* : Поиск *Entity* производится в том же регионе, в котором находится персонаж;
  + *False* : Проверка региона при поиске *Entity* не производится.

- <a name ="ref-HealthCheck"></a>***HealthCheck*** - дополнительная проверка уровня здоровья *Entity* (HP).
  + *True* : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг *IsDead*;
  + *False* : Здоровье *Entity* (HP) не проверяется.

- <a name ="ref-HoldTargetEntity"></a>***HoldTargetEntity*** - флаг удержания *Entity*.
   + *True* : Бот продолжает следовать к ранее найденному *Entity*, даже в том случае, если будет обнаружено *Entity* поближе;
   + *False* : Бот постоянно производит поиск и следует к ближайшему *Entity*.

- <a name ="ref-CustomRegions"></a>***CustomRegions*** - набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustomRegionSet](../../General/CustomRegionSet-RU.md).

## **Опции, модифицирующие поведение (категория "Interruptions")**
### **Управление боем**
- <a name ="ref-IgnoreCombat"></a>***IgnoreCombat*** - флаг, предписывающий активировать режим игнорирования боя ***IgnoreCombat*** при следовании к целевой *Entity*.

- <a name ="ref-CombatDistance"></a>***CombatDistance*** - расстояние до целевой *Entity*, на котором отключается режим игнорирования боя ***IgnoreCombat***. <br/>
При установке значения более ``5`` на [Mapper](../../Patches/Mapper/Mapper-RU.md) соответствующая область отображается окружностью, центром которой является соответствующая *Entity*.

- <a name ="ref-AbortCombatDistance"></a>***AbortCombatDistance*** - расстояние от *Entity*, за пределами которого бой принудительно прерывается. <br/>
Бой снова активируются на расстоянии [*CombatDistance*](#ref-CombatDistance) от целевой *Entity*. При значении меньшем [*CombatDistance*](#ref-CombatDistance) или при выключенном флаге [*IgnoreCombat*](#ref-IgnoreCombat), опция отключается;

- <a name ="ref-AttackTargetEntity"></a> ***AttackTargetEntity*** - флаг, предписывающий атаковать целевую *Entity*. <br/>
Опция игнорируется, если флаг [*IgnoreCombat*](#ref-IgnoreCombat) не установлен.

### **Прерывание команды**
- <a name ="ref-StopOnApproached"></a>***StopOnApproached*** - флаг, завершающий выполнение команды после того как персонаж приблизился к целевой *Entity* на расстояние [*CombatDistance*](#ref-CombatDistance).

## **Прочие опции**
- <a name ="ref-ResetCurrentHotSpot"></a>***ResetCurrentHotSpot*** - флаг, предписывающий двигаться к ближайшему *HotSpot*'у после исчезновения (уничтожения) всех видимых целевых *Entity*.<br/>  
Если флаг не установлен бот "запоминает" последний *HotSpot*, к которому двигался перед обнаружением *Entity* и после её исчезновения (уничтожения) продолжает движение к нему.


# **Завершение команды**

Команда самостоятельно не завершается, если не задан флаг [*StopOnApproached*](#ref-StopOnApproached).

Принудительное завершение команды возможно одним из [перечисленных в статье способов](./../../General/ForcedQuesterActionTermination-RU.md).


# [Вернуться к содержанию](../../index.md)