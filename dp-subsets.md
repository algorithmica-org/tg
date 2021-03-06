
# Динамика по подмножествам

Иногда в качестве состояния динамики нужно брать множество. Это множество можно потом перебрать либо втупую, либо использовать в динамике.

Множество удобно представлять в виде *битовой маски*.

Перед тем, как разбирать конкретные задачи, несколько советов по поводу кодинга:

Числа хранятся в памяти компьютера просто как последовательность битов.


```
с = a & b; // побитовое И
c = a | b; // побитовое ИЛИ
c = a ^ b; // побитовое исключающее ИЛИ (XOR)
c = ~a;    // побитовое НЕ
```

Битовым операциям соответствуют операции над подмножествами: «И» соответствуют пересечение, «ИЛИ» соответствует объединение и так далее.

Также тут работуют такие операции, как двоичные сдвиги. По сути, `a<<l` означает домножить на $2^l$, а `a>>l` означает поделить на $2^l$ с остатком. Аккуратнее с переполнением!

Очень часто нужно проверять, входит ли какой-то элемент в множество. Аналогично, стоит ли единица на какой-то позиции в маске.


```

```

## Рюкзак по подмножествам

> Даны $n \leq 20$ слитков золота, каждый весом до $10^9$ кг. У вас есть рюкзак, вмещающий $W$ кг. Какой максимальный вес можно в нем унести за один раз?

Можно просто перебрать все множества и посмотреть, какого они суммарного веса.


```
int w[20] = { ... };

int ans = 0;

for (int mask = 0; mask < (1<<n); mask++) {
    int sum = 0;
    for (int i = 0; i < n; i++)
        for (mask>>i&1)
            sum += w[i];
    if (sum < w && sum > ans)
        ans = sum;
}
```

При итеративной реализации динамики нужно не забывать о том, что обработка состояний в должна осуществляться от простых случаев к сложным. Перебор всех масок по возрастанию это гарантирует — подумайте, почему.

## Турнир на выбывание

Тут нужно немножко подумать, как устроен теорвер.

На самом деле, это очень общая постановка задачи. Почти всегда состояние будет описываться каким-то очень большим количеством параметров и кодируются битовыми масками.
