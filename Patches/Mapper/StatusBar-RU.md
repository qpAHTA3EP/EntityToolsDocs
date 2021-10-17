# **Строка состояния**

![MappingTools](img/StatusBar.png)

---

![HoldPlayer](img/icons/miniHold.png) <a name="ref-HoldPlayer"></a> **Фокусировка на персонаже**  

При активации данной опции персонаж помещается в центр области, отображаемой в Mapper'e.  
Во время движения персонажа, отображаемая часть путевого графа и окружающего пространства смещается таким образом, чтобы персонаж оставался в центре Mapper'a.

---

![Undo](img/icons/miniUndo.png) **<a name="ref-Undo"></a> Отмена изменений**  
Отмена изменений, произведенных в Mapper'e следующими инструментами:  
![RelocateNodes](img/icons/miniNodeMove.png) [Перемещение путевых точек](Mapper-EditTools-RelocateNodes-RU.md);  
![DeleteNodes](img/icons/miniCancel.png) [Удаление путевых точек](Mapper-EditTools-DeleteNodes-RU.md);  
![EditEdge](img/icons/miniEditEdge.png) [Изменение ребер](Mapper-EditTools-RelocateNodes-RU.md);  
![AddCustomRegion](img/icons/miniAddCR.png) [Добавление CustomRegion](Mapper-CustomRegionTools-Add-RU.md)'a;  
![EditCustomRegion](img/icons/miniEditCR.png) [Изменение CustomRegion](Mapper-CustomRegionTools-Edit-RU.md)'a.

Следует иметь ввиду, что отменить ранее совершенные действия можно лишь до сохранения.


![Save](img/icons/miniSave.png) **<a name="ref-Save"></a> Сохранение изменений**  
Сохранение в файл quester-профиля всех изменений, произведенных в Mapper'e, включая изменение путевого графа и [*CustomRegion*](Mapper-CustomRegionTools-RU.md)'ов.  
Перед сохранением путевой граф [оптимизируется](Mapper-GraphTools-RU.md#ref-Compression).  
Однако, после сохранения изменений ранее совершенные действия [отменить](#ref-Undo) нельзя.  
Hot-key: ``Ctrl+Shift+S``  

---

![Customization](img/icons/miniCustomization.png) **<a name="ref-Save"></a> Настройки отображения** 

Доступ к [панели настроек](GeneralOptions-RU.md).

---

![ZoomIn](img/icons/miniZoomin.png) <a name="ref-Scale"></a> **Масштаб**

Информация о масштабе путевого графа и кнопки изменения масштаба:  
![ZoomIn](img/icons/miniZoomin.png) : Увеличение масштаба.  
![ZoomIn](img/icons/miniZoomout.png) : Уменьшение масштаба. 
Масштаб изменяется в диапазоне 10%-800%.

Изменить масштаб можно прокручивая колесо мыши.  
Двойной клик левой кнопкой мыши на метке с процентами, установит масштаб 250%.

---

## <a name="ref-Info"></a> **Информация**

![Compas](img/icons/miniCompas.png) Трехмерные координаты персонажа в формате `` X,y | Y,y | Z,z ``.  
Если фокусировка на персонаже выключена, отображаются координаты центра экрана.
Следом за двойной разделительной чертой ``||`` отображается средняя скорость перемещения персонажа, измеряемая в игровых футах в секунду (f/s), а в скобках - количество итераций, используемых для вычисления скорости.  

![MouseCoord](img/icons/miniMouse.png) Координаты курсора мыши в игровом пространстве в формате `` X,y | Y,y ``  

![Info](img/icons/miniInfo.png) служебная информация о работе Mapper'a:
- Частота обновления окна Mapper'a - количество кадров в секунду (fps).
- Среднее время формирования изображения в окне Mapper'a в миллисекундах (ms).
- Средняя частота обновления [кэша путевых вершин](GeneralOptions-RU.md#ref-MashesCaching) в секунду (cps).

---

Как любая панель инструментов, строка состояния может быть скрыта.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к описанию Mapper'a](Mapper-RU.md)  
[Назад к содержанию](../../index.md)