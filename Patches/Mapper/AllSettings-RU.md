# **Все настройки Mapper'a**

Активация патча, который подменяет [штатный](https://www.neverwinter-bot.com/forums/viewtopic.php?p=43909#p43909) Mapper, выполняется на панели плагина.  
После активации опции, патч будет применен при следующем запуске бота.

<p align="center"><img src="img/MapperPatch-Activation.png"></p>

Полный список настроек Mapper'a доступен на вкладке ***Settings*** в группе ***Mapper***.  

<p align="center"><img src="img/MapperExt-AllSettings.png"></p>

После выбора опции её описание отобразится внизу окна.

## **Основные**

- <a name="ref-Patch"></a>**Patch** : Активация (деактивация) патча окна Mapper'a.

## **Опции [картографирования](Mapper-MappingTools-RU.md):**
<a name="ref-WaypointDistance"></a> ![WaypointDistance](img/icons/miniNodeDistance.png) **WaypointDistance** : Расстояние между добавляемыми путевыми точками.  
<a name="ref-WaypointEquivalenceDistance"></a> ![WaypointEquivalenceDistance](img/icons/miniDistance.png) **WaypointEquivalenceDistance** : Радиус, в пределах которого точки пути считаются эквивалентными (новые не добавляются).  
<a name="ref-MaxElevationDifference"></a> ![WaypointDistance](img/icons/miniZdiff.png) **MaxElevationDifference** : Максимальная допустимая разница высот между соединяемыми точками пути.  
<a name="ref-ForceLinkingWaypoint"></a> ![ForceLinkingWaypoint](img/icons/miniLink.png) **ForceLinkingWaypoint** : Флаг принудительного связывания с предыдущей точкой пути.  
<a name="ref-LinearPath"></a> ![LinearPath](img/icons/miniLinPath.png) **LinearPath** : Флаг прокладывания линейного пути (без связей с пересекающимися путями).

### <a name="ref-CacheOptions"></a> **Опции кэширования при [картографировании](Mapper-MappingTools-RU.md):**

- <a name="ref-CacheActive"></a> **CacheActive** : Активация кэша путевых точек в режиме прокладывания пути.  
- <a name="ref-CacheRadius"></a> **CacheRadius** : Радиус в пределах которого кэшируются путевые точки.
- <a name="ref-CacheRegenTimeout"></a> **CacheRegenTimeout** : Период времени между обновлениями кэша

## **Настройки окна Mapper'a:**
- <a name="ref-Location"></a> **Location** : Координаты окна на экране монитора.
- <a name="ref-Size"></a> **Size** : Размер окна на экране в пикселях.
- <a name="ref-RedrawMapperTimeout"></a> **RedrawMapperTimeout** : Интервал времени между обновлением (перерисовкой) окна Mapper'a. [Подробнее...](GeneralOptions-RU.md#ref-MeshesCaching)  
- <a name="ref-LayerDepth"></a> **LayerDepth** : Размер слоя по оси Z, отображаемого в окне Mapper'a. [Подробнее...](GeneralOptions-RU.md#ref-ZLimit)  

### **Настройки видимости панелей инструментов:**
- <a name="ref-MappingBarVisible"></a> **MappingBarVisible** : Видимость панели инструментов '[*Mapping Tools*](Mapper-MappingTools-RU.md)'.
- <a name="ref-GraphToolsBarVisible"></a> **GraphToolsBarVisible** : Видимость панели инструментов '[*Graph Tools*](Mapper-GraphTools-RU.md)'.
- <a name="ref-GraphEditToolsBarVisible"></a> **GraphEditToolsBarVisible** : Видимость панели инструментов '[*Graph Edit Tools*](Mapper-EditTools-RU.md)'.
- <a name="ref-CustomRegionBarVisible"></a> **CustomRegionBarVisible** : Видимость панели инструментов '[*CustomRegion Tools*](Mapper-CustomRegionTools-RU.md)'.
- <a name="ref-StatusBarVisible"></a> **StatusBarVisible** : Видимость строки состояния '[*StatusBar*](StatusBar-RU.md)'.

### **[Цвета путевого графа](GeneralOptions-RU.md#ref-MeshesOptions):**


![Bidirectional](img/icons/miniBiPath.png) <a name="ref-BidirectionalPathColor"></a> ***<font color="Maroon">BidirectionalPathColor</font>*** : Цвет двунаправленного пути (BidirectionalPath).  
![Unidirectional](img/icons/miniUniPath.png) <a name="ref-UnidirectionalPathColor"></a> ***<font color="Coral">UnidirectionalPathColor</font>*** : Цвет однонаправленного пути (UnidirectionalPath).  
![Background](img/icons/miniBack.png) <a name="ref-BackgroundColor"></a> ***BackgroundColor*** : Цвет фона.

### **[Цвета объектов](GeneralOptions-RU.md#ref-ObjectsOptions):**
- <a name="ref-DrawEnemies"></a> ***DrawEnemies*** : Отображение врагов.
- <a name="ref-EnemyColor"></a> ***<font color="OrangeRed">EnemyColor</font>*** : Цвет врагов.
- <a name="ref-DrawFriends"></a> ***DrawEnemies*** : Отображение дружественных NPC и Entity.
- <a name="ref-FriendColor"></a> ***<font color="Green">FriendColor</font>*** : Цвет дружественных NPC и Entity.
- <a name="ref-DrawPlayers"></a> ***DrawPlayers*** : Отображение игроков.
- <a name="ref-PlayerColor"></a> ***<font color="LawnGreen">PlayerColor</font>*** : Цвет игроков.
- <a name="ref-DrawOtherNPC"></a> ***DrawOtherNPC*** : Отображение нейтральных NPC и Entity.
- <a name="ref-OtherNPCColor"></a> ***<font color="Grey">OtherNPCColor</font>*** : Цвет нейтральных NPC и Entity.
- <a name="ref-DrawNodes"></a> ***DrawNodes*** : Отображение точек взаимодействия (Node).
- <a name="ref-NodeColor"></a> ***<font color="YellowGreen">NodeColor</font>*** : Цвет точек взаимодействия (Node).
- <a name="ref-DrawSkillNodes"></a> ***DrawSkillNodes*** : Отображение точек проверки талантов (SkillNode).
- <a name="ref-SkillNodeColor"></a> ***<font color="Gold">SkillNodeColor</font>*** : Цвет точек проверки талантов (SkillNode).

---

<a href="javascript:history.back()">Назад</a>  
[Назад к описанию Mapper'a](Mapper-RU.md)  
[Назад к содержанию](../../index.md)