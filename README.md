# IDZ-4-ABC-
# ИДЗ №4. Татаров Константин Манолисович БПИ 228
**Варинат 4. Работа выполнена на 10 баллов.\
Условие задания:**\
Задача о Винни-Пухе и мстительных пчелах. Неправильные
пчелы, подсчитав в конце месяца убытки от наличия в лесу ВинниПуха, решили разыскать его и наказать в назидание всем другим
любителям сладкого. Для поисков медведя они поделили лес на
участки, каждый из которых прочесывает одна стая неправильных пчел. В случае нахождения медведя на своем участке стая проводит показательное наказание и возвращается в улей. Если участок
прочесан, а Винни-Пух на нем не обнаружен, стая также возвращается в улей. Там она получает информацию об еще неисследованных участках и снова улетает. Требуется создать многопоточное
приложение, моделирующее действия пчел. При решении использовать парадигму «портфель задач». Каждая стая пчел — отдельный
поток.

**Решение:**\
[Код на ассемблере с комментариями](https://github.com/kkkkkostya/IDZ-3-ABC-/tree/eba835c586b11ba92e165baa8bf7f3904998c4a5/Assembler%20code)\
[Тест собраны тут](https://github.com/kkkkkostya/IDZ-3-ABC-/tree/803b1e0f99b8944e29a407d5cd8f0dd2e581d6d4/tests)

**Отчет по критериям:**

4-5: 
* Сценарий: задача состоит из улья, в котором располагается некоторое количество отрядов пчел, каждый из которых прочесывает свой участок леса в надежде найти Винни-Пуха. Если отряд нашел медведя, то он его наказывает, сообщая о находке остальным отрядам, и возвращается в улей, после чего пчелы больше не вылетают из него. Если же Винни-Пух не найден, то отряд обозначает, что данный участок уже обследован и сюда идти уже не нужно, и затем возвращается в улей чтобы узнать, на какой следующий участок леса нужно выдвинуться. В случае, если все учатски уже прочесаны (или текущий свободный участок выходит за пределы допустимых участков), то отряд не должен никуда лететь, а просто ждать, пока другой отряд накажет медведя.
* Модель параллельных вычислений заключается в использовании нескольких потов, каждый из которых представляет отдельный отряд и параллельно прочесывает не посещенные участки. Разделяемой переменной в разработанной программе является переменная, которая указывает на поимку Винни-Пуха (true/false), которая блокируется мьютексом соответственно.
* Входными данными программы являются количество участков леса и количество отрядов пчел. Каждая переменная должна принадлежать промежутку [1; 1000]
* Реализовано консольное приложение, решающее поставленную задачу с использованием одного варианта изученных синхропримитивов.
* Ввод данных в приложение реализован с консоли во время выполнения программы (без использования аргументов командной строки).
* Для используемых генераторов случайных чисел описаны их диапазоны и то, как интерпретируются данные этих генераторов.
* Созданный информативный вывод, который позволяет понять, что в данный момент происходит в программе: какая стая и какой участок леса прочесывает, наказывает Винни-Пуха или он уже найден.
* В программе присутствуют комментарии, поясняющие выполняемые действия и описание используемых объектов и переменных
* Результаты тестирования:
\
![Результат выполнения программы:](https://github.com/kkkkkostya/IDZ-3-ABC-/blob/803b1e0f99b8944e29a407d5cd8f0dd2e581d6d4/tests/scrin_test1.png)

6-7: 
* Внутри функций используются регистровые или локальные (при нехватке) переменные.
* Для чтения текста из файла реализован буфер ограниченного размера, равного 512 байтам. При этом программа читает файлы размером до 10 килобайт.
* Реализован ввод исходных данных, их обработку, вывод результатов через соответствующие подпрограммы. Подпрограммы получают необходимые им данные через параметры в соответствии с принятым соглашением о передаче параметров.
* Возвращаемые из подпрограмм значения возвращаются через параметры в соответствии с общепринятыми соглашениями.
\
8: 
* Добавил в программу возможность дополнительного вывода результатов на консоль через запрос пользователя, который решаем выводить на консоль результат преобразования данных с файла или нет.
* Реализовал дополнительную тестовую программу с заготовленными тестами для проверки корректности работы программы.
\
![Результаты тестирования:](https://github.com/kkkkkostya/IDZ-3-ABC-/blob/803b1e0f99b8944e29a407d5cd8f0dd2e581d6d4/tests/auto_tests.png)

9: 
* Добавил отдельную [автономную библиотеку](https://github.com/kkkkkostya/IDZ-3-ABC-/blob/803b1e0f99b8944e29a407d5cd8f0dd2e581d6d4/Assembler%20code/macro-lib.asm) с макросами для реализации ввода, обработки и вывода данных.
* Также реализовал дополнительную тестовую программу, вызывающую выполняемые подпрограммы через макросы.

10: 
* Разбил программу на несколько единиц компиляции и создал унифицированные модули подпрограмм ввода и вывода. 
* Также выделил макросы в отдельную автономную библиотеку,которая подключается в главном файле
