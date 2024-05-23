# Стиль кода WEB (TS, Angular, HTML/CSS)

<style>
.text-center {
  text-align: center;
}
</style>

## TypeScript:

1. При объявлении переменных указываем её тип, даже если его можно упустить (исключением являются переменные для чтения)

| Плохо:              | Хорошо:                      |
|---------------------|------------------------------|
| public size = 5;    | public size: number = 5;     |
| private apple;      | private apple: Apple;        |

2. В случае объявлении переменных только для чтения, которая не должна изменяться даже в конструкторе, то её тип не указывается

| Плохо:                                   | Хорошо:                          |
|------------------------------------------|----------------------------------|
| private readonly FILE_SIZE: number = 10; | private readonly FILE_SIZE = 10; |

3. При объявлении метода явно указываются типы данных его аргументов и тип возвращаемого значения

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
public changeDisplay (status) {
  …
}
      </pre>
    </td>
    <td>
      <pre>
public changeDisplay (status: boolean): void {
  …
}
      </pre>
    </td>
  </tr>
</table>

4. Для склеивания строк стараемся использовать литерал шаблонной строки

| Плохо:                 | Хорошо:                |
|------------------------|------------------------|
| let str = a + ‘ ’ + b; | let str = `${a} ${b}`; |

5. Используем только let и const, не используем var и не упускаем объявление

| Плохо:                 | Хорошо:                |
|------------------------|------------------------|
| var a = 5;             | let a = 5;             |
| b = 9;                 | let b = 9;             |
|                        | const c = 10;          |

6. Если функция принимает много значений (что стремимся избегать), то её перенос осуществляем следующим образом

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
function foo(bar,
             baz,
             quux) {
  // ...
}
      </pre>
    </td>
    <td>
      <pre>
function foo(
  bar,
  baz,
  quux,
) {
  // ...
}
      </pre>
    </td>
  </tr>
</table>

7. При использовании анонимных функция, используем стрелочную функцию

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});
      </pre>
    </td>
    <td>
      <pre>
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
      </pre>
    </td>
  </tr>
</table>

8. Если стрелочная функция принимает один аргумент и/или состоит из одного действия, то лишние скобки упускаем, если это не ухудшает читаемость

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
[1, 2, 3].map((x) => {
  return x * x;
});
      </pre>
    </td>
    <td>
      <pre>
[1, 2, 3].map(x => x * x);
      </pre>
    </td>
  </tr>
</table>

9. Для возведения в степень используем оператор **

| Плохо:                          | Хорошо:                 |
|---------------------------------|-------------------------|
| const binary = Math.pow(2, 10); | const binary = 2 ** 10; |

## Angular:

1. Во всех файлах указываем отступ в два пробела

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
@Component({
    selector: 'app-cell',
    templateUrl: './cell.component.html',
    styleUrls: ['./cell.component.scss']
})
      </pre>
    </td>
    <td>
      <pre>
@Component({
  selector: 'app-cell',
  templateUrl: './cell.component.html',
  styleUrls: ['./cell.component.scss']
})
      </pre>
    </td>
  </tr>
</table>

2. Для наименования классов в структуре HTML применяем БЭМ

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
<div class="menu">
  ...
  <span class="menuItem"></span>
</div>
      </pre>
    </td>
    <td>
      <pre>
<div class="menu">
  ...
  <span class="menu__item"></span>
</div>
      </pre>
    </td>
  </tr>
</table>

3. Все стили для страниц описываем рядом в файле css (scss). В общие же записываем сброс стилей, подключение шрифтов, параметры основной страницы.

4. Все параметры и объекты private readonly пишем в виде UPPER_CASE_SNAKE_CASE

| Плохо:                    | Хорошо:                    |
|---------------------------|----------------------------|
| private readonly maxCount | private readonly MAX_COUNT |

5. Объекты перечислений всегда начинаются с заглавной буквы

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
export enum MonthSeason {
  /** Зима */
  winter = 0
}
      </pre>
    </td>
    <td>
      <pre>
export enum MonthSeason {
  /** Зима */
  Winter = 0
}
      </pre>
    </td>
  </tr>
</table>

6. Для каждой переменной, функции и метода обязательно указываем доступ

| Плохо:                    | Хорошо:                       |
|---------------------------|-------------------------------|
| resetFilter(): void {}    | public resetFilter(): void {} |

7. В конце каждой строки указываем точку с запятой, когда заканчивается конструкция

| Плохо:                         | Хорошо:                         |
|--------------------------------|---------------------------------|
| this.isVisibleHintBox = status | this.isVisibleHintBox = status; |

8. Строки импорта разделяем на две основные группы 
a.	Внешние
b.	Внутренние

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
import { Component } from '@angular/core';
import { ModalWindowType } from 'src/app/models/modal-window-type.enum';
      </pre>
    </td>
    <td>
      <pre>
import { Component } from '@angular/core';

import { ModalWindowType } from 'src/app/models/modal-window-type.enum';
      </pre>
    </td>
  </tr>
</table>

9. Передаваемые объекты между компонентами оформляем в таком виде:

| Плохо:                                   | Хорошо:                                |
|------------------------------------------|----------------------------------------|
| @Input() isOpenVacationsGroup!: boolean; | @Input()                               |
|                                          | public isOpenVacationsGroup!: boolean; |

10. Алиасам перечислений даем имя, как и у самого перечисления

| Плохо:                         | Хорошо:                       |
|--------------------------------|-------------------------------|
| public userLevels = UserLevel; | public UserLevel = UserLevel; |

11. Подключаем сервисам даем такое же имя, только со строчной буквы

| Плохо:                           | Хорошо:                                 |
|----------------------------------|-----------------------------------------|
| public settings: SettingsService | public settingsService: SettingsService |

12. Публичные поля, которые приходят в конструктор оформляем в следующем виде

<table>
  <tr>
    <td class='text-center'><b>Плохо:</b></td>
    <td class='text-center'><b>Хорошо:</b></td>
  </tr>
  <tr>
    <td>
      <pre>
public today: Date;

/**
 * Конструктор для создания настроек приложения
 * @param today сегодняшняя дата
 */
public constructor(
  today: Date
  ) {
  this.today = today;
}
      </pre>
    </td>
    <td>
      <pre>
/**
 * Конструктор для создания настроек приложения
 * @param today сегодняшняя дата
 */
public constructor(
  public today: Date
  ) {
}
      </pre>
    </td>
  </tr>
</table>

13. Наименование файлов пишем через дефис, в конце указываем тип файла
a.	для моделей указывается «model»;
b.	для интерфейсов указывается «interface»;
c.	для перечислений указывается «enum»;
d.	для вспомогательных классов «class».

| Плохо:          | Хорошо:                      |
|-----------------|------------------------------|
| EmployeeSend.ts | employee-send.model.ts       |
| DutyTab.ts      | duty-tab.enum.ts             |
|                 | unique-position.interface.ts |

## HTML под Angular:

1. При большом количестве атрибутов в HTML делаем следующие отступы:
a. Все атрибуты начинаются с новой строки;
b. Если у тега есть значение, то атрибутам добавляется 4 пробела, иначе два.

<b>Плохо:</b>
```
<!--Дни отпуска-->
<div class="employee__vacation-date" [class.employee__vacation-date_dismissal]="employee.isDismissalZUP" [class.employee__position_benefit]="!employee.isDismissalZUP && employee.benefit">
  {{countDaysVacation}}
</div>
```

<b>Хорошо:</b>
```
<!--Дни отпуска-->
<div 
    class="employee__vacation-date"
    [class.employee__vacation-date_dismissal]="employee.isDismissalZUP"
    [class.employee__position_benefit]="!employee.isDismissalZUP && employee.benefit">
  {{countDaysVacation}}
</div>
```

2. При наличии вложенного блока, атрибуты родителя так же отделяем через 4 пробела
3. 
<b>Плохо:</b>
```
<div
  #comboBox
  class="combo-box">
  <div
      class="combo-box-field">
  </div>
</div>
```

<b>Хорошо:</b>
```
<div
    #comboBox
    class="combo-box">
  <div
      class="combo-box-field">
  </div>
</div>
```

3. Логические блоки отделяем пустой строкой и подписываем комментарием

4. Соблюдаем следующий порядок атрибутов:
  * *ngIf или *ngFor (структурные директивы)
  * \#
  * id (идентификатор)
  * class (основной класс)
  * [class.] (классы с условиями)
  * Остальные атрибуты через []
  * События через ()

5. Стремимся не использовать методы в HTML разметки, т.к. это вызывает многочисленные вызовы

<b>Плохо:</b>
```
<p class="calendar__text">
  {{getName()}}
</p>
```

<b>Хорошо:</b>
```
<p class="calendar__text">
  {{nameVacationMonth}}
</p>
```

## CSS

1. Используем препроцессор SCSS
2. Для сортировки свойств используем POSTCSS-SORTING

