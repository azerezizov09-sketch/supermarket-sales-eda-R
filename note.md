# Supermarket satış məlumatları üzrə EDA

## Metodologiya

**Dataset:** `supermarket_sales - Sheet1.csv` (GitHub: cwentz12/Supermarket-Sales-Analysis). 1000 sifariş, 17 sütun, 3 filial (A, B, C), tarix aralığı: yanvar–mart 2019.

**Alətlər:** Tapşırıq **R** ilə həll edilib
**Addımlar:**
1. Faylı yüklədim, ölçünü (1000 x 17), sütun tiplərini və boş dəyərləri yoxladım. Heç bir sütunda boş dəyər yoxdur.
2. `Date` sütununu tarix formatına (`mdy`), `Time` sütunundan isə saatı (`Hour`) çıxardım. `Month` sütunu əlavə etdim.
3. `group_by` və `summarise` ilə Branch, Product line, Customer type və Gender üzrə ümumi satışı (`Total` cəmi) və sifariş sayını hesabladım.
4. Saat üzrə satış və sifariş sayına baxıb ən yoğun saatları tapdım.
5. Məhsul kateqoriyalarını ümumi satışa görə sıraladım (ən yaxşı və ən zəif).
6. Qrafiklər çəkdim: məhsul kateqoriyası üzrə bar chart, müştəri növü üzrə pie chart, saat üzrə line chart, filial × kateqoriya heatmap.
7. Bonus: hər kateqoriya üçün gross margin faizini hesabladım.

"Satış" üçün `Total` sütunu (vergi daxil məbləğ) istifadə olunub.

## Əsas tapıntılar

1. **C filialı ən yüksək satışa malikdir, çünki orada orta sifariş məbləği daha böyükdür.** Ümumi satış: C ≈ 110 569, A ≈ 106 200, B ≈ 106 198. C-nin sifariş sayı ən azdır (328), amma orta sifariş məbləği ən yüksəkdir (337.10; A: 312.35, B: 319.87). Deməli C-də satışı sifariş sayı yox, sifariş məbləği artırır.

2. **Kateqoriyalar arasında fərq azdır, ən zəif kateqoriya Health and beauty-dir.** Ən yaxşı: Food and beverages (≈ 56 145) və Sports and travel (≈ 55 123). Ən zəif: Health and beauty (≈ 49 194), liderdən təxminən 12% geridir. Bu kateqoriya ən çox inkişaf potensialına malikdir.

3. **Ən yoğun saatlar 19:00 və 13:00-dır.** 19:00-da ən çox sifariş (113) və ən yüksək satış (≈ 39 700) var. İkinci zirvə 13:00-dadır (103 sifariş, ≈ 34 723). Kassir sayı və məhsul ehtiyatı bu saatlara görə planlaşdırıla bilər.

4. **Qadınlar kişilərdən daha çox xərcləyir və kateqoriya seçimləri fərqlidir.** Sifariş sayı demək olar ki, eynidir (501 və 499), amma qadınların satışı ≈ 167 883, kişilərinki ≈ 155 084-dür (orta sifariş: 335.10 və 310.79). Qadınlar Food and beverages-ə, kişilər isə Health and beauty-yə daha çox pul xərcləyir. Kampaniyaları hədəf qrupuna görə qurmaq olar.

## Əlavə qeydlər

- **Gross margin** bütün kateqoriyalarda eynidir (4.76%). Deməli kateqoriyalar arasında fərq mənfəət faizindən yox, satış həcmindən gəlir.
- **Aylar:** yanvar ən güclü aydır (≈ 116 292), fevral ən zəifdir (≈ 97 219). Fevral daha qısa aydır, ona görə bu fərq tam "zəiflik" deyil.