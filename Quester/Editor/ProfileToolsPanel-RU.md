# **Панель инструментов профиля**

<p align="center"><img src="img/ProfilePanelButton.png"></p>

На панели расположены следующие кнопки:

![Undo](icons/Undo.png) **Undo** : Отмена изменений, внесенных в *quester-профиль* в порядке, обратном их совершению.  
В настоящий момент отслеживаются лишь часть операций, такик как удаление [*команд*](../EntityTools-QuesterExtensions-RU.md#ref-Actions), [*условий*](../EntityTools-QuesterExtensions-RU.md#ref-Condition), [*CustomRegion*](CustomRegionsPanel-RU.md)'ов, [*HotSpots*](HotSpostPanel-RU.md)'ов, [*торговцев*](VendorsPanel-RU.md), [*игнорируемых врагов*](BlackListPanel-RU.md) и некоторых других.
При сохранении *quester-профиля* очередь отмены очищается.

---

![NewProfile](icons/New.png) **New Profile** : Создание нового пустого *quester-профиль*.

![OpenProfile](icons/Open.png) **Open Profile** : Загрузка существующего *quester-профиль* из файла.

![SaveProfile](icons/Save.png) **Save Profile** : Сохрание редактируемого *quester-профиль* в файл.  
Если профиль новый, перед сохранением открывается диалоговое окно, в котором необходимо указать имя файла.
Если полный путь к файлу редактируемого *quester-профиля* совпадает с полным путем к исполняемому в текущий момент *quester-профилем* автоматически производится [выгрузка профиля в исполнительный движок бота](#ref-UploadProfile).  

![SaveAsProfile](icons/SaveAs.png) <a name="ref-SaveAs"></a>**Save Profile as...** : Сохранение редактируемого *quester-профиль* в новый файл.  
Перед сохранением открывается диалоговое окно, в котором необходимо указать имя файла.

---

![UploadProfile](icons/Import.png) <a name="ref-UploadProfile"></a>**Upload to Quester** : Выгрузка редактируемого *quester-профиль* в исполнительный движок бота.  
Одним из ключевых моментов при разработке модифицированного *quester-редактора* является независимость редактируемого *quester-профиля* от активного (исполняемого) ботом *quester-профиля*, управляющего действиями игрового персонажа в текущий момент.  
Для того чтобы внесенные изменения отразились на поведение персонажа в игре, требуется выгрузить редактируемый *quester-профиль* в исполнительный движок бота.
Перед выгрузкой все внесеныне в *quester-профиль* изменения сохраняются в файл на диске, бот останавливается, а затем измененный профиль загружается в в исполнительный движок бота.

![UploadProfile](icons/ImportTo.png) <a name="ref-UploadProfile"></a>**Upload and focuse selected Action** : Выгрузка редактируемого *quester-профиль* в исполнительный движок бота и установка выделенной в редакторе [*команды*](../EntityTools-QuesterExtensions-RU.md#ref-Actions) в качестве активной.  

---

![OpenMapper](icons/Road.png) **Open Mapper** : Открытие инструмента картографирования ([*Mapper*](../../Patches/Mapper/Mapper-RU.md)).

![OpenMissionMonitor](icons/Quest.png) **Open MissionMonitor** : Открытие инструмента мониторинга миссий ([*MissionMonitor*](../../MainPanel/MissionMonitor-RU.md)).

![OpenEntityViewer](icons/NPC.png) **Open EntityViewer** : Открытие обозревателя игровых сущностей ([*EntityViewer*](../../General/EntityIdentification-RU.md#ref-EntityViewer)).

![OpenAuraViewer](icons/EvilEye.png) **Open AuraViewer** : Открытие обозревателя аур ([*AuraViewer*](../../MainPanel/AuraViewer-RU.md)).

---

<a href="javascript:history.back()">Назад</a>  
[Назад к содержанию](../../index.md)