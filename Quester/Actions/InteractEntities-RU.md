# **InteractEntities**

Команда предназначена для патрулирования по маршруту, заданному набором точек *HotSpots*, в поисках заданного *Entity* и последующего с ним взаимодействия.

## **Описание алгоритма**
1. Бот перемещается между точками *HotSpots*, производя поиск ближайшего *Entity*, удовлетворяющего критериям поиска. <br/>
   - Патрулирование может производиться в режиме игнорирования боя [*IgnoreCombat*](#ref-IgnoreCombat).<br/>
   - Область поиска *Entity* может быть ограничена опциями [*CustomRegions*](#ref-CustomRegions),  [*ReactionRange*](#ref-ReactionRange) и [*ReactionZRange*](#ref-ReactionZRange).

2. Когда целевое *Entity* найдено, бот следует к нему по кратчайшему пути.   
   - В отличие от штатной команды *InteractNPC* возможно взаимодействие с движущимися *Entity*.
   - В случае, если взаимодействие прервано нападением противников, оно повторяется после выхода из боя.
   - После завершения взаимодействия или исчерпания попыток, целевая *Entity* временно помещается в черный список для предотвращения повторных безуспешных попыток взаимодействия с ним.
  
3. После исчезновения всех *Entity*, удовлетворяющих критериям поиска, бот возобновляет патрулирование. 

---

# **Настройки команды**

| **Наименование** | **Описание** 
|:-----------------|:-------------
||**Настройки идентификации *Entity* (категория "Entity")**
|<a name ="ref-EntityID">***EntityID***</a><br/><a name ="ref-EntityIdType">***EntityIdType***</a><br/><a name ="ref-EntityNameType">***EntityNameType***</a><br/><a name ="ref-EntityID">***EntitySetType***</a> | Идентификация *Entity* производится сочетанием четырех перечисленных слева свойств, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification-RU.md).
||**Дополнительные фильтры *Entity* (категория "Entity Search Options")**
|<a name ="ref-HealthCheck">***HealthCheck***</a> | Дополнительная проверка уровня здоровья *Entity* (HP).<br/>- ***True*** : Игнорируются *Entity* с нулевым количеством очков здоровья (HP) либо, имеющие флаг ***IsDead***;<br/>- ***False*** : Здоровье *Entity* (HP) не проверяется.
|<a name ="ref-HoldTargetEntity">***HoldTargetEntity***</a> | Флаг удержания *Entity*.<br/>- ***True*** : Бот продолжает следовать к ранее найденному *Entity*, даже в том случае, если будет обнаружено *Entity* поближе;<br/>- ***False*** : Бот постоянно производит поиск и следует к ближайшему *Entity*.
||**Область поиска *Entity* (категория "Search Area")**
|<a name ="ref-ReactionRange">***ReactionRange***</a> | Максимальное допустимое расстояние от *Entity* до персонажа. *Entity* на большем расстоянии игнорируются.<br/> Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.
|<a name ="ref-ReactionZRange">***ReactionZRange***</a> | Максимальная допустимая разница по высоте (ZAxis) между *Entity* и персонажем. *Entity* игнорируются, если находятся выше (ниже) заданной величины относительно персонажа. <br/> Опция отключается при установке значения ``0``. При этом поиск производится среди всех видимых боту *Entity*.
|<a name ="ref-RegionCheck">***RegionCheck***</a> | Флаг, активирующий дополнительную проверку внутриигрового региона (не то же самое, что *CustomRegion*), в котором находится *Entity*.<br/>- ***True*** : Поиск *Entity* производится в том же регионе, в котором находится персонаж;<br/>- ***False*** : Проверка региона при поиске *Entity* не производится.
|<a name ="ref-CustomRegions">***CustomRegions***</a> | Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustomRegionSet](../../General/CustomRegionSet-RU.md).
|| **Опции взаимодействия (категория "Interaction")**
|<a name ="ref-Dialogs">***Dialogs***</a> | Ответы в окне диалога с *Entity*.
|<a name ="ref-InteractDistance">***InteractDistance***</a> | Максимальное допустимое расстояние, на котором возможно взаимодейтсвие с целевой *Entity*. <br/> В пределах заданного расстояния также отключается режим игнорирования боя, если задан флаг [*IgnoreCombat*](#ref-IgnoreCombat). <br/> При установке значения более ``5`` на [Mapper](../../Patches/Mapper/Mapper-RU.md) соответствующая область отображается окружностью, центром которой является целевая *Entity*.
|<a name ="ref-InteractTime">***InteractTime***</a> | Время взаимодействия в миллисекундах.
|<a name ="ref-InteractOnce">***InteractOnce***</a> | Флаг,  запрещающий повторное взаимодействие с *Entity*. После взаимодействия *Entity* бессрочно помещается в черный списо.
|<a name ="ref-InteractionTimeout">***InteractionTimeout***</a> | Время запрета на повторное взаимодействие с *Entity*. Опция игнорируется если установлен флаг [*InteractOnce*](#ref-InteractOnce)
|| **Управление боем (категория "Manage Combat Options")**
|<a name ="ref-IgnoreCombat">***IgnoreCombat***</a> | Флаг, предписывающий активировать режим игнорирования боя *IgnoreCombat* при следовании к целевой *Entity*.
|<a name ="ref-IgnoreCombatCondition">***IgnoreCombatCondition***</a> | Дополнительное условие, управляющее режимом прерывания боя. Если условие на выполняется, то режим игнорирования боя не активируется.
|<a name ="ref-IgnoreCombatMinHP">***IgnoreCombatMinHP***</a> | Величина минимального здоровья персонажа HP (в процентах), при котором может быть активирован режим игнорирования боя. Если здоровье персонажа опустится ниже указанной величины, то персонаж вступи в бой.<br/>При значении -1 команда не меняетт системное значение **IgnoreCombatMinHP** при активации режима игнорирования боя.
|<a name ="ref-AbortCombatDistance">***AbortCombatDistance***</a> | Расстояние от *Entity*, за пределами которого бой принудительно прерывается. <br/> Бой снова активируются на расстоянии [*CombatDistance*](#ref-CombatDistance) от целевой *Entity*. При значении меньшем [*CombatDistance*](#ref-CombatDistance) или при выключенном флаге [*IgnoreCombat*](#ref-IgnoreCombat), опция отключается.
|| **Прерывание команды (категория "Interruptions")**
|<a name ="ref-EntitySearchTime">***EntitySearchTime***</a> | Время поиска в миллисекундах, в течение которого бот пытается обнаружить заданную *Entity*, удовлетворяющую критериям поиска.<br/> Команда прерывается, если до истечения заданного времени *Entity* не будет обнаружен.<br/> Опция отключается при установке значения ``0``. При этом поиск продолжается неограниченное время.
|| **Прочие настройки (категория "Optional")**
|<a name ="ref-ResetCurrentHotSpot">***ResetCurrentHotSpot***</a> | Флаг, предписывающий двигаться к ближайшему *HotSpot*'у после взаимодействия со всеми видимыми целевыми *Entity* (их исчезновения).<br/> Если флаг не установлен, бот "запоминает" последний *HotSpot*, к которому двигался перед обнаружением *Entity*, и, после взаимодействия со всеми видимыми *Entity* (их исчезновения), продолжает движение к этому *HotSpot'у*.

---

# **Внутренние условия**

Перед запуском команды проверяется истинность одного из условий:
- Задана опция [*EntityID*](#ref-EntityID).
- Опции [*EntityNameType*](#ref-EntityNameType) имеет значение *Empty*.

---

# **Завершение команды**

Команда самостоятельно не завершается, если не задан флаг [*StopOnApproached*](#ref-StopOnApproached).

Принудительное завершение команды возможно одним из способов, перечисленных в [статье](ForcedQuesterActionTermination-RU.md).

---

# **Аналоги**

Похожие команды, входящие в базовый функционал бота:
- [***InteractNPC***](Astral-Actions-RU.md#ref-InteractNPC);
- [***FollowNPC***](Astral-Actions-RU.md#ref-FollowNPC).

---

# **Блок-схема**

<p align="center"><img src="diagrams/InteractEntities.svg"></p>

---

<a href="javascript:history.back()">Назад</a>  
[Назад к перечню команд](../EntityTools-QuesterExtensions-RU.md#ref-Actions)  
[Назад к содержанию](../../index.md)