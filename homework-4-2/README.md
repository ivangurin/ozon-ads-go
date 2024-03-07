# Поиск цикла

## Условие задачи

Вам дан неориентированный граф без петель и кратных ребер.
Вам требуется проверить граф на наличия циклов и вывести все вершины, входящие в цикл, в порядке возрастания, если цикл имеется, и -1, если цикл отсутствует. Если циклов несколько, то выведите любой.

{\*} Задача со звездочкой - не используйте в решении рекурсию.

## Входные данные

Все вершины занумерованы натуральными числами, не превышающими 2^31.

В первой строке вводится N — количество ребер, которое также не превышает 2^31.

Последующие N строчек имеют вид: start end, где start и end — номера полянок, которые соединены тропинкой. По тропинке можно пройти в любую сторону.

## Выходные данные

Все вершины, входящие в цикл в порядке возрастания. -1, если цикла нет.

## Пример теста 1

### Входные данные

```
5
5 4
4 1
2 1
3 1
2 4

```

### Выходные данные

```
1 2 4

```

## Пример теста 2

### Входные данные

```
4
6 1
2 3
3 5
1 2

```

### Выходные данные

```
-1

```