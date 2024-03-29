# **Алгоритм обработки UCC-профиля**

После вступления персонажа в бой и активации подсистемы [**Universal Combat Class**](https://www.neverwinter-bot.com/forums/viewtopic.php?f=150&t=8020) (Далее - *UCC*), бот перебирает набор [*ucc-команд*](EntityTools-UccExtensions-RU.md#ref-Actions) с начала (сверху) до конца (вниз), и активирует их, если выполняются соответсвующие им условия (внутренние и внешние). Эти действия повторяются до тех пор, пока персонаж находится в бою. Это называется **БОЕВОЙ ЦИКЛ**.  

Откаты, дальность умения, наличие очков действия (ОД для Ежедневок) учитывается ботом самостоятельно и вносить их в список условий не нужно.

Перед попыткой активации [*ucc-команды*](EntityTools-UccExtensions-RU.md#ref-Actions) проверяются:

- **внешние** [*ucc-уcловия*](EntityTools-UccExtensions-RU.md#ref-Condtions), добавленные к [*ucc-команде*](EntityTools-UccExtensions-RU.md#ref-Actions) вручную через специальный интерфейс;  
- **внутренние** условия, "встроенные" в [*ucc-команду*](EntityTools-UccExtensions-RU.md#ref-Actions). К ним относятся наличиет ОД, расстояние до цели, кулдауны(откаты), наличие классового ресурса и прочее.

Если вышеуказанные условия выполняются, то [*ucc-команда*](EntityTools-UccExtensions-RU.md#ref-Actions) активируется, а бот начинает обработку с первой команды текущего набора команд, то есть **БОЕВОЙ ЦИКЛ** начинается с начала.
В противном случае [*ucc-команда*](EntityTools-UccExtensions-RU.md#ref-Actions) пропускается и бот анализирует следующую.

Команды активации умений, не изученных у данного персонажа, помечаются в редакторе словами "Unknown spell" и в бою пропускаются.  
Команды активации умений неэкипированных умений (без префикса [Slotted]) также пропускаются.

При выполнении команды [***UCCActionPack***](Actions/UCCActionPack-RU.md) для всех вложенных [*ucc-команд*](EntityTools-UccExtensions-RU.md#ref-Actions) проверяются связанные с ними условия и производится попытка их активации.  
По умолчанию обработка последовательности вложенных команд не прерывается в результате успешной активации предыдущей *ucc-команды* как в обычном порядке, то есть **БОЕВОЙ ЦИКЛ** не прерывается и не начинается сначала.

Таким образом, самые важные [*ucc-команды*](EntityTools-UccExtensions-RU.md#ref-Actions) **НЕОБХОДИМО** поместить в начале (сверху) набора (Ежедневные умения, Уклонения и умения защиты).  
[*UCC-команды*](EntityTools-UccExtensions-RU.md#ref-Actions) не требующие соблюдения каких-либо условий (свободные умения) нужно размещать в конце набора, в противном случае персонаж зациклится на такой [*ucc-команде*](EntityTools-UccExtensions-RU.md#ref-Actions) и следующие за ней никогда не будут применяться.

---

Порядок обработки набора *ucc-команды* для режима патрулирования (*Patrol*) очень похож на вышеуописанный и отличается тем, что **БОЕВОЙ ЦИКЛ** повторяется лишь один раз в 10 (Десять) секунд.  
Следует отметить, что в [***Лаунчер***](https://discord.com/channels/463954532221845535/498815693546979328) встроен патч *PatrolePause*, активация которого уменьшает до 200 (Двухсот)миллисекунд интервал между запусками обработки набора *ucc-команд* в режиме патрулирования (*Patrol*).

---

Пример обработки ucc-профиля боевой подсистемой бота приведен [*в отдельной статье*](UccActionPlayerExample-RU.md).

---

<p align="center"><img src="diagrams/UccAlgorithm-RU.svg"></p>

---

<a href="javascript:history.back()">Назад</a>  
[Назад к содержанию](../index.md)
