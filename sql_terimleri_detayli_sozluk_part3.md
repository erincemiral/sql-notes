#  SQL Terimleri Sözlüğü - Bölüm 3: WHERE ve Operatörler

##  WHERE
Belirli bir koşula uyan satırları filtrelemek için kullanılır.  
```sql
SELECT * FROM Calisanlar WHERE Maas > 5000;
```

---

##  AND, OR, NOT
Koşulları birleştirir veya tersine çevirir:  
```sql
SELECT * FROM Calisanlar WHERE Maas > 5000 AND Departman = 'IT';
SELECT * FROM Calisanlar WHERE Maas < 3000 OR Departman = 'Muhasebe';
SELECT * FROM Calisanlar WHERE NOT Departman = 'Pazarlama';
```

---

##  IN, NOT IN
Belirli bir grup değerden biri mi kontrol eder:  
```sql
SELECT * FROM Calisanlar WHERE Departman IN ('IT', 'Muhasebe');
SELECT * FROM Calisanlar WHERE Departman NOT IN ('Yönetim', 'Pazarlama');
```

---

##  BETWEEN
İki değer arasında olup olmadığını kontrol eder (dahil):  
```sql
SELECT * FROM Calisanlar WHERE Maas BETWEEN 4000 AND 6000;
```

---

##  LIKE
Desene göre eşleşme arar:  
```sql
SELECT * FROM Calisanlar WHERE Adi LIKE 'A%';   -- A ile başlayanlar
SELECT * FROM Calisanlar WHERE Adi LIKE '%e';   -- e ile bitenler
SELECT * FROM Calisanlar WHERE Adi LIKE '%e%';  -- İçerisinde 'e' harfi bulunanlar (Örnek: Ahmet)
```

---

##  IS NULL, IS NOT NULL
Değerin boş olup olmadığını kontrol eder:  
```sql
SELECT * FROM Calisanlar WHERE IkinciAdi IS NULL;
SELECT * FROM Calisanlar WHERE Telefon IS NOT NULL;
```

---

## Örnek Tablo: Calisanlar

| CalisanID | Adi   | Departman  | Maas  | IkinciAdi | Telefon   |
|-----------|-------|------------|-------|-----------|-----------|
| 1         | Ali   | IT         | 6000  | NULL      | 555-1234  |
| 2         | Ayşe  | Muhasebe   | 4500  | Banu      | 555-5678  |
| 3         | Ahmet | Pazarlama  | 3000  | NULL      | NULL      |
| 4         | Can   | IT         | 7000  | Emre      | 555-0000  |
