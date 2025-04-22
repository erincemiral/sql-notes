# SQL Terimleri Sözlüğü

Bu belge, SQL öğrenme sürecinizde başvurabileceğiniz temel komutların açıklamaları ve örnekleriyle birlikte hazırlanmıştır.

## 🧪 Örnek Tablo: Employees

| employee_id | first_name | last_name | department | salary |
|-------------|------------|-----------|------------|--------|
| 1           | John       | Doe       | IT         | 5000   |
| 2           | Jane       | Smith     | HR         | 4500   |
| 3           | Alice      | Brown     | IT         | 5200   |
| 4           | Bob        | Davis     | Sales      | 4800   |
| 5           | Charlie    | Wilson    | HR         | 4700   |

---

# CREATE DATABASE

### 📌 Açıklama:
Yeni bir veritabanı oluşturmak için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
CREATE DATABASE MyDatabase;
```

### 🎯 Uygulama:
```sql
-- Veritabanı oluşturma
CREATE DATABASE CompanyDB;
```

---

# CREATE TABLE

### 📌 Açıklama:
Yeni bir tablo oluşturmak için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
CREATE TABLE table_name (column1 datatype, column2 datatype, ...);
```

### 🎯 Uygulama:
```sql
-- Employees tablosunu oluşturma
CREATE TABLE Employees (
    employee_id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    department VARCHAR(50),
    salary INT
);
```

---

# ALTER TABLE

### 📌 Açıklama:
Var olan bir tabloyu değiştirmek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
ALTER TABLE table_name ADD column_name datatype;
```

### 🎯 Uygulama:
```sql
-- Employees tablosuna email sütunu ekleme
ALTER TABLE Employees ADD email VARCHAR(100);
```

---

# INSERT INTO

### 📌 Açıklama:
Bir tabloya yeni veri eklemek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);
```

### 🎯 Uygulama:
```sql
-- Yeni bir çalışan ekleme
INSERT INTO Employees (employee_id, first_name, last_name, department, salary)
VALUES (6, 'Emily', 'Clark', 'Finance', 5100);
```

---

# UPDATE

### 📌 Açıklama:
Var olan bir veriyi güncellemek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
UPDATE table_name SET column1 = value1 WHERE condition;
```

### 🎯 Uygulama:
```sql
-- Maaşı güncelleme
UPDATE Employees SET salary = 5500 WHERE employee_id = 1;
```

---

# DELETE

### 📌 Açıklama:
Veri silmek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
DELETE FROM table_name WHERE condition;
```

### 🎯 Uygulama:
```sql
-- IT departmanındaki çalışanları silme
DELETE FROM Employees WHERE department = 'IT';
```

---

# DROP TABLE

### 📌 Açıklama:
Bir tabloyu tamamen silmek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
DROP TABLE table_name;
```

### 🎯 Uygulama:
```sql
-- Employees tablosunu silme
DROP TABLE Employees;
```

---

# SELECT

### 📌 Açıklama:
Veritabanından veri çekmek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
SELECT column1, column2 FROM table_name;
```

### 🎯 Uygulama:
```sql
-- Tüm çalışanların adlarını getirme
SELECT first_name, last_name FROM Employees;
```

---

# FROM

### 📌 Açıklama:
Verinin hangi tablodan geleceğini belirtmek için kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
SELECT * FROM table_name;
```

### 🎯 Uygulama:
```sql
-- Employees tablosundan tüm verileri çekme
SELECT * FROM Employees;
```

---

# WHERE

### 📌 Açıklama:
Şartlı sorgularda kullanılır.

### 🔧 Örnek Söz Dizimi:
```sql
SELECT * FROM table_name WHERE condition;
```

### 🎯 Uygulama:
```sql
-- IT departmanındaki çalışanları getirme
SELECT * FROM Employees WHERE department = 'IT';
```

