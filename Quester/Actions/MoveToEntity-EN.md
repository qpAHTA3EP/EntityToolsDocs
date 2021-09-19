# **MoveToEntity**
Команда предназначена для патрулирования по *HotSpots* до обнаружения заданного *Entity*, которое может быть принудительно атаковано или сопровождаться

# **Настройки команды**
## **Настройки идентификации *Entity***
Искомое *Entity* задается комбинацией свойств ***EntityID***, ***EntityIdType***, ***EntityNameType***, которые подробно описаны в разделе [Идентификация *Entity*](../../General/EntityIdentification.md)


## **Дополнительные фильтры *Entity* (категория "Optional")**

- ***ReactionRange*** - The maximum distance from the character within which the Entity is searched. The default value is 0, which disables distance checking.
- ***ReactionZRange*** - The maximum ZAxis difference from the withing which the Entity is searched. The default value is 0, which disables ZAxis checking.
- ***RegionCheck*** - Check *Entity*'s ingame Region (Not CustomRegion):
  + *True* : Only Entities located in the same Region as Player are detected;
  + *False* : *Entity*'s Region does not checked during search;
- ***HealthCheck*** - Check if Entity's health greater than zero:;
  + *True* : Only Entities with nonzero health are detected;
  + *False* : *Entity*'s health does not checked during search;
- ***HoldTargetEntity*** - 
   + *True* : Do not change the target Entity while it is alive or until the Bot within ***Distance*** of it;
   + *False* : Constantly scan an area and target the nearest *Entity*.
- ***CustomRegions*** - Набор *CustomRegion*'ов, задающих область поиска *Entity*. Подробное описание приведено в разделе [CustorRegionSet](../../General/CustorRegionSet-RU.md).

## **Опции, модифицирующие поведение (категория "Interruptions")**
### **Управление боем**
- ***IgnoreCombat*** - Enable '***IgnoreCombat***' mode while playing action;
- ***Distance*** - Distance to the *Entity* by which it is necessary to approach. Keep in mind that the distance below 5 is too small to display on the [Mapper](../../Patches/Mapper/Mapper-RU.md).
- ***AbortCombatDistance*** - The battle is aborted outside ***AbortCombatDistance*** radius from the target *entity*. The combat is restored within the ***Distance*** radius. However, this is not performed if the value less than ***Distance*** or ***IgnoreCombat*** is *False*;
- ***AttackTargetEntity*** - 
  + *True* : Clear the list of attackers and attack the target Entity when it is approached. This option is ignored if ***IgnoreCombat*** does not set.
### **Прерывание команды**
- ***StopOnApproached*** - 
  + *True* : Complete an action when the Entity is closer than ***Distance***;
  + *False* : Follow an Entity regardless of its distance.

## **Прочие опции**
- ***ResetCurrentHotSpot*** - Reset current HotSpot after approaching the target *Entity*

[**Вернуться к перечню команд**](../EntityTools-QuesterExtensions-RU.md)