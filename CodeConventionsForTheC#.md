# Стиль кода C#

<style>
.text-center {
  text-align: center;
}
</style>

#### Интерфейсы:

**ISum.cs**
```c#
public interface ISum
{
    /// <summary>
    /// Описание интерфейса
    /// </summary>
    void SumTwoAndTwo();
}
```

#### Классы:

**Example.cs**

```c#
//Здесь не должно быть неиспользуемых пространств имен
using System;

/// <summary>
/// Здесь должно быть осмысленное описание класса
/// </summary>
public class Example: ISum
{
    /// <summary>
    /// Константы капсом с underscore
    /// </summary>
    const decimal PI = 3.14m;
-> Между описаниями переменных в классе оставляем пустые строки, не лепим простыню без разрывов

    /// <summary>
    /// Приватные поля со знака подчеркивания и camelCase
    /// </summary>
    private int _iAmHidden;

    /// <summary>
    /// Публичные свойства с заглавной, автогенерируемые getter, setter можно писать в одну строку
    /// </summary>
    public int SomeValue { get; set; }

    /// <summary>
    /// Название метода должно начинаться с глагола, с заглавной буквы
    /// </summary>
    /// <remarks>
    /// Если описание метода получается длинным или имеет какие-то особенности,
    /// то используем данный раздел
    /// </remarks>
    /// <param name="value">Описываем аргументы метода</param>
    /// <returns>Описываем возвращаемое значение, если оно не является избыточным</returns>
    protected int DoSomething(int value)
    //особое внимание на переносы скобок и табуляции
    {
        // Локальные переменные со строчной буквы
	    // Вместо указания явного типа используем var, за исключением ситуаций, где
	    // указание явного типа требуется
        var localVariable = value + 1;
    }

    /// <summary>
    /// Суммирует 2 и 2
    /// </summary>
    public void SumTwoAndTwo()
    {
        var a = 2 + 2;
    }
}
```

#### Перечисления:

**SensorSource.cs**

```c#
/// <summary>
/// Название в единственном числе
/// </summary>
public enum SensorSource: byte
{
    /// <summary>
    /// Осмысленный комментарий
    /// </summary>
    Undefined = 0, // Стремимся указывать с 0 и последовательно для оптимизации работы перечислений

    /// <summary>
    /// Осмысленный комментарий
    /// </summary>
    Historian = 1  //в явном виде указать число, чтобы не было проблем с приведением типов
}
```

Фигурные скобки: начинаются с новой строки

```c#
private int GetValue()
{
…
}
```

Отступы делаются пробелами, чтобы во всех системах читалось одинаково. Многие IDE поддерживают замену табуляции на пробелы, т.е. в настройках указать сколькими пробелами будет заменяться табуляция и при дальнейшем нажатии клавиши TAB произойдёт вставка N пробелов.

## Правила оформления

1. Скобки после return не нужны

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| return (a + b + c); | return a + b + c;     |

2. Используйте var

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| string s = "abc";   | var s = "abc";        |

3. Все названия на английском языке (используйте переводчик при затруднениях)

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| var procent = 0.05; | var percent = 0.05;   |
| string[] stroki;    | string[] lines;       |

4. Yазвания переменных должны быть осмысленными. Чем больше область видимости, тем развернутее должно быть название

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| var p = 0.05;       | var percent = 0.05;   |

5. Не используйте of, the и a в названиях

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| ColorOfCar          | CarColor              |
| theSun              | sun                   |
| aStar               | star                  |

6. Булевы переменные называйте в виде вопросов, на которые можно ответить да или нет. Не используйте название flag

| Плохо:              | Хорошо:               |
|---------------------|-----------------------|
| var flag = false;   | var isSorted = false; |

7. Названия переменных в lowerCamelCase

| Плохо:                        | Хорошо:                     |
|-------------------------------|-----------------------------|
| var percent_per_month = 0.05; | var percentPerMonth = 0.05; |
| var PercentPerMonth = 0.05;   |                             |

8. Не оставляйте пустых строк после объявления метода и после return

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
int GetOne()
{<br/>
    return 1;<br/>
}
      </pre>
    </td>
    <td>
      <pre>
int GetOne()
{
    return 1;
}
      </pre>
    </td>
  </tr>
</table>

9. Стирайте неактуальные комментарии

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
int GetOne()
{
    // TODO: Напишите здесь return 1
    return 1;
}
      </pre>
    </td>
    <td>
      <pre>
int GetOne()
{
    return 1;
}
      </pre>
    </td>
  </tr>
</table>

10. Тело if всегда в новой строке. Тело цикла всегда в новой строке.

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
if (a > b) return 0;
      </pre>
    </td>
    <td>
      <pre>
if (a > b)
    return 0;
      </pre>
    </td>
  </tr>
</table>

11. Не смотря на то, что язык позволяет упускать скобки тела при коде в одну строку, необходимо всегда проставлять скобки

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
if (a > b)
    return 0;
      </pre>
    </td>
    <td>
      <pre>
if (a > b)
{
    return 0;
}
      </pre>
    </td>
  </tr>
</table>


12. Не пишите else, если выше везде выходите из тела if

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
if (a > b)
{
   return 10;
}
else 
{
   … 
   return 20;
}
      </pre>
    </td>
    <td>
      <pre>
if (a > b)
{
   return 10;
}

… 
return 20;
      </pre>
    </td>
  </tr>
</table>

13. Пишите одну и ту же строчку два раза - выделите в метод

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
var lenAB = Math.Sqrt((ax-bx)*(ax-bx) + (ay-by)*(ay-by));
var lenBC = Math.Sqrt((bx-cx)*(bx-cx) + (by-cy)*(by-cy));
      </pre>
    </td>
    <td>
      <pre>
double GetLength(
    double ax,
    double ay,
    double bx,
    double by)
{
    return Math.Sqrt((ax-bx)*(ax-bx) + (ay-by)*(ay-by));
}

…

var lenAB = GetLength(ax, ay, bx, by);
var lenBC = GetLength(bx, by, cx, cy);
      </pre>
    </td>
  </tr>
</table>

14. Не сравнивайте bool c константой с помощью ==

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
if (success == true)

…

if (success == false)
      </pre>
    </td>
    <td>
      <pre>
if (success)

…

if (!success)
      </pre>
    </td>
  </tr>
</table>

15. Названия методов в UpperCamelCase

| Плохо:                            | Хорошо:                          |
|-----------------------------------|----------------------------------|
| public static double get_length() | public static double GetLength() |
| public static double getLength()  |                                  |

16. Названия методов должно начинаться с глагола

| Плохо:                            | Хорошо:                          |
|-----------------------------------|----------------------------------|
| public static double Length()     | public static double GetLength() |

17. Используйте множественное число в названии коллекций

| Плохо:                            | Хорошо:                          |
|-----------------------------------|----------------------------------|
| Apple[] Apple                     | Apple[] Apples                   |

18. Не пишите тип коллекции в названии. Исключение, если есть коллекция другого типа с теми же данными

| Плохо:                            | Хорошо:                          |
|-----------------------------------|----------------------------------|
| Orange[] ArrayOfOranges           | Orange[] Oranges                 |
| List<Apple> AppleList             | List<Apple> Apples               |

19. Всегда явно указывайте модификаторы доступа

| Плохо:                            | Хорошо:                          |
|-----------------------------------|----------------------------------|
| class Vector                      | public class Vector              |

20. Соблюдайте порядок элементов внутри класса.
Сначала поля и свойства, потом конструктор, затем методы.

21. Между методами оставляйте пустую строку

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
public static void DoSomething()
{
    ...
}
public static void DoSomethingElse()
{
    ...
}
      </pre>
    </td>
    <td>
      <pre>
public static void DoSomething()
{
    ...
}

public static void DoSomethingElse()
{
    ...
}
      </pre>
    </td>
  </tr>
</table>

22. После for, if, … ставьте пробел

| Плохо:            | Хорошо:            |
|-------------------|--------------------|
| if(a > b) ...     | if (a > b) ...     |

23. Обрамляйте арифметические, логические операторы, оператор присваивания пробелами

| Плохо:            | Хорошо:            |
|-------------------|--------------------|
| if (a>b) c=0;     | if (a > b) c = 0;  |

24. Правильно переносите длинный тернарный оператор

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
return needAutocomplete ? Сommand.AutoComplete : Command.Ignore;
      </pre>
    </td>
    <td>
      <pre>
return needAutocomplete
    ? Сommand.AutoComplete
    : Command.Ignore;
      </pre>
    </td>
  </tr>
</table>

25. Переносите выражения так, чтобы новая строка начиналась с оператора

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
if (longExpression &&
    anotherExpression)
      </pre>
    </td>
    <td>
      <pre>
if (longExpression
   && anotherExpression)
      </pre>
    </td>
  </tr>
</table>

26. Для записи однострочных свойств используйте сокращённую форму

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
public int Length
{
    get {return bytes.Length;}
}
      </pre>
    </td>
    <td>
      <pre>
public int Length => bytes.Length;
      </pre>
    </td>
  </tr>
</table>

27. При записи длинной цепочки вызовов методов пишите каждый вызов в новой строке

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
return lines.Where(...)
    .Select(...)...
      </pre>
    </td>
    <td>
      <pre>
return lines
    .Where(...)
    .Select(...)
    ...
      </pre>
    </td>
  </tr>
</table>

28. Кортежи делаем именованные для увеличения читаемости

| Плохо:                       | Хорошо:                                |
|------------------------------|----------------------------------------|
| (double, int) t1 = (4.5, 3); | (double Sum, int Count) t2 = (4.5, 3); |

29. Котрежи оформляем с заглавной буквы

| Плохо:                                 | Хорошо:                                |
|----------------------------------------|----------------------------------------|
| (double sum, int count) t1 = (4.5, 3); | (double Sum, int Count) t2 = (4.5, 3); |