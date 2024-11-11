## Отчет по лабораторной работе №2

#### № группы: `ПМ-2401`

#### Выполнил: `Овчинникова Анастасия Дмитриевна`

#### Вариант: `19`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

  ### 1. Постановка задачи
  
> 1) Программа получает на вход N+1 натуральных чисел. Необходимо сформировать массив из N элементов. Перовое число - количество элементов массива, остальные заполняют массив.
> 2) Необходимо переставить эелементы массива таким образом, чтобы вначале располагались избыточные числа в порядке возрастания, а остальные в порядке убывания.
> 3) Найти избыточные числа, вывести их количество.
> 4) Создать строчный массив, заполнить в соотвествии с массивом из пункта 1, где избыточные числа соответсвуют строке "Избыточное", а другие числа "nananan"
> 5) Заменить в массиве их пункта 1 числа, на количество его делителей, вкулючая его само.
>
> Избыточное число - целое число, сумма целых делителей которого (отлинчых от него самого) превышает само число.
> Делитель - целое число, на которое делится данное число без остатка.

### 2. Входные и выходные данные
#### Данные на вход
Программа получает на вход N+1 чисел. Первое число N - количество элементов массива. Остальные N чисел для зполнения массива. Числа являются натуральными (целые положительные) по условию.
#### Данные на выход
Для задачи 2 необходимо вывести тот же массив, но с перестановками. Следовательно, на выходе будет N натуральных чисел.
Для задачи 3 необходимо вывести избыточные числа и их количество. Значит на выходе будут натуральные числа.
Для задачи 4 необходимо вывести строчный массив. Значит на выходе будет N строк.
Для задачи 5 необходимо вывести тот же массив, что и во второй задаче, но где числа заменены на количество их делителей. Количество - натуральное число (min 2: 1, само число). 
Следовательно, на выходе будет ряд натуральных чисел.
### 3. Выбор структуры данных

Программа получает N+1 целых чисел. Где первое число - количество элементов в массиве. Предельные значения не указаны, можем взять число 0<n<200000, не нарушая целостности задачи, поэтому для хранения возьмем тип данных int. Необходим массив, в котором будут храниться числа, введенные с клавиатуры. Необходим второй массив, для строчного типа данных. Вводится переменная c, для подсчета избыточных чисел, оно положительное, типа int хвататет для его хранения. Также вводятся врменные переменные b и k для перестановок, т.к. они используются для обработки массива типа int, для них используется тот же тип данных.
В массив a вводятся натуральные числа, будем считать, что они не превышают 200000, используем тип данных int. Массив g строчный, в него будут вводится данные типа String.

|             | название переменной | Тип (в Java) | 
|-------------|---------------------|--------------|
| N (Число 1) | `n`                 | `int`        |
| массив 1    | `a`                 | `int`        |
| массив 2    | `g`                 | `String`     | (класс)
| C (Число 2) | `c`                 | `int`        |
| k (Число 3) | `k`                 | `int`        |
| b (Число 4) | `b`                 | `int`        |

Для вывода результата необязательно его хранить в отдельной переменной.


### 4. Алгоритм

#### Алгоритм выполнения программы, выводить результат будем после выполнения каждой задачи:

1. **Первая задача, ввод данных:**
   Программа получает на вход число N. И еще N натуральных чисел, которые заполняют массив a, при помощи цикла for.
2. **Вторая задача**
   Заводим переменную c для подсчета избыточных чисел. При помощи вложенного цикла for определим какие числа избыточные.
   1) Берется элемент a[i], для него проверяются числа от 1<j<a[i], т.е. все возможные делители.
   2) Если число a[i] делится без остатка на j, то j прибавялется к sumdel (сумма делителей).
   3) Если итоговая сумма делителей a[i] превышает само число, то переставляем a[i] на a[c]. Таким образом, мы добьемся того, что все избыточные чисила будут стоять в начале массива. После чего прибавялем к с единиицу. После проверки каждого a[i] сумму делителей необходимо обнулить.
      В итоге получаем массив, где в начале c избыточных чисел, а далее стоят остальные.
   4) При помощи вложенного цикла сравниваем между собой первые c элементов, т.е. избыточные числа. И расставляем их в порядке возрастания. Во втором цикле за j возьмем i+1. Т.е. элемент a[i] сравнивается с элементом a[i+1], если a[i]>a[j], то элементы меняем местами при помощи перемнной b.
      Расставили первые с чисел в порядке взрастания.
   5) Таким же образом переставляем остальные числа, только в порядке убывания. Но небходимо поменять знак в условии сравнения. Теперь меняем элементы местами, если a[i]<a[i+1].
  Получили массив, где первые с чисел - избыточные, стоят в порядке возрастания, а остальные стоят далее в порядке убывания.
   6) Выводим этот массив при помощи цикла for.
3. **Третья задача**
   Все действия будем производить с массивом, который был получен во второй задаче.
   1) Необходимо найти избыточные числа и вывести их количесвто. Эти подзадачи были выполнены в предыдщуем пункте, поэтому воспользуемся данными оттуда. Нет смысла прокуричвать те же циклы второй раз.
   2) Для того, чтобы вывести избыточные числа на экран. Выведем первые с чисел при помощи цикла for.
   3) За их количество отвечаем переменная с, поэтому выводим её следующим пунктом.
4. **Четвертая задача**
   1) В начале программы был создан массив g для хранения строчного типа данных, той же длины, что и массив a. Необходимо заполнить его таким образом, чтобы на месте избыточных чисел стояло слово "Избыточное", а на месте остальных "nananan".
Для этого первые с мест массива зполним строкой "Избыточное" при помощи цикла for. При помощи второго цикла for оставшиеся места заполним строкой "nananan".
Таким образом, мы получили массив, где избыточные числа из массива a соответсвуют строкам "Избыточное", а остальнные "nananan".
   3) Выведем полученный массив g при помощи цикла for.
5. **Пятая задача**
   Необходимо вывести количество делитилей каждого числа массива a.
   1) Создадим цикл for и вложенный в него for. Первый цикл берет элемент a[i], а вложенный в него проверяет являются ли числа от 1<j<=a[i] делителями, т.е. делится ли a[i] на j без остатка. Если да, то к врменной переменной b прибавляем единицу. По завершению вложенного цикла a[i] заменяется на b, а b обнуляется.
   2) При помощи цикла for выводим полученный массив, где каждое число заменено на количество его делителей.
      

