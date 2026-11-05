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
| Cluster 1 | Единицы (1) | 39,993 |
| Cluster 2 | Двойки (2) | 40,002 |
| Cluster 3 | Тройки (3) | 68,302 |
| Cluster 4 | Четвёрки (4) | **120,112** (Peak) |
| Cluster 5 | Пятёрки (5) | **120,112** (Symmetric Peak) |
| Cluster 6 | Шестёрки (6) | 69,190 |
| Cluster 7 | Семёрки (7) | 71,176 |
| Cluster 8 | Восьмёрки (8) | *In progress / В процессе* |
| Cluster 9 | Девятки (9) | *In progress / В процессе* |

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
