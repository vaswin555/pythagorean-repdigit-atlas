# pythagorean-repdigit-atlas

[![SQLite](https://img.shields.io/badge/SQLite-3-blue.svg)](https://www.sqlite.org/)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Language: EN/RU](https://img.shields.io/badge/Language-EN%20%7C%20RU-brightgreen.svg)]()

## 📖 Abstract / Краткое описание

This repository contains a comprehensive, indexed SQLite database of Pythagorean triples (\(a^2 + b^2 = c^2\)) where the fixed leg \(a\) is a repdigit (a number consisting of repeating identical digits) for digits from **1 to 9**, with lengths up to **29 digits**. The search for the second leg \(b\) is bounded within a computational window of \(b \le 10^{24}\).

Этот репозиторий содержит полную проиндексированную базу данных SQLite пифагоровых троек (\(a^2 + b^2 = c^2\)), где фиксированный катет \(a\) является репдигитом (числом из повторяющихся одинаковых цифр) для цифр от **1 до 9** с длиной до **29 знаков**. Поиск второго катета \(b\) ограничен вычислительным окном \(b \le 10^{24}\).

---

## 🎯 Motivation & Novelty / Мотивация и новизна

The project is designed as a ready-to-use reference archive, not as a computational tool. Researchers, students, or mathematicians can instantly access verified results for any cluster without writing code, configuring arbitrary-precision libraries, or running day-long computations. The database also captures extreme asymmetric triples (where \(c - b = 1\) or \(2\)) that extend far beyond the standard iteration window, reaching up to **46 digits** for the hypotenuse.

Проект создаётся как готовый справочный архив, а не вычислительный инструмент. Исследователи, студенты или математики могут мгновенно получить доступ к верифицированным результатам по любому кластеру, не написав ни строчки кода и не запуская суточные прогоны. База также фиксирует экстремальные асимметричные тройки (где \(c - b = 1\) или \(2\)), которые выходят далеко за пределы стандартного окна перебора, достигая **46 знаков** для гипотенузы.

---

## ✨ Key Features / Ключевые особенности

- **Huge Dataset:** Hundreds of thousands of triples, including massive numbers with 29+ digits.
- **Bilingual Views:** The database contains both English (`Group_6_Sixes`) and Russian (`Группа_6_Шестерки`) views for convenience.
- **Statistical Summaries:** Built-in views (`Summary_6_9_By_Lengths`) provide instant statistics on the number of triples found for each length and digit.
- **TEXT Storage:** Handles arbitrarily large numbers without integer overflow.
- **Extreme Asymmetry:** Includes analytically derived triples where \(c - b = 1\) or \(2\), extending to 46-digit hypotenuses.

- **Огромный набор данных:** Сотни тысяч троек, включая числа с 29+ знаками.
- **Двуязычные представления:** База содержит как английские (`Group_6_Sixes`), так и русские (`Группа_6_Шестерки`) представления для удобства.
- **Статистические сводки:** Встроенные представления (`Summary_6_9_By_Lengths`) мгновенно показывают количество найденных троек для каждой длины и цифры.
- **Хранение в TEXT:** Обрабатывает сколь угодно большие числа без переполнения целочисленного типа.
- **Экстремальная асимметрия:** Включает аналитически выведенные тройки, где \(c - b = 1\) или \(2\), вплоть до 46-значных гипотенуз.

---

## 🗄️ Database Schema / Структура базы данных

The data is split into two files for performance reasons:
1. `pythagoras_r_1-5-EN-RU.db` (Digits 1, 2, 3, 4, 5)
2. `pythagoras_r_6-9-EN-RU.db` (Digits 6, 7, 8, 9)

### Tables / Таблицы:
- `main_structure`: Contains the "folders" (catalog digits and lengths). / Содержит «папки» (цифры каталога и длины).
- `triples_storage`: Contains the actual Pythagorean triples (`fixed_cat`, `second_cat`, `hypotenuse`). / Содержит сами пифагоровы тройки (`fixed_cat`, `second_cat`, `hypotenuse`).

### Views / Представления:
- `Group_X_...` / `Группа_X_...`: Shows all triples for a specific digit (X). / Показывает все тройки для конкретной цифры (X).
- `Summary_X_Y_By_Lengths` / `Сводка_X_Y_По_Длинам`: Aggregated pivot table showing the count of triples by length, including a `TOTAL` row. / Сводная таблица, показывающая количество троек по длинам, включая строку `TOTAL` / `ИТОГО`.

---

## 📊 Density Map / Карта плотности распределения

Below is the verified and preliminary summary of the total number of solutions recorded in the database by cluster.
Ниже представлены выверенные и предварительные итоги общего количества решений, зафиксированных в базе по кластерам.

| Cluster / Кластер | Base Digit / Базовая цифра | Total Triples / Всего троек |
| :--- | :--- | :--- |
| Cluster 1 | Единицы (1) | **44,041** (Minimum)|
| Cluster 2 | Двойки (2) | 44,050 |
| Cluster 3 | Тройки (3) | 79,964 |
| Cluster 4 | Четвёрки (4) | 132,260 |
| Cluster 5 | Пятёрки (5) | 132,260 |
| Cluster 6 | Шестёрки (6) | 80,054 |
| Cluster 7 | Семёрки (7) | 83,984 |
| Cluster 8 | Восьмёрки (8) | **220,443** (Peak) |
| Cluster 9 | Девятки (9) | 116,031 |

---

## 🚀 How to Use / Как использовать

1. Download the `.db` files from the `databases/` folder.
2. Install [DB Browser for SQLite](https://sqlitebrowser.org/).
3. Open the `.db` file.
4. Go to the **Browse Data** tab and select the desired view (e.g., `Group_6_Sixes` or `Summary_6_9_By_Lengths`).

1. Скачайте файлы `.db` из папки `databases/`.
2. Установите [DB Browser for SQLite](https://sqlitebrowser.org/).
3. Откройте файл `.db`.
4. Перейдите на вкладку **Browse Data** и выберите нужное представление (например, `Group_6_Sixes` или `Summary_6_9_By_Lengths`).

### Useful SQL Queries / Полезные SQL-запросы

**Find the smallest second leg for a specific fixed leg:**
```sql
SELECT * FROM Group_6_Sixes 
WHERE Fixed_Leg = '6666666666' 
ORDER BY LENGTH(Second_Leg) ASC, Second_Leg ASC 
LIMIT 1;

## 🔬 Methodology / Методология

The computational pipeline consists of several optimized stages:

1. **Computational Core (C++):** A search algorithm written in C++ using the **GMP (GNU Multiple Precision Arithmetic Library)** via the `mpz_class` class to process numbers exceeding 25 digits without precision loss.
2. **Algorithmic Filter:** Pre-filtering of residues by small primes (`SMALL_PRIMES_LIMIT = 100000`) to avoid costly square-root operations on unsuitable numbers.
3. **Data Pipeline (Python & SQLite):** Results from text logs are automatically parsed by a Python script and inserted into a relational SQLite database for subsequent indexing.

Вычислительный конвейер состоит из нескольких оптимизированных этапов:

1. **Вычислительное ядро (C++):** Поисковый алгоритм на C++ с использованием библиотеки длинной арифметики **GMP** через класс `mpz_class` для обработки чисел разрядностью выше 25 знаков без потери точности.
2. **Алгоритмический фильтр:** Предварительная фильтрация остатков по малым простым числам (`SMALL_PRIMES_LIMIT = 100000`) для исключения ресурсоёмких операций извлечения корней из заведомо неподходящих чисел.
3. **Конвейер данных (Python & SQLite):** Результаты расчётов из текстовых логов автоматически парсятся скриптом на Python и заносятся в реляционную базу данных SQLite для последующего индексирования.

---

## 🔍 Interesting Observations / Интересные наблюдения

### 1. Beautiful Digit Patterns / Красивые цифровые паттерны

During the generation, striking repeating patterns were discovered. For example, for the fixed leg `888888888888888` (fifteen 8s), the triples contain sequences like:
* `123456790123456790...`
* `987654320987654320...`

This highlights the deep cyclic nature of numbers when generating Pythagorean triples.

В ходе генерации были обнаружены удивительные повторяющиеся паттерны. Например, для катета `888888888888888` (пятнадцать восьмёрок) тройки содержат последовательности вида:
* `123456790123456790...`
* `987654320987654320...`

Это подчёркивает глубокую циклическую природу чисел при генерации пифагоровых троек.

### 2. Symmetry of Clusters 4 and 5 / Симметрия кластеров 4 и 5

Clusters 4 (Fours) and 5 (Fives) produced an absolutely identical number of triples (132,260 each). A hypothesis is that this is due to the influence of the squares of prime numbers $2^2$ and $5^2$ in the factorization structure.

Кластеры 4 (Четвёрки) и 5 (Пятёрки) выдали абсолютно идентичное число троек (по 132 260). Гипотеза: влияние квадратов простых чисел $2^2$ и $5^2$ в структуре разложения сомножителей.

### 3. Extreme Asymmetry ($c - b = 1$ and $c - b = 2$) / Экстремальная асимметрия

*   **Odd Asymmetry ($c - b = 1$):** Found in the Ones cluster. The Diophantine equation yields exact formulas: $b = \frac{a^2 - 1}{2}$, $c = \frac{a^2 + 1}{2}$. For $a$ consisting of 24 ones, $a^2$ reaches $\sim 10^{46}$, demonstrating the architecture's ability to capture analytical extremes far beyond the $10^{24}$ iteration window.
*   **Even Asymmetry ($c - b = 2$):** Observed in even clusters (e.g., Fours). Formulas: $b = \frac{a^2 - 4}{4}$, $c = \frac{a^2 + 4}{4}$.

*   **Нечётная асимметрия ($c - b = 1$):** Обнаружена в кластере Единиц. Диофантово уравнение даёт точные формулы: $b = \frac{a^2 - 1}{2}$, $c = \frac{a^2 + 1}{2}$. Для $a$ из 24 единиц $a^2$ достигает $\sim 10^{46}$, что доказывает способность архитектуры фиксировать аналитические экстремумы далеко за пределами окна перебора $10^{24}$.
*   **Чётная асимметрия ($c - b = 2$):** Наблюдается в чётных кластерах (например, Четвёрки). Формулы: $b = \frac{a^2 - 4}{4}$, $c = \frac{a^2 + 4}{4}$.

---

## 🚀 Roadmap / Планы по развитию

1. **Complete the 1–9 matrix:** Finalize the C++ computational runs for Clusters 8 (Eights) and 9 (Nines).
2. **Final verification:** Perform a validation pass across all 9 clusters to guarantee 100% accuracy of the reference dataset.
3. **Analytical expansion:** Integrate "Fast-Shortcut" triggers into the C++ core to automatically generate boundary triples for $c - b = 1$ and $c - b = 2$ without brute-force iteration, instantly extending the database to 50-digit numbers for extreme triangles.
4. **Public release:** Publish the repository as an open-source verified atlas for the global mathematical community.

1. **Полное закрытие матрицы (1–9):** Доведение вычислительных прогонов на C++ до логического финала.
2. **Финальная сверка данных:** Повторный валидационный проход по всем 9 кластерам для исключения случайных системных опечаток или пропусков, гарантирующий 100% точность справочника.
3. **Аналитическое расширение:** Интеграция в C++ ядро триггеров быстрого вычисления (Fast-Shortcut), которые при фиксации катета $a$ автоматически генерируют пограничные тройки для $c - b = 1$ и $c - b = 2$, минуя стадию циклического брутфорса. Это позволит мгновенно расширить рамки базы данных до 50-значных чисел для экстремальных треугольников.
4. **Публикация:** Перевод репозитория в публичный доступ для мирового математического сообщества как открытого верифицированного Open Source атласа.

---

## 📚 References / Bibliography

1.  **Muzaffar, H., & Zelator, K. (2009). "Pythagorean Triangles with Repeated Digits – Different Bases."** *arXiv:0908.3866 [math.GM]*.
    *   **Description:** This foundational paper investigates the existence and properties of Pythagorean triangles where the lengths of the legs or hypotenuse are repdigits (numbers consisting of repeating digits) in various number bases. It provides the direct theoretical context for studying triples with repeated-digit fixed legs.
    *   **Link:** [https://arxiv.org/abs/0908.3866](https://arxiv.org/abs/0908.3866)

2.  **Delph, A. (2025). "The Scaling-Palindrome Theorem for Multibase Pythagorean Triples."** *Zenodo*.
    *   **Description:** This work presents a theorem on digit-string symmetries that emerge when primitive Pythagorean triples are scaled by palindromic repdigit factors in an arbitrary base. It directly relates to the "beautiful" palindromic number patterns observed in the generated dataset (e.g., sequences like `123456790...`).
    *   **Link:** [https://zenodo.org/records/16593599](https://zenodo.org/records/16593599)

3.  **"The Pell Spine as an Optimal Rational Separator: Extremal Resolution and Smooth Transport in Primitive Pythagorean Triples." (2026).** *Zenodo*.
    *   **Description:** This paper studies extremal problems in primitive Pythagorean triples, specifically focusing on the normalized leg separation \(\Delta k = |b-a|/c\). It proves that record minima occur at near-isosceles triples forming a Pell-generated sequence, which resonates with the extreme asymmetric cases (\(c - b = 1\) or \(2\)) captured in this atlas. It also includes an exhaustive computational enumeration of 795,763 primitive triples for independent verification.
    *   **Link:** [https://zenodo.org/records/21510911](https://zenodo.org/records/21510911)

4.  **Cazorla García, P.-J. (2025). "On generalised Pythagorean triples over number fields."** *arXiv:2506.11636 [math.NT]*.
    *   **Description:** This paper provides a survey and extension of results on generalized Pythagorean triples (integer solutions to \(ax^2 + by^2 + cz^2 = 0\)) over number fields. It offers a broader theoretical perspective on Diophantine equations related to the Pythagorean theorem.
    *   **Link:** [https://arxiv.org/abs/2506.11636](https://arxiv.org/abs/2506.11636)

5.  **Okagbue, H. I., Adamu, M. O., Oguntunde, P. E., Opanuga, A. A., Owoloko, E. A., & Bishop, S. A. (2017). "Datasets on the statistical and algebraic properties of primitive Pythagorean triples."** *Data in Brief*, 14, 686-694.
    *   **Description:** This article describes a dataset derived from the statistical and algebraic analysis of the first 331 primitive Pythagorean triples. It serves as an excellent example of how mathematical datasets can be structured, analyzed, and published, providing a methodological reference for this project's data presentation.
    *   **DOI:** [https://doi.org/10.1016/j.dib.2017.08.021](https://doi.org/10.1016/j.dib.2017.08.021)

6.  **OEIS Foundation Inc. "Sequence A010785: Repdigit numbers."** *The On-Line Encyclopedia of Integer Sequences*.
    *   **Description:** The authoritative encyclopedia entry for the sequence of repdigit numbers (1, 2, ..., 9, 11, 22, 33, ...), which form the basis of the fixed legs in this atlas.
    *   **Link:** [https://oeis.org/A010785](https://oeis.org/A010785)

7.  **The GNU Multiple Precision Arithmetic Library (GMP).**
    *   **Description:** The official documentation for the arbitrary-precision arithmetic library used in the C++ computational core to handle numbers exceeding standard integer limits without precision loss.
    *   **Link:** [https://gmplib.org/](https://gmplib.org/)

---

## 📜 License / Лицензия

*(License file will be added soon / Файл лицензии будет добавлен в ближайшее время)*

*Planned License: Creative Commons Attribution 4.0 International (CC BY 4.0).*
*Планируемая лицензия: Creative Commons Attribution 4.0 International (CC BY 4.0).*

---

## 👤 Author / Автор

**vaswin555**
*Created as part of a deep mathematical research project.*
*Создано в рамках глубокого математического исследовательского проекта.*
