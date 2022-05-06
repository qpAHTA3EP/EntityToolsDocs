# **MoveToEntity**

Команда предназначена для патрулирования по маршруту, заданному набором точек *HotSpots*, в поисках заданного *Entity*.

## **Описание алгоритма**

1. Бот перемещается между точками *HotSpots* производя поиск ближайшего *Entity*, удовлетворяющего критериям поиска. <br/>
   - Патрулирование может производиться в режиме игнорирования боя [*IgnoreCombat*](#ref-IgnoreCombat).<br/>
   - Область поиска *Entity* может быть ограничена опциями [*CurrentMap*](#ref-CurrentMap), [*CustomRegions*](#ref-CustomRegions),  [*ReactionRange*](#ref-ReactionRange) и [*ReactionZRange*](#ref-ReactionZRange).

2. Когда целевое *Entity* найдено, бот следует к нему по кратчайшему пути.
   - Целевое *Entity* может быть принудительно атаковано, если установлен флаг [*AttackTargetEntity*](#ref-AttackTargetEntity). При этом игнорируется список *Blacklist* выполняемого quester-профиля.
   - При перво воздействии на целевое *Entity* применяется умение [*PowerId*](#ref-PowerId).  

3. После исчезновения (уничтожения) всех *Entity*, удовлетворяющих критериям поиска, бот возобновляет патрулирование.

---

# **Настройки команды**

| **Наименование** | **Описание** |
|:-----------------|:-------------|
||**Настройки идентификации *Entity* (категория "Entity")**|
|<a name ="ref-EntityID">***EntityID***</a><br/><a name ="ref-EntityIdType">***EntityIdType***</a><br/><a name ="ref-EntityNameType">***EntityNameType***</a> | Идентификация *Entity* производится сочетанием трех перечисленных слева свойств, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification-RU.md).
||**Дополнительные фильтры *Entity* (категория "Entity Search Options")**|
|<a name ="ref-HealthCheck">***HealthCheck***</a> | Дополнительная проверка уровня здоровья *Entity* (HP).<br/>- ***True*** : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг ***IsDead***;<br/>- ***False*** : Здоровье *Entity* (HP) не проверяется.
|<a name ="ref-HoldTargetEntity">***HoldTargetEntity***</a> | Флаг удержания *Entity*.<br/>- ***True*** : Бот продолжает следовать к ранее найденному *Entity*, даже в том случае, если будет обнаружено *Entity* поближе;<br/>- ***False*** : Бот постоянно производит поиск и следует к ближайшему *Entity*.
||**Область поиска *Entity* (категория "Search Area")**|
|<a name ="ref-ReactionRange">***ReactionRange***</a> | Максимальное допустимое расстояние от *Entity* до персонажа. *Entity* на большем расстоянии игнорируются.<br/> Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.
|<a name ="ref-ReactionZRange">***ReactionZRange***</a> | Максимальная допустимая разница по высоте (ZAxis) между *Entity* и персонажем. *Entity*, находящиеся выше (ниже) заданной величины относительно персонажа, - игнорируются. <br/> Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.
|<a name ="ref-RegionCheck">***RegionCheck***</a> | Флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*.<br/>- ***True*** : Поиск *Entity* производится в том же регионе, в котором находится персонаж;<br/>- ***False*** : Проверка региона при поиске *Entity* не производится.
|<a name ="ref-CustomRegions">***CustomRegions***</a> | Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustomRegionSet](../../General/CustomRegionSet-RU.md).
|<a name ="ref-CustomRegionsPlayerCheck">***CustomRegionsPlayerCheck***</a> | Флаг, устанавливающий требование нахождения персонажа в области, заданной опцией [CustomRegions](#ref-CustomRegions). Команда не будет запущена, если персонаж находится за пределами заданной области.
|<a name ="ref-CurrentMap">***CurrentMap***</a> | Идентификатор карты, на которой должен производиться поиск *Entity*. Команда не будет запущена, если персонаж находится за пределами заданной карты.<br/>Опция игнорируется, если идентификатор не задан.
||**Управление боем (категория "Manage Combat Options")**|
|<a name ="ref-IgnoreCombat">***IgnoreCombat***</a> | Флаг, предписывающий активировать режим игнорирования боя *IgnoreCombat* при следовании к целевой *Entity*.
|<a name ="ref-IgnoreCombatCondition">***IgnoreCombatCondition***</a> | Дополнительное условие, управляющее режимом прерывания боя. Если условие на выполняется, то режим игнорирования боя не активируется.
|<a name ="ref-IgnoreCombatMinHP">***IgnoreCombatMinHP***</a> | Величина минимального здоровья персонажа HP (в процентах), при котором может быть активирован режим игнорирования боя. Если здоровье персонажа опустится ниже указанной величины, то персонаж вступи в бой.<br/>При значении -1 команда не меняетт системное значение **IgnoreCombatMinHP** при активации режима игнорирования боя.
 |<a name ="ref-CombatDistance">***CombatDistance***</a> | Расстояние до целевой *Entity*, на котором отключается режим игнорирования боя *IgnoreCombat*. <br/> Минимальное значение ``5``. <!--на [Mapper](../../Patches/Mapper/Mapper-RU.md) соответствующая область отображается окружностью, центром которой является соответствующая *Entity*. -->
|<a name ="ref-AbortCombatDistance">***AbortCombatDistance***</a> | Расстояние от *Entity*, за пределами которого бой принудительно прерывается. <br/> Бой снова активируются на расстоянии [*CombatDistance*](#ref-CombatDistance) от целевой *Entity*. При значении меньшем [*CombatDistance*](#ref-CombatDistance) или при выключенном флаге [*IgnoreCombat*](#ref-IgnoreCombat), опция отключается.
|<a name ="ref-AttackTargetEntity">***AttackTargetEntity***</a> | Флаг, предписывающий атаковать целевую *Entity*. <br/> Опция игнорируется, если флаг [*IgnoreCombat*](#ref-IgnoreCombat) не установлен.
|<a name ="ref-PowerId">***PowerId***</a> | Идентификатор умения, применяемого к целевому *Entity* в качестве первого удара. Заданное умение может применяться, даже если  цель является дружественной.
|<a name ="ref-PowerCastingTime">***PowerCastingTime***</a> | Время активации умения, заданного опцией [*PowerId*](#ref-PowerId).
|| **Прерывание команды (категория "Interruptions")**
|<a name ="ref-StopOnApproached">***StopOnApproached***</a> | Флаг, завершающий выполнение команды после того как персонаж приблизился к целевой *Entity* на расстояние [*CombatDistance*](#ref-CombatDistance).
|<a name ="ref-EntitySearchTime">***EntitySearchTime***</a> | Время поиска в миллисекундах, в течение которого бот пытается обнаружить заданную *Entity*, удовлетворяющую критериям поиска.<br/> Команда прерывается, если до истечения заданного времени *Entity* не будет обнаружен.<br/> Опция отключается при установке значения ``0``. При этом поиск продолжается неограниченное время.
|| **Прочие опции**|
|<a name ="ref-ResetCurrentHotSpot">***ResetCurrentHotSpot***</a> | Флаг, предписывающий двигаться к ближайшему *HotSpot*'у после исчезновения (уничтожения) всех видимых целевых *Entity*.<br/> Если флаг не установлен, бот "запоминает" последний *HotSpot*, к которому двигался перед обнаружением *Entity*, и после уничтожения всех видимых *Entity* (их исчезновения), продолжает движение к этому *HotSpot'у*.

---

# **Внутренние условия**

Перед запуском команды проверяется истинность следующих условий:
1) Персонаж находится на карте [*CurrentMap*](#ref-CurrentMap), если задана соответствующая опция.
2) Персонаж находится в области, заданной опцией [*CustomRegions*](#ref-CustomRegions), если установлен флаг опцией [*CustomRegionsPlayerCheck*](#ref-CustomRegionsPlayerCheck).
3) Кроме того, должно быть истинным одно из условий:
   - Задан идентификатор [*EntityID*](#ref-EntityID).
   - Опция [*EntityNameType*](#ref-EntityNameType) имеет значение *Empty*.

---

# **Завершение команды**
Команда завершается в следующих случаях:
1) Персонаж приблицился к заданному *Entity*, при условии, что задан флаг [*StopOnApproached*](#ref-StopOnApproached).
2) Истекло время поиска *Entity*, заданное опцией [*EntitySearchTime*](#ref-EntitySearchTime).
3) [Внутренние условия](#внутренние-условия) стали ложны.

Если опции [*StopOnApproached*](#ref-StopOnApproached) и [*EntitySearchTime*](#ref-EntitySearchTime) не заданы, то команда выполняется до тех пор, пока не будет прервана принудительно одним из способов, перечисленных в [статье](ForcedQuesterActionTermination-RU.md).

---

# **Блок-схема**

<p align="center"><img src="diagrams/MoveToEntity.svg"></p>

---

# **Аналоги**

Похожие команды, входящие в базовый функционал бота:
- [***Grind***](Astral-Actions-RU.md#ref-Grind).

---

<a href="javascript:history.back()">Назад</a>  
[Назад к перечню команд](../EntityTools-QuesterExtensions-RU.md#ref-Actions)  
[Назад к содержанию](../../index.md)