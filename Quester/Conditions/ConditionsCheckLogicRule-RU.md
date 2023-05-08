# **Проверка набора условий**

Истинность [*условий*](../EntityTools-QuesterExtensions-RU.md#ref-Conditions), ассоциированных с [*командой*](../EntityTools-QuesterExtensions-RU.md#ref-Actions), проверяется перед запуском данной команды.

По-умолчанию истиными должны быть все [*условий*](../EntityTools-QuesterExtensions-RU.md#ref-Conditions), то есть должна выполняться **конъюнкция** (логическое **И**).  

Если у [*команды*](../EntityTools-QuesterExtensions-RU.md#ref-Actions) установлен флаг ***OnlyOneConditionMustBeGood***, тогда действует следующий порядок проверки условий:  
* истиными должны быть все условия, помеченные флагом ***Locked*** (далее - залоченное условие), то есть выполняться **конъюнкция** (логическое **И**);
* истиной должна быть хотя бы одна команда, не помеченная флагом ***Locked***, то есть выполняться **дизъюнкция** (логическое **ИЛИ**).  

---

## <a name="ref-"></a>**Примеры**

Для наглядности условие с ``Loked = False`` будет записаны в круглых скобках **(УСЛОВИЕ_1)**, а залоченное условие ``Loked = True`` - в квадратных скобках <b><font color=green>[УСЛОВИЕ_1]</font></b>:  

### **Пример 1**  

* УСЛОВИЕ_1 (Loked=<font color=blue>False</font>)
* УСЛОВИЕ_2 (Loked=<font color=blue>False</font>)
* УСЛОВИЕ_3 (Loked=<font color=blue>False</font>)
* УСЛОВИЕ_4 (Loked=<font color=blue>False</font>)

В данном случае при ``PlayWhileConditionsAreOk = False`` совокупность условий будет проверяться по правилу <b><font color=red>И</font></b>: истино, если **ВСЕ** условия истины.

<b>(УСЛОВИЕ_1) <font color=red>И</font> (УСЛОВИЕ_2) <font color=red>И</font> (УСЛОВИЕ_3) <font color=red>И</font> (УСЛОВИЕ_4)</b>

При ``PlayWhileConditionsAreOk = True`` совокупность условий будет проверяться по правилу <b><font color=blue>ИЛИ</font></b>: истино, если хотя бы одно условие истино.

<b>(УСЛОВИЕ_1) <font color=blue>ИЛИ</font> (УСЛОВИЕ_2) <font color=blue>ИЛИ</font> (УСЛОВИЕ_3) <font color=blue>ИЛИ</font> (УСЛОВИЕ_4)</b>

---

### **Пример 2**  

* <font color=green>УСЛОВИЕ_1</font> (Loked=<font color=red>True</font>)  
* УСЛОВИЕ_2 (Loked=<font color=blue>False</font>)  
* <font color=green>УСЛОВИЕ_3</font> (Loked=<font color=red>True</font>)  
* УСЛОВИЕ_4 (Loked=<font color=blue>False</font>)  

В данном случае при ``PlayWhileConditionsAreOk = False`` ничего не меняется, совокупность условий будет проверяться по правилу <b><font color=red>И</font></b>: истино, если **ВСЕ** условия истины.

<b>{ <font color=green>[УСЛОВИЕ_1]</font> <font color=red>И</font> <font color=green>[ УСЛОВИЕ_3 ]</font> } <font color=red>И</font> { (УСЛОВИЕ_2) <font color=red>И</font> (УСЛОВИЕ_4) }</b>

При ``PlayWhileConditionsAreOk = True`` совокупность условий будет проверяться по **смешанному правилу**: истино, если истины оба условия 1, 3 и хотя бы одно из условий 2 или 4.

<b>{ <font color=green>[УСЛОВИЕ_1]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_3]</font>} <font color=red>И</font> { (УСЛОВИЕ_2) <font color=blue>ИЛИ</font> (УСЛОВИЕ_4) }</b>  

---

### **Пример 3**  

* <font color=green>УСЛОВИЕ_1</font> (Loked=<font color=red>True</font>)  
* <font color=green>УСЛОВИЕ_2</font> (Loked=<font color=red>True</font>)  
* <font color=green>УСЛОВИЕ_3</font> (Loked=<font color=red>True</font>)  
* УСЛОВИЕ_4 (Loked=<font color=blue>False</font>)  

В данном случае независимо от значения флага **PlayWhileConditionsAreOk** совокупность условий будет проверяться по правилу <b><font color=red>И</font></b>: истино, если **ВСЕ** условия истины.  

<b>{ <font color=green>[УСЛОВИЕ_1]</font> И <font color=green>[УСЛОВИЕ_2]</font> И <font color=green>[УСЛОВИЕ_3]</font> } И { (УСЛОВИЕ_4) }</b>

---

### **Пример 4** 
* <font color=green>УСЛОВИЕ_1</font> (Loked=<font color=red>True</font>)
* <font color=green>УСЛОВИЕ_2</font> (Loked=<font color=red>True</font>)
* <font color=green>УСЛОВИЕ_3</font> (Loked=<font color=red>True</font>)
* <font color=green>УСЛОВИЕ_4</font> (Loked=<font color=red>True</font>)

В данном случае при ``PlayWhileConditionsAreOk = False`` ничего не меняется, и совокупность условий будет проверяться по правилу <b><font color=red>И</font></b>: истино, если **ВСЕ** условия истины.  

<b>{ <font color=green>[УСЛОВИЕ_1]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_2]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_3]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_4]</font> } .</b>

Если ``PlayWhileConditionsAreOk = True`` проверка  <b><font color=red>ВСЕГДА</font></b> выдает **ложный результат**, даже если все из условий 1-4 будут истины.  

<b>{ <font color=green>[УСЛОВИЕ_1]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_3]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_2]</font> <font color=red>И</font> <font color=green>[УСЛОВИЕ_4]</font> } <font color=red>И</font> <font color=purple>{ПУСТОЕ_МНОЖЕСТВО_УСЛОВИЙ</font> }</b>  

В данном случае <b><font color=purple>ПУСТОЕ_МНОЖЕСТВО_УСЛОВИЙ</font></b> с опушенным флагом **Loked** бот оценивает как **ЛОЖЬ**.

---

<a href="javascript:history.back()">Назад</a>  
[Назад к содержанию](../../index.md)