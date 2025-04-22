
## 9. `SELECT TOP`

**Açıklama:**  
`SELECT TOP` ifadesi, döndürülecek kayıt sayısını sınırlar. Genellikle sıralama (`ORDER BY`) ile birlikte kullanılır.

**Söz Dizimi:**
```sql
SELECT TOP n * FROM tablo_adı ORDER BY sütun;
```

**Örnek:**
```sql
SELECT TOP 3 * FROM Ogrenciler ORDER BY Yas DESC;
```

---

## 10. `WITH` & CTE (Common Table Expression)

**Açıklama:**  
`WITH` ifadesi, geçici adlandırılmış sonuç kümeleri oluşturmak için kullanılır. Karmaşık sorguları daha okunabilir hale getirir.

**Söz Dizimi:**
```sql
WITH cte_adı AS (
  SELECT ...
)
SELECT * FROM cte_adı;
```

**Örnek:**
```sql
WITH Yaslar AS (
  SELECT Ad, Yas FROM Ogrenciler WHERE Yas > 20
)
SELECT * FROM Yaslar;
```

---

## 11. `SELECT TOP 1 WITH TIES`

**Açıklama:**  
`TOP 1 WITH TIES`, ilk satırla aynı değeri taşıyan diğer satırları da getirir.

**Örnek:**
```sql
SELECT TOP 1 WITH TIES * FROM Ogrenciler
ORDER BY Puan DESC;
```

---

## 12. `GROUP BY`

**Açıklama:**  
Gruplama yapmak için kullanılır. Genellikle `COUNT`, `SUM`, `AVG` gibi toplu fonksiyonlarla birlikte kullanılır.

**Örnek:**
```sql
SELECT Sehir, COUNT(*) AS KisiSayisi
FROM Ogrenciler
GROUP BY Sehir;
```

---

## 13. `JOIN` (INNER JOIN)

**Açıklama:**  
İki tabloyu ortak sütunlar üzerinden birleştirir. Sadece eşleşen kayıtlar döner.

**Örnek:**
```sql
SELECT O.Ad, S.DersAdi
FROM Ogrenciler O
INNER JOIN Siniflar S ON O.SinifID = S.SinifID;
```

---

## 14. `LEFT JOIN`

**Açıklama:**  
Sol tablodaki tüm kayıtları ve sağ tablodaki eşleşen kayıtları döner. Eşleşmeyen sağ taraf NULL olur.

**Örnek:**
```sql
SELECT O.Ad, S.DersAdi
FROM Ogrenciler O
LEFT JOIN Siniflar S ON O.SinifID = S.SinifID;
```

---

## 15. `RIGHT JOIN`

**Açıklama:**  
Sağ tablodaki tüm kayıtları ve sol tablodaki eşleşenleri getirir.

**Örnek:**
```sql
SELECT O.Ad, S.DersAdi
FROM Ogrenciler O
RIGHT JOIN Siniflar S ON O.SinifID = S.SinifID;
```

---

## 16. `FULL JOIN`

**Açıklama:**  
Her iki tablodan da tüm kayıtları döndürür. Eşleşmeyen alanlar için `NULL` değer gösterilir.

**Örnek:**
```sql
SELECT O.Ad, S.DersAdi
FROM Ogrenciler O
FULL JOIN Siniflar S ON O.SinifID = S.SinifID;
```

---

## 17. `CROSS APPLY`

**Açıklama:**  
Bir tablo ile fonksiyon veya alt sorguyu birleştirir. Fonksiyon veya alt sorgu dış tabloya bağımlı şekilde çalışır.

**Örnek:**
```sql
SELECT O.Ad, D.DersAdi
FROM Ogrenciler O
CROSS APPLY (
  SELECT TOP 1 DersAdi FROM Siniflar WHERE SinifID = O.SinifID
) D;
```
