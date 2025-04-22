#  SQL Terimleri Sözlüğü - Bölüm 5: JOIN Türleri ve CROSS APPLY

##  INNER JOIN
İki tabloyu ortak bir sütun üzerinden eşleştirir, yalnızca eşleşen satırları getirir.
```sql
SELECT c.Adi, d.DepartmanAdi
FROM Calisanlar c
INNER JOIN Departmanlar d ON c.DepartmanID = d.DepartmanID;
```

---

##  LEFT JOIN
Sol tablodaki tüm kayıtları ve sağ tablodan eşleşenleri getirir. Sağda eşleşme yoksa NULL gelir.
```sql
SELECT c.Adi, d.DepartmanAdi
FROM Calisanlar c
LEFT JOIN Departmanlar d ON c.DepartmanID = d.DepartmanID;
```

---

##  RIGHT JOIN
Sağ tablodaki tüm kayıtları ve soldan eşleşenleri getirir. Solda eşleşme yoksa NULL gelir.
```sql
SELECT c.Adi, d.DepartmanAdi
FROM Calisanlar c
RIGHT JOIN Departmanlar d ON c.DepartmanID = d.DepartmanID;
```

---

##  FULL JOIN
Her iki tablodaki tüm kayıtları getirir. Eşleşme olmayan alanlar için NULL döner.
```sql
SELECT c.Adi, d.DepartmanAdi
FROM Calisanlar c
FULL JOIN Departmanlar d ON c.DepartmanID = d.DepartmanID;
```

---

##  CROSS JOIN
Tüm kayıtları çapraz birleştirir (karta çarpımı gibi). Her satır her satırla eşleşir.
```sql
SELECT c.Adi, d.DepartmanAdi
FROM Calisanlar c
CROSS JOIN Departmanlar d;
```

---

##  SELF JOIN
Bir tablonun kendisiyle eşleştirilmesidir.
```sql
SELECT A.Adi AS Calisan, B.Adi AS Yonetici
FROM Calisanlar A
INNER JOIN Calisanlar B ON A.YoneticiID = B.CalisanID;
```

---

##  CROSS APPLY
Satır bazlı alt sorgular veya fonksiyonlar ile çalışmak için kullanılır.  
Özellikle bir tablo-valued function (TVF) döndürüyorsa oldukça etkilidir.

```sql
SELECT c.Adi, Detay.MaasYuzdesi
FROM Calisanlar c
CROSS APPLY (
    SELECT c.Maas * 0.10 AS MaasYuzdesi
) AS Detay;
```

---

## Örnek Tablo: Calisanlar

| CalisanID | Adi   | DepartmanID | YoneticiID | Maas  |
|-----------|-------|-------------|------------|-------|
| 1         | Ali   | 1           | NULL       | 6000  |
| 2         | Ayşe  | 2           | 1          | 4500  |
| 3         | Ahmet | 3           | 1          | 3000  |
| 4         | Can   | 1           | 2          | 7000  |

## Örnek Tablo: Departmanlar

| DepartmanID | DepartmanAdi |
|-------------|--------------|
| 1           | IT           |
| 2           | Muhasebe     |
| 3           | Pazarlama    |

---

##  Açıklama
Bu bölümde öğrendikleriniz:

- Tablo birleştirme yöntemleri (`JOIN` türleri)
- Özellikle raporlama, veri çekme ve veritabanı ilişkilendirmelerinde kullanılan yapılar
- `CROSS APPLY` gibi gelişmiş kavramlarla satır bazlı işlemler

