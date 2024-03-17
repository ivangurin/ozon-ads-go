# Бэклог

## Условие задачи

Вы работаете над множеством задач, которые постоянно поступают к вам в бэклог. Вы - ответственный работник, и полностью соблюдаете требование руководителя: каждый раз при поступлении новой задачи вы складываете ее в бэклог, а когда наступает время браться за новую задачу, вы берёте ту задачу, у которой наивысший приоритет.

К сожалению, лицензия на продукт, управляющий вашим бэклогом, истекла. У вас остались на руках логи ваших действий в этой системе в хронологическом порядке.

Действия могут быть двух видов.

1. Добавление задачи с id = X в бэклог с приоритетом P. Считается, что чем меньше P, тем выше приоритет. Приоритет 1 выше, чем приоритет 2. Приоритет 0 - наивысший. Например, "239 7" означает, что в бэклог добавлена задача id=239 с приоритетом 7.

2. Взятие задачи в работу. Вы удаляете из бэклога задачу с самым высоким приоритетом. Если таких задач несколько, вы выбираете среди них (среди имеющих самый высокий приоритет) задачу с наименьшим id. Гарантируется, что в момент совершения операции в бэклоге есть хотя бы одна задача. Действие обозначается строкой "-1".

Ваш руководитель пообещал вам, что в ближайшее время новых задач не будет, и вам нужно доделать оставшиеся.

Определите список id задач, которые остались невыполненными. Выведите список id задач в том порядке, в котором их необходимо будет выполнить.

## Входные данные

В первой строке вводится одно целое число N - количество событий в системе. 0≤N≤10^6

Далее идут N строк. Каждая строка может быть одного из двух видов:

1. "Х, P" - где Х - id задачи, P - приоритет задачи. 0≤X,P≤10^6

2. "-1".

## Выходные данные

Массив целых чисел, состоящий из id задач, которые необходимо выполнить.

## Пример теста 1

### Входные данные

```
5
1 1
2 0
-1
3 4
4 2

```

### Выходные данные

```
1 4 3

```

## Пример теста 2

### Входные данные

```
4
1 100
2 0
3 0
-1

```

### Выходные данные

```
3 1

```