#  SQL Terimleri Sözlüğü - Bölüm 6: CTE, TOP, Sıralama ve Satır Numaralandırma

##  WITH (CTE - Common Table Expression)
Geçici bir sorgu sonucu üretip, sorgu içinde tekrar kullanmak için tanımlanır.
```sql
WITH ITCalisanlari AS (
    SELECT * FROM Calisanlar WHERE Departman = 'IT'
)
SELECT * FROM ITCalisanlari WHERE Maas > 5000;
```

---

##  SELECT TOP
İlk N kadar satırı getirir.
```sql
SELECT TOP 3 * FROM Calisanlar ORDER BY Maas DESC;
```

---

##  SELECT TOP 1 WITH TIES
İlk satırı ve onunla aynı değere sahip tüm diğer satırları getirir.
```sql
SELECT TOP 1 WITH TIES *
FROM Calisanlar
ORDER BY Maas DESC;
```
> Eğer en yüksek maaşlı birden fazla çalışan varsa, hepsi gelir.

---

##  ORDER BY
Sonuçları sıralamak için kullanılır.
```sql
SELECT * FROM Calisanlar ORDER BY Maas ASC;
SELECT * FROM Calisanlar ORDER BY Maas DESC, Adi ASC;
```

---

##  ROW_NUMBER()
Her satıra sıralı numara verir. Genellikle alt sorgularda veya CTE içinde kullanılır.
```sql
WITH SiraliMaaslar AS (
    SELECT Adi, Maas,
           ROW_NUMBER() OVER (ORDER BY Maas DESC) AS Sira
    FROM Calisanlar
)
SELECT * FROM SiraliMaaslar WHERE Sira = 1;
```
> En yüksek maaşlı çalışanı bulmak için kullanılabilir.

---

## Örnek Tablo: Calisanlar

| CalisanID | Adi   | Departman  | Maas  |
|-----------|-------|------------|-------|
| 1         | Ali   | IT         | 6000  |
| 2         | Ayşe  | Muhasebe   | 4500  |
| 3         | Ahmet | Pazarlama  | 6000  |
| 4         | Can   | IT         | 7000  |
| 5         | Ece   | Muhasebe   | 5000  |

---

##  Açıklama
Bu bölümde öğrendikleriniz:

- Sorgulara esneklik ve tekrar kullanabilirlik sağlayan yapılar (`WITH CTE`)
- En çok kazanan çalışan gibi sıralı sorgular için `ROW_NUMBER()` kullanımı
- Belirli sayıda satırla çalışmak (`TOP`, `TOP 1 WITH TIES`)
- Sonuç sıralamaları (`ORDER BY`)

