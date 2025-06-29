### **Виды `JOIN` в SQL и их разница**

В `SQL` существует несколько типов `JOIN`, которые используются для объединения данных из двух таблиц.

---

### **📌 Таблица с основными видами `JOIN` и их разницей:**

|**Тип JOIN**|**Описание**|**Возвращает совпадения?**|**Возвращает НЕсовпадающие записи?**|
|---|---|---|---|
|**`INNER JOIN`**|Возвращает только те строки, где есть совпадение в обеих таблицах.|✅ Да|❌ Нет|
|**`LEFT JOIN` (или `LEFT OUTER JOIN`)**|Возвращает все строки из левой таблицы и **совпадения** из правой. Если нет совпадения, подставляет `NULL`.|✅ Да|✅ Левые (`NULL` из правой)|
|**`RIGHT JOIN` (или `RIGHT OUTER JOIN`)**|Возвращает все строки из правой таблицы и **совпадения** из левой. Если нет совпадения, подставляет `NULL`.|✅ Да|✅ Правые (`NULL` из левой)|
|**`FULL JOIN` (или `FULL OUTER JOIN`)**|Возвращает все строки из обеих таблиц. Где нет совпадения, подставляет `NULL`.|✅ Да|✅ И левые, и правые (`NULL` в недостающих местах)|
|**`CROSS JOIN`**|Создаёт **декартово произведение** (каждая строка левой таблицы умножается на каждую строку правой).|❌ Нет условий|❌ Нет|
|**`SELF JOIN`**|Это `JOIN` самой таблицы на себя (например, для поиска иерархий, связанных записей).|✅ Да|❌ Нет|
|**`NATURAL JOIN`**|Автоматически объединяет таблицы по столбцам с одинаковыми именами.|✅ Да|❌ Нет|

---

### **📌 Визуальные примеры разных `JOIN`**

#### **1️⃣ `INNER JOIN` (пересечение)**

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

✔ Вернёт **только совпадающие** записи по `department_id`.

#### **2️⃣ `LEFT JOIN` (все из `employees`, совпадения из `departments`)**

```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.id;
```

✔ Если у сотрудника нет отдела, будет `NULL`.

#### **3️⃣ `RIGHT JOIN` (все из `departments`, совпадения из `employees`)**

```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.id;
```

✔ Если в `departments` есть отдел без сотрудников, будет `NULL`.

#### **4️⃣ `FULL JOIN` (всё из обеих таблиц)**

```sql
SELECT employees.name, departments.department_name
FROM employees
FULL JOIN departments ON employees.department_id = departments.id;
```

✔ **Выведет всех сотрудников и все отделы**, даже если нет совпадений.

#### **5️⃣ `CROSS JOIN` (декартово произведение)**

```sql
SELECT employees.name, departments.department_name
FROM employees
CROSS JOIN departments;
```

✔ Каждая строка `employees` **перемножится** на каждую строку `departments`.

---

### **📌 Когда использовать `JOIN`?**

|**Ситуация**|**Какой `JOIN` использовать?**|
|---|---|
|Нужно **только совпадения**|`INNER JOIN`|
|Нужно **всё из одной таблицы + совпадения**|`LEFT JOIN` / `RIGHT JOIN`|
|Нужно **всё из обеих таблиц**|`FULL JOIN`|
|Нужно **умножить таблицы (каждую на каждую)**|`CROSS JOIN`|
|Таблица ссылается сама на себя (например, сотрудники и их начальники)|`SELF JOIN`|

---

🚀 **ИТОГ:**

- `INNER JOIN` → только совпадения.
- `LEFT JOIN` → **всё из левой**, совпадения из правой.
- `RIGHT JOIN` → **всё из правой**, совпадения из левой.
- `FULL JOIN` → **всё из обеих** таблиц.
- `CROSS JOIN` → декартово произведение.

🔥 **Теперь ты знаешь все `JOIN` и их различия!** 💡