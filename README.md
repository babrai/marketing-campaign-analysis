# 📂 marketing-campaign-analysis

Анализ эффективности рекламных кампаний и проверка корректности атрибуции пользователей.  
Проект включает работу с маркетинговыми данными: установки пользователей, рекламные расходы, доходы и каналы привлечения.

---

## 📁 Структура проекта

```plaintext
marketing-campaign-analysis/
│
├── data/                      # исходные данные
│   ├── users.csv
│   ├── attribution.csv
│   ├── payments.csv
│   ├── ad_data.csv
│   ├── marketing_summary_by_date_channel_campaign.csv
│
├── notebooks/                 # анализ данных
│   ├── Задача 1.ipynb
│   ├── Задача 2.ipynb
│   └── Задача 3.ipynb
│
├── results/                   # сохранённые сводные таблицы
│   └── tiktok campaign eval.csv
│
├── .gitignore
└── README.md

---

## ⚡ Задача 1 — Подготовка данных

**Цель:** создать сводную таблицу для оценки рекламных кампаний.

**Шаги:**
- Загрузила исходные таблицы в `sqlite3` и `pandas`
- SQL-запросом объединила `users`, `attribution`, `payments`, `ad_data`
- Сгруппировала данные по `date`, `media_source`, `campaign`
- Сохранила сводную таблицу в `marketing_summary_by_date_channel_campaign.csv`

📁 _Результат_: `data/marketing_summary_by_date_channel_campaign.csv`

---

## ⚡ Задача 2 — Анализ кампаний TikTok

**Цель:** определить, какие кампании на канале `tiktokglobal_int` эффективны по критерию ROAS_7 > 0.18.

**Шаги:**
- Загрузила `marketing_summary_by_date_channel_campaign.csv`
- Отфильтровала `media_source == "tiktokglobal_int"`
- Сгруппировала по `campaign` → `sum(costs)`, `sum(revenue)`
- Посчитала `ROAS_7 = total_revenue_7 / costs`
- Добавила статус:
  - `эффективная` — если `ROAS_7 > 0.18`
  - `неэффективная` — иначе
- Сохранила результат в `tiktok campaign eval.csv`

**Выводы:**
- Всего кампаний: 4
- Эффективные (`ROAS_7 > 0.18`): 3  
- Неэффективные: 1  
- Наиболее успешные: `tt_campaign_4`, `tt_campaign_3`, `tt_campaign_1`

📁 _Результат_: `results/tiktok campaign eval.csv`

---

## ⚡ Задача 3 — Проверка корректности атрибуции

**Цель:** проверить корректность атрибуции пользователей канала `googleadwords_int`.

**Шаги:**
- Загрузила `users.csv` и `attribution.csv`
- Посчитала:
  - пользователей всего
  - пользователей с атрибуцией
  - пользователей без атрибуции
  - пользователей с `googleadwords_int` и их долю среди всех с атрибуцией
- Собрала таблицу `user_id | есть_в_users | есть_в_attribution | media_source`
- По ней оценила корректность атрибуции

**Результаты:**
- Всего пользователей: 29 767
- С атрибуцией: 20 711
- Без атрибуции: 9 056 (30.42 %)
- С `googleadwords_int`: 1 457 (7.03 % от всех с атрибуцией)

**Выводы:**
- Доля пользователей без атрибуции — 30 %, что может указывать на проблему с обработкой установок
- Доля `googleadwords_int` — 7 %, что выглядит низкой
- Возможна потеря части пользователей канала `googleadwords_int` — требует дополнительной проверки

---

## 🛠 Стек
- Python, pandas
- SQLite (через `sqlite3`)
- Jupyter Notebook

---
