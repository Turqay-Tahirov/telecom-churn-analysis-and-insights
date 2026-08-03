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

## 📈 Korrelyasiya Analizi və Əsas Nəticələr

### 🔵 Güclü Müsbət Korrelyasiyalar
1. **`tenure` və `TotalCharges` (0.83):** Datadakı ən güclü əlaqədir. Müştərinin şirkətdə qaldığı ay sayı (`tenure`) artdıqca, şirkətə ödədiyi ümumi məbləğ (`TotalCharges`) düz mütənasib şəkildə yüksəlir.
2. **`MonthlyCharges` və `TotalCharges` (0.65):** Aylıq ödəniş məbləği yüksək olan müştərilərin təbii olaraq ümumi gəlirə verdiyi töhfə də daha böyük olur.
3. **`MonthlyCharges` və `StreamingTV` / `StreamingMovies` (0.63):** Müştərilər paketlərinə TV və Kino əlavə etdikcə, onların aylıq ödəniş haqqı kəskin şəkildə artır.
4. **`StreamingTV` və `StreamingMovies` (0.53):** Bu iki xidmət bir-biri ilə sıx bağlıdır. Platformada TV yayımlarını aktivləşdirən müştərilər çox böyük ehtimalla kino paketlərini də birlikdə alırlar.

---

### 🔴 Əsas Mənfi Korrelyasiyalar
1. **`tenure` və `Churn` (-0.35):** Datadakı ən güclü tərs mütənasib əlaqədir. Müştərinin şirkətdə qaldığı ay sayı (`tenure`) artdıqca, sistemdən çıxma/itki ehtimalı (`Churn`) azalır. Bu, **yeni müştərilərin şirkəti tərk etməyə ən çox meylli qrup olduğunu** riyazi olaraq sübut edir.
2. **`Dependents` və `SeniorCitizen` (-0.21):** Yaşlı müştərilərin (`SeniorCitizen`) himayəsində yetkinlik yaşına çatmayan və ya baxıma möhtac şəxslərin (`Dependents`) olma ehtimalı daha aşağıdır.
3. **`TotalCharges` və `Churn` (-0.20):** Şirkətə ümumi olaraq çox pul qazandırmış müştərilərin sistemdən çıxma riski daha azdır.

---

## 🎯 Strateji Biznes Təklifləri

* 🚀 **Yeni Müştərilərə Xüsusi Dəstək:** `tenure` və `Churn` arasındakı əlaqə (-0.35) göstərir ki, şirkəti tərk edənlərin çoxu yeni müştərilərdir. İlk 3 ayda onlara xüsusi diqqət, onboarding dəstəyi və müvəqqəti endirimlər edilməlidir.
* 📦 **Kino və TV-ni Paket Kimi Satmaq:** Bu iki xidmət bir-biri ilə sıx bağlı olduğu (0.53) və aylıq gəliri birbaşa artırdığı (0.63) üçün onları tək-tək yox, birləşdirilmiş vahid istirahət paketi kimi satmaq daha effektiv olacaqdır.
* 👑 **Sadiq Müştərilərin Qorunması (VIP Proqramlar):** Müştərinin şirkətdə qaldığı müddət artdıqca qazandırdığı ümumi pul maksimuma çatır (0.83). Bu sadiq müştəriləri itirməmək üçün onlara xüsusi VIP təhlükəsizlik, prioritetsiz dəstək və bonuslar təqdim edilməlidir.

## 🧰 İstifadə Olunan Alətlər
* **Dil:** Python
* **Kitabxanalar:** Pandas
* **Mühit:** Jupyter Notebook

  ## 👤 Author

**Turqay Tahirov**  
*Data Analyst*

* 🌐 **LinkedIn:** [linkedin.com/in/turqay-tahirov](https://linkedin.com/in/turqay-tahirov)
* 🐙 **GitHub:** [github.com/turqaytahirov](https://github.com/turqaytahirov)
* 📧 **Email:** [turqaytahirov@gmail.com](mailto:turqaytahirov@gmail.com)
