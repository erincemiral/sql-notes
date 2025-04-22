#  SQL Terimleri Sözlüğü - Bölüm 4: Fonksiyonlar ve Gruplama

##  COUNT()
Belirli bir koşula uyan satır sayısını verir.
```sql
SELECT COUNT(*) FROM Calisanlar;
SELECT COUNT(Telefon) FROM Calisanlar WHERE Departman = 'IT';
```

---

##  SUM()
Sayısal sütunların toplamını verir.
```sql
SELECT SUM(Maas) AS ToplamMaas FROM Calisanlar;
```

---

##  AVG()
Sayısal bir sütunun ortalamasını hesaplar.
```sql
SELECT AVG(Maas) AS OrtalamaMaas FROM Calisanlar;
```

---

##  MIN() ve MAX()
Minimum ve maksimum değerleri döndürür.
```sql
SELECT MIN(Maas) AS EnDusukMaas, MAX(Maas) AS EnYuksekMaas FROM Calisanlar;
```

---

##  LEN()
Bir metin alanındaki karakter sayısını döndürür.
```sql
SELECT Adi, LEN(Adi) AS KarakterSayisi FROM Calisanlar;
```

---

##  GETDATE()
Mevcut sistem tarihini ve saatini getirir.
```sql
SELECT GETDATE() AS BugunTarih;
```

---

##  GROUP BY
Verileri belirli bir sütuna göre gruplamak için kullanılır.
```sql
SELECT Departman, COUNT(*) AS CalisanSayisi
FROM Calisanlar
GROUP BY Departman;
```

---

##  HAVING
Gruplandırılmış veriler üzerinde koşul belirlemek için kullanılır (WHERE gibi ama GROUP BY sonrasında gelir).
```sql
SELECT Departman, AVG(Maas) AS OrtalamaMaas
FROM Calisanlar
GROUP BY Departman
HAVING AVG(Maas) > 5000;
```

---

## Örnek Tablo: Calisanlar

| CalisanID | Adi   | Departman  | Maas  | Telefon   |
|-----------|-------|------------|-------|-----------|
| 1         | Ali   | IT         | 6000  | 555-1234  |
| 2         | Ayşe  | Muhasebe   | 4500  | 555-5678  |
| 3         | Ahmet | Pazarlama  | 3000  | NULL      |
| 4         | Can   | IT         | 7000  | 555-0000  |
| 5         | Ece   | Muhasebe   | 5000  | 555-9999  |

---

##  Açıklama
Bu bölümde öğrendiklerin:

- SQL’de veri toplama işlemleri (SUM, AVG, COUNT vs.)
- Gruplama ve filtreleme (`GROUP BY`, `HAVING`)
- Veri özetleme ve raporlama mantığını kavramak için temel yapı taşlarıdır.
