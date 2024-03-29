# Min-Hash

## Условие задачи

Разработчик Саша экспериментирует со способами оптимизировать поиск похожих товаров в поисковом движке, и во имя науки решил воспользоваться алгоритмом [MinHash](hhttps://en.wikipedia.org/wiki/MinHash).

Для простоты экспериментов он взял следующую базовую хеш-функцию от строки S=(s1,...,sl), состоящей из l символов (ASCII-символы с кодом x в диапазоне 33≤x≤126) с параметром k:

Hk(s0,…,sl)=h0⋅Mkl+h1⋅Mkl−1+…+hl−1⋅Mk+hl=i=1∑lhi⋅Mkl−i

где hi=si−33, а Mk — некоторый коэффициентов с индексом k.

В рекурсивной форме: H(s0,…,sl)=H(s0,…sl−1)⋅Mk+hl

Также он решил дополнительно умножать значения хеш-функций на соответствующие�Mk (в качестве темы для размышления предлагается понять, зачем). Так он получил семейство хеш-функций:

hashk(s0,…,sl)=Mk⋅Hk(s0,…,sl)=Mk⋅i=1∑lhi⋅Mkl−i

В качестве коэффициентов он выбрал первые 51 простые числа [Мерсена](https://ru.wikipedia.org/wiki/Число_Мерсенна#Поиск_простых_чисел_Мерсенна).

Хеш-функция вычисляется как 32-битное знаковое число.

На этапе <<индексации>> алгоритм получает n множеств Bi,i=1..n, для каждого из которых вычисляется и запоминается только его сигнатура (массив из 51 min-hash по hashk). Сами множества запоминать не требуется.

k-ый элемент сигнатуры множества A={a1,…,at}:

signk(A)=mini=1..t(hashk(ai))

Далее алгоритм получает m множеств Aj,j=1..m, для каждого из которых вычисляется сигнатуры и методом MinHash вычисляется мера схожести со всеми множествами Bi,i=1..n по их сигнатурам.

Реализуй для Саши алгоритм MinHash, чтобы он мог продолжить с ним эксперименты в поисковом движке.

Первые 51 простых чисел Мерсена: 2, 3, 5, 7, 13, 17, 19, 31, 61, 89, 107, 127, 521, 607, 1279, 2203, 2281, 3217, 4253, 4423, 9689, 9941, 11213, 19937, 21701, 23209, 44497, 86243, 110503, 132049, 216091, 756839, 859433, 1257787, 1398269, 2976221, 3021377, 6972593, 13466917, 20996011, 24036583, 25964951, 30402457, 32582657, 37156667, 42643801, 43112609, 57885161, 74207281, 77232917, 82589933.

Для самопроверки: значения хеш-функция для строки Hello!: 6784, 53757, 880075, 5940809, 215813507, 1044570559, 2013480749, -2023706479, 1903631059, 1306052407, -1744343883, -678182479, 707822855, 850958161, 1666027313, -954647483, -1642547929, -1552791233, 1194154355, 634604041, -1774973513, -944905349, 776239043, -1567568273, 1337892619, -1070145177, 1884682751, 463618717, 1996901673, 2093487103, 953269957, 301233001, -97512729, 1761447973, 1754979091, -1210752461, -821112561, 56983071, 974041515, 1107238517, 670399721, 2128998137, 2005260791, 309245263, 535642661, -1734074825, 1179435439, 789840935, 1739628191, -800669381, 1335680931/

Также стоит отметить, что это далеко не лучшая хеш-функция для данной задачи, но зато достаточно простая для понимания и отладки.

## Входные данные

В первой строке вводится натуральное число n — количество множеств Bi. Значение n не превышает 2^31.

Каждая из последующих n строк содержит множество Bi,i=1..n, состоящее из элементов, разделённых пробелом.

Далее следует строка с числом m — количеством множеств Aj,j=1..m. Значение m не превышает 2^31.

Каждая из последующих m строк содержит множество Aj,j=1..m, состоящее из элементов, разделённых пробелом.

## Выходные данные

Требуется вывести m строк, содержащих сравнения соответствующего множества Aj,j=1..m с множествами Bi,i=1..m.

Каждая jя строчка-сравнение содержит меры схожести каждой из пар (Aj,B1),(Aj,B2),…,(Aj,Bn) разделённые пробелами.

Мерой схожести выступает доля совпавших элементов сигнатуры.

Мера схожести записывается как десятичное число с тремя знаками после точки. Ноль перед точкой всегда пишется: например 00.123, а не .123. Незначащие нули всегда пишутся: например, 0.100, а не 0.1.

## Пример теста 1

### Входные данные

```
10
10 20 30
10 20 40
10 20 50
30 40 50
20 40 50 60 70 80 90
80 80 80 80 80 80 80
90
190
120 4143 134
1 2 1000
5
1 2 3
10 20 30
20 40 50
90
80 90

```

### Выходные данные

```
0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.000 0.471
1.000 0.647 0.725 0.098 0.039 0.000 0.000 0.000 0.000 0.000
0.059 0.294 0.216 0.314 0.647 0.000 0.000 0.000 0.000 0.000
0.000 0.000 0.000 0.000 0.059 0.000 1.000 0.000 0.000 0.000
0.000 0.000 0.000 0.000 0.176 0.765 0.235 0.000 0.000 0.000

```

## Пример теста 2

### Входные данные

```
3
abcdefg hello world
alpha beta gamma delta omega
me and you
5
hello world
omega
alpha delta
abcdefgh
hi there hello it's me I'm the Adstronaut!

```

### Выходные данные

```
0.706 0.000 0.000
0.000 0.255 0.000
0.000 0.314 0.000
0.000 0.000 0.000
0.059 0.000 0.039

```