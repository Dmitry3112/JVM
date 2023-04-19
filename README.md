Алгоритм работы JVM

Вызов методов создаёт отдельный для каждого метода фрейм в стеке:

void main(String[] args){...}
void printAll(Object o, int i, Integer ii){...}
println(o.toString() + i + ii)
println("finished")




В соответствующий фрейм (main()) в стеке помещается информация о примитиве i.

Загрузка класса Object;

Создание в куче объекта Object();

Создание переменной o в фрейме main() со ссылкой на созданный в куче объект Object().

Загрузка класса Integer;

Созание в куче объекта Integer();

Создание переменной ii с информацией о ней в фрейме main() и передача ей ссылки на созданный в куче объект Integer().

Создание в стеке фрейма для printAll();

Создание переменной o со ссылкой на созданный ранее в куче объект Object() в фрейме printAll();

В фрейм printAll() помещается информация о переменной i, которая содержит значение примитивного типа "int";

Создание переменной ii в фрейме printAll и передача ей ссылки на созданный ранее в куче объект Integer().

Создание нового объекта Integer() в куче для последующего использования;

Создание переменной uselessVar с информацией о ней в фрейме printAll и передача ей ссылки на созанный выше объект Integer() (этот объект впоследствии может быть удален при работе GC, т.к. при выполнении программы (метод main()) на него не остается ссылок).

Загрузка класса System со static-полем out (не будет затронут работой GC);

Создание в стеке фрейма для println(o.toString() + i + ii);

Передача в фрейм println(o.toString() + i + ii) переменных о, ii со ссылками на соответствующие объекты, созданные ранее. Значение переменной i передается в качестве аргумента, а не в виде ссылки, так как является примитивом.

Создание в стеке фрейма для println("finished").
