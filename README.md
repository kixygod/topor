# Резюме по материалам

## 1. Основы линейного программирования

### Математическая постановка задачи

Задача линейного программирования (ЛП) включает оптимизацию целевой функции при наличии ограничений на ресурсы. Например, фабрика, производящая столы и шкафы, может стремиться максимизировать прибыль с учетом ограничений по наличию материалов.

#### Пример 1: Планирование производства

Допустим, мебельная фабрика производит два типа продукции — столы и шкафы. Для их производства используются три вида ресурсов: пиломатериалы, шурупы и краска. У фабрики есть определенные месячные запасы этих ресурсов. Требуется определить, сколько столов и шкафов нужно произвести, чтобы максимизировать прибыль.

- **Дано**:
  - $b_1, b_2, b_3$ — запасы пиломатериалов, шурупов и краски.
  - $c_1, c_2$ — цены продажи стола и шкафа.
  - $a_{ij}$ — норма расхода i-го ресурса на единицу продукции j.
  
- **Целевая функция**: максимизация прибыли от продаж:
  $$ Z(X) = c_1 x_1 + c_2 x_2 \to \max $$
  
- **Ограничения**: расходы на ресурсы не должны превышать запасы:
  $$ \sum_{j=1}^{n} a_{ij} x_j \leq b_i, \quad i = 1, 2, 3 $$

- **Условия**:
  - $x_1 \geq 0$ — количество столов не может быть отрицательным.
  - $x_2 \geq 0$ — количество шкафов не может быть отрицательным.
  
#### Пример 2: Рацион питания

Задача по составлению рациона питания для животных. Нужно минимизировать затраты на корм, при этом каждый корм должен удовлетворять потребностям в питательных веществах (витаминах).

- **Дано**:
  - $a_{ij}$ — количество единиц питательных веществ в 1 кг i-го типа корма.
  - $c_i$ — стоимость 1 кг i-го типа корма.
  - $b_j$ — потребности в витаминах (ежедневное требование).
  
- **Целевая функция**: минимизация затрат на корм:
  $$ Z(X) = \sum_{i=1}^{m} c_i x_i \to \min $$

- **Ограничения**: каждый корм должен удовлетворять минимальному требованию по витаминам:
  $$ \sum_{i=1}^{m} a_{ij} x_i \geq b_j, \quad j = 1, 2, 3 $$

---

## 2. Симплекс-метод

### Основная теорема линейного программирования

Согласно основной теореме ЛП, если задача имеет оптимальное решение, то оно будет достигнуто в одной из угловых точек области допустимых решений. В случае нескольких угловых точек экстремум можно достичь в их линейной комбинации.

### Идея решения задачи

Суть симплекс-метода заключается в последовательном переходе от одной угловой точки к другой, пока не будет найдено оптимальное решение.

### Прямой алгоритм симплекс-метода

1. **Приведение задачи к каноническому виду**:
   - Все ограничения преобразуются в уравнения с помощью дополнительных переменных (например, $x_3$, $x_4$).
   - Целевая функция записывается в виде: 
     $$ F = -a_1 x_1 - a_2 x_2 \dots = 0 $$

2. **Заполнение симплекс-таблицы**:
   - Вносятся коэффициенты при переменных, результаты правых частей уравнений, и коэффициенты целевой функции.
   
3. **Пошаговая проверка оптимальности**:
   - Если в последней строке таблицы есть отрицательные элементы, план не оптимален.
   - Из всех отрицательных элементов выбирается наименьший, и это определяет разрешающий столбец.
   - Находится разрешающая строка, которая задает, какая переменная войдет в базис.

4. **Переход к новой угловой точке**:
   - Проводятся математические операции для обновления значений в таблице.
   - Повторяются итерации, пока не будет достигнут оптимальный план.

---

## 3. Графический метод решения ЛП

Графический метод подходит для задач с двумя переменными. Основная цель — построить область допустимых решений и найти точку, которая максимизирует или минимизирует целевую функцию.

### Этапы решения

1. **Построение области допустимых решений**:
   - Для каждого ограничения строится прямая на графике.
   - Определяется область, которая удовлетворяет всем ограничениям (пересечение полуплоскостей).

2. **Определение направления градиента**:
   - Вектор-градиент функции $Z(X) = 3x_1 + 3x_2$ указывает направление максимального увеличения функции.

3. **Поиск оптимальной точки**:
   - Определяется точка пересечения двух ограничений, которая является оптимальной.
   - Решение: $x_1 = 5, x_2 = 3$.
   - Максимальная прибыль: $Z = 3 \times 5 + 3 \times 3 = 24$.

---

## 4. Двойственность в ЛП

### Первая теорема двойственности

Если одна из пар задач (прямая или обратная) имеет оптимальное решение, то и другая задача также имеет оптимальное решение. Оптимальные значения целевых функций обеих задач будут равны.

### Вторая теорема двойственности

Для достижения оптимальности в паре задач необходимо выполнить следующее условие:
- Если все переменные в одной из задач равны нулю, то это соответствует определенной стоимости ресурсов в другой задаче.

---

## 5. Анализ ограничений в ЛП

### Анализ изменения запаса ресурсов

1. **Как изменение запаса влияет на решение**:
   - Если дефицитный ресурс увеличивается, это может изменить оптимальный план.
   - Если ресурс избыточен, его запас можно уменьшить, не нарушив оптимальности.

2. **Графический и табличный анализ**:
   - Для каждой переменной можно определить диапазон изменения её значения, чтобы не изменить статус решения (например, не стать избыточным или дефицитным).

---

## 6. Целочисленное программирование

### Особенности

Целочисленное программирование — это разновидность линейного программирования, где переменные должны быть целыми числами. Применяется в задачах, где решение должно быть выражено целыми числами (например, количество товаров, рабочих мест и т.д.).

#### Методы решения:
- Применяются такие методы, как ветви и границы, чтобы найти оптимальное целочисленное решение.

---

## 7. Транспортная задача

Транспортная задача — это задача оптимизации перевозок товаров от нескольких поставщиков к нескольким потребителям с минимальными затратами.

### Методы решения

1. **Метод минимального элемента**:
   - Определяется минимальная стоимость перевозки и распределяются поставки с учётом минимизации затрат.
   
2. **Метод потенциалов**:
   - Определяются потенциальные значения для поставщиков и потребителей, что позволяет оптимизировать транспортные расходы.

3. **Проверка оптимальности плана**:
   - После распределения товара проверяется, может ли быть улучшен план (меньшие расходы на транспортировку).

---

## 8. Метод ветвей и границ

Метод ветвей и границ применяется для задач, в которых необходимо выбрать лучший из множества возможных вариантов, например, в задачах о маршрутах или назначениях.

### Алгоритм

1. **Деление на подзадачи**:
   - Каждая подзадача представляет собой новый вариант решения.
   
2. **Оценка каждой подзадачи**:
   - Для каждой подзадачи вычисляется нижняя граница её стоимости (прибыль, затраты и т.д.).

3. **Выбор ветки с минимальной границей**:
   - Если ветка имеет лучшую оценку, она продолжает развиваться.

---

## 9. Динамическое программирование

### Уравнение Беллмана

Динамическое программирование используется для задач, которые можно разбить на более мелкие задачи. Каждая задача решается на основе решения предыдущих.

#### Пример:
- **Задача распределения ресурсов между предприятиями**:
  - Распределяется ограниченный ресурс с максимизацией общей эффективности всех предприятий.

