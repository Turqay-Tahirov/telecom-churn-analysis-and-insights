# 📊 Müştəri İtkisinin Analizi (Telecom Churn): Təmizləmə, EDA və Statistik Nəticələr

## 📌 Layihə Haqqında
Bu layihə telekommunikasiya sektorunda müştəri itkisinin (churn) qarşısını almaq üçün həyata keçirilmiş tam analitik prosesi əks etdirir. Layihə məlumatların təmizlənməsi (Data Cleaning), ilkin kəşfiyyat analizi (EDA), `groupby` funksiyaları ilə statistik seqmentasiyalar və biznes üçün strateji təklifləri əhatə edir.

---

## 🛠️ Əsas Analitik Mərhələlər

### 1. Məlumatların Təmizlənməsi və Hazırlanması (Data Cleaning)
* Struktur xətaları düzəldildi və tiplər çevrildi (məsələn, `TotalCharges` sütunu rəqəmsal formata gətirildi).
* Unikal identifikatorlar (`customerID`) yoxlanılaraq təkrar qeydlərin (duplicate) olmadığı təsdiqləndi.
* Kateqorial sütunlardaki anomaliyalar analitik dəqiqliyi qorumaq üçün standartlaşdırıldı.

### 2. Kəşfiyyat Məlumat Analizi (EDA)
* **Müqavilə və Ödəniş Tipləri:** Aylıq müqavilə (`Month-to-month`) və Elektron çek (`Electronic check`) istifadə edən müştərilərdə itki riski daha yüksəkdir.
* **İnfrastruktur:** Müştərilərin ~90.3%-i aktiv telefon xidmətindən (`PhoneService`) istifadə edir.
* **Demoqrafik Mənzərə:** Cinsiyyət bölgüsü bərabərdir (50/50), lakin partnyoru olan (`Partner`) müştərilərin sadiqlik göstəricisi daha yüksəkdir.

### 3. Statistik Təhlil və Əsas Nəticələr
* **Churn vs. Sadiqlik Müddəti və Aylıq Ödəniş:** 
  * Şirkətdən gedən müştərilərin (1) ortalama sadiqlik müddəti (`tenure`) daha qısa (~18 ay), aylıq ödənişləri isə daha yüksəkdir (~74.4).
  * Qalan müştərilər (0) daha uzun müddət sadiqlik göstərir (~37.6 ay) və aylıq ödənişləri daha aşağıdır (~61.3).
* **Rəqəmsal Ekosistem:** Kino izləmə (`StreamingMovies`) xidmətindən istifadə edənlərin sadiqlik müddətinin medianı 45 ay olduğu halda, bu xidməti almayanlarda cəmi 20 aydır.
* **Ailə Faktoru:** Partnyoru olan müştərilərin (`Partner=1`) ortalama sadiqlik müddəti (~41-42 ay), tək yaşayanlara nisbətən (~23 ay) təxminən iki dəfə çoxdur.

---

## 💡 Biznes Üçün Strateji Təkliflər

1. **Uzunmüddətli Müqavilə Həvəsləndirmələri:** Yüksək ödəniş edən aylıq müştərilərə xüsusi endirimlərlə 1-2 illik müqavilələrə keçid təklif edilərək `tenure` göstəricisi artırılmalıdır.
2. **Əlavə Xidmətlərin Paketləşdirilməsi:** Sadiqliyi 2 dəfədən çox artıran xidmətlər (`StreamingMovies`, `OnlineSecurity`) yuvarlaq tariflərə pulsuz və ya simvolik qiymətlə daxil edilməlidir.
3. **Ailə və Çoxlu Xətt Paketləri:** Tək yaşayan müştərilərin riskini azaltmaq üçün onları ekosistemə bağlayan ailə/dost endirim paketləri tətbiq olunmalıdır.
4. **Avtomatik Ödəniş Bonusları:** Elektron çekdən avtomatik bank ödənişinə (`Auto-payment`) keçən müştərilərə birdəfəlik keşbek və ya bonuslar verilməlidir.

---

## 🧰 İstifadə Olunan Alətlər
* **Dil:** Python
* **Kitabxanalar:** Pandas, NumPy, Matplotlib, Seaborn
* **Mühit:** Jupyter Notebook
