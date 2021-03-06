# **Ауры**

<a name = "ref-Aura">***Аура (Aura)***</a> - это любой усиливающий (баф) или ослабляющий (дебаф) эффект наложенный на персонажа и других *Entity*.

# <a name = "ref-AuraViewer"></a> **Окно AuraViewer**

В плагине **EntityTools** реализованно модифицированное окно просмотра списка аур.
<!-- , который с помощью патча заменяет [штатный *Mapper*](https://www.neverwinter-bot.com/forums/viewtopic.php?p=43909#p43909) бота Астрал. -->

|Штатный AuraDetector|Модифицированный AuraViewer|
|:-----:|:--------------:|
|![AuraDetector](img/AuraViewer/AuraDetector.png)|![AuraViewer](img/AuraViewer/AuraViewer.png)|

1. Вверху окна справа от метки ``Select entity which to search an Aura`` расположен переключатель, позволяющий выбрать объект, ауры которого исследуются:
   - **Player** - персонаж;
   - **Target** - цель персонажа;
   - **Entity** - *Entity*, выбранный в окне [*EntityViewer*](EntityIdentification-RU.md).  
   В строке ниже отображается [InternalName](EntityIdentification-RU.md#ref-Entity-InternalName) выбранного объекта исследования.
3. В центре окна расположен список аур, наложенных на объект исследования.   
   В начале указывается локализованное название ауры (*DisplayName*), а в квадратных скобках - её внутриигровой идентификатор (*InternalName*).   
   В обычном режиме после изменения объекта исследования или фильтров необходимо нажать кнопку ``Reload``, чтобы обновить список аур.  
5. Под списком аур выводится внутриигровое описание выбранной ауры (если оно имеется).
2. Над списком аур ниже метки ``Filters`` расположены два текстовых поля редактирования:
   - Слева - фильтр <a name = "ref-Filter-DisplayName"></a>**DisplayName**, задающий часть локализованного (русифицированного) имени ауры, которую необходимо найти.
   - Справа - фильтр <a name = "ref-Filter-InternalName"></a>**InternalName**, задающий часть внутриигрового идентификатора ауры, которую необходимо найти.  
   Указанные фильтры позволяют скрыть в списке ауры, не содержащие текст, заданный в соответствующих полях редактирования.  
   В списке будут отображены ауры, удовлетворяющие обоим фильтрам.  
   В обычном режиме после изменения фильтра необходимо нажать кнопку ``Reload``, чтобы обновить список аур.
4. Опция ``Display new auras only``, расположенная над полем редактирования фильтров, включает динамический режим отслеживания ауры.  
   При этом в список будут автоматически добавляться только новые ауры, наложенные на объект исследования **ПОСЛЕ** активации данного режима.  
   Этот режим удобен для поиска ауры, накладываемой определенным умением персонажа.  
   Нажатие кнопки ``Reload`` очистит список и он начнет заполняться снова.
6. В нижней части окна находится пара кнопок:
   - ``Reload`` обновляет список аур, после выбора объекта исследования или изменения фильтров.
   - ``Select`` копирует идентификатор выбранной ауры в буфер обмена и закрывает окно.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к содержанию](../index.md)
