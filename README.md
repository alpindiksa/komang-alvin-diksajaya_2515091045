# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[KOMANG ALVIN DIKSAJAYA]`
- **NIM:** `[2515091045]`
- **Program Studi:** `[SISTEM INFORMASI]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek


Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_startup_saas.csv` yang berisi informasi tentang `"Nama_Startup","Kategori_Layanan","Pendapatan_Tahunan_Miliar_IDR","Biaya_Akuisisi_Pelanggan_Juta_IDR","Nilai_Pelanggan_Juta_IDR","Tingkat_Churn_Persen"`. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `Pendapatan_Tahunan_Miliar_IDR` dan `Nilai_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `Pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...*dari variabel Pendapatan_Tahunan_Miliar_IDR di dapatkan Mean:31.88, Median:31.3, Modus:1.87
  - *Interpretasi:* Dari Mean : 31,88 kita tahu kalau secara rata-rata pendapatan tahunan startup dalam dataset adalah sekitar 31,88 miliar rupiah.
                    Dari Median: 31.3 kita tahu kalau nilai tengah pendapatan tahunan startup adalah 31,3 miliar rupiah, artinya setengah dari startup memiliki pendapatan di bawah angka tersebut dan setengah lainnya di atasnya.
                    Dari Modus: 1.87 kita tahu kalau sebagian besar startup dalam dataset memiliki pendapatan tahunan sebesar 1,87 miliar rupiah.”
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*dari Pendapatan_Tahunan_Miliar_IDR didapatkan standar deviasi:19.79, Range: 1 - 66.89, Kuartil 1: 14,31 ,kuartil 2: 31,30, kuartil 3: 49,04
  - *Interpretasi:*Standar deviasi sebesar 19,79 menunjukkan bahwa nilai pendapatan cukup bervariasi dan tidak terkonsentrasi di sekitar rata-rata. 
                   Range yang lebar, yaitu dari 1 hingga 66,89 miliar rupiah, menandakan adanya perbedaan yang besar antara pendapatan terendah dan tertinggi.
                   Selain itu, jarak antar kuartil yang cukup besar (Q3–Q1) dapat disimpulkan bahwa data pendapatan tidak homogen dan memiliki tingkat penyebaran yang tinggi.
  
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results/histogram_Pendapatan_Tahunan_Miliar_IDR*
  - *Interpretasi:* Histogram menunjukkan bahwa pendapatan tahunan startup memiliki distribusi yang cenderung merata
                    namun terdapat lonjakan frekuensi yang signifikan pada rentang pendapatan rendah (sekitar 0–10 miliar IDR)
                    Garis merah putus-putus menunjukkan nilai Mean sebesar 31,88 miliar IDR. Terlihat bahwa rata-rata berada tepat di tengah persebaran data
                    Data menunjukkan bahwa ekosistem startup dalam dataset ini sangat heterogen

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*1.497e-14
  - *Interpretasi:* data tidak berdistribusi dengan normal karena nilai p-value 1,497e-14 jauh lebih kecil daripada taraf signifikansi  0,05 ,
                    Implikasinya: Peralihan Uji Statistik: Saya harus menggunakan uji non-parametrik (seperti Spearman atau Mann-Whitney) 
                    karena uji parametrik (seperti uji-t atau Pearson) sudah tidak valid untuk data ini.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results/qqplot_Pendapatan_Tahunan_Miliar_IDR*
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
                    titik-titiknya dari tidak mengikuti garis menjadi mengikuti garis kemudian tidak mengikuti garis lagi 
                    artinya Berdasarkan grafik tersebut, distribusi pendapatan startup cenderung rata di bagian tengah 
                    namun memiliki puncak frekuensi yang mencolok di area pendapatan rendah (0–10 miliar IDR), yang mengonfirmasi nilai Modus 1,87.
                    Meskipun garis merah menunjukkan Mean (31,88) berada di tengah, batang histogram yang tersebar lebar dari 1 hingga 66,89 miliar 
                    tanpa pola lonceng membuktikan adanya variansi data yang sangat tinggi sesuai dengan Standar Deviasi 19,79. Selain itu, 
                    terdapat penurunan jumlah startup yang drastis pada kelompok pendapatan tertinggi (di atas 65 miliar IDR), yang mengindikasikan bahwa hanya segelintir startup yang mampu mencapai level pendapatan maksimal tersebut.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*"Koefisien Korelasi (r) = 0.997"
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
                    korelasi antara Pendapatan_Tahunan_Miliar_IDR dan Nilai_Pelanggan_Juta_IDR korelasinya positif kuat
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Nilai_Pelanggan_Juta_IDR*
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
                    ya pola pada scatter plot mendukung hasil korelasi karena arahnya naik tandanya psotifi dan membentuk garis tandanya korelasinya kuat

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Nilai_Pelanggan_Juta_IDR  =  3.57  +  3.02  *Pendapatan_Tahunan_Miliar_IDR*
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
                    b0 = 3.57 berarti jika pendapatan tahunan perusahaan adalah 0 miliar IDR, maka nilai pelanggan diprediksi sebesar 3,57 juta IDR.
                    b1 = 3.02 berarti bahwa setiap kenaikan 1 miliar IDR Pendapatan_Tahunan_Miliar_IDR akan meningkatkan Nilai_Pelanggan_Juta_IDR sebesar 3,02 juta IDR, dengan asumsi variabel lain konstan.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared ...*0.994
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
                    variasi dari variabel dependen yang dapat dijelaskan oleh model regresi saya adalah 99.4 %
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results/plot_regresi_Pendapatan_Tahunan_Miliar_IDR_vs_Nilai_Pelanggan_Juta_IDR*
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
                    Garis regresi yang menanjak dan lurus menunjukkan hubungan linear positif, 
                    di mana peningkatan pendapatan tahunan diikuti oleh peningkatan nilai pelanggan.
---

## 6. Kesimpulan

Dari analisi diatas, dapat disimpulkan bahwa pendapatan tahunan startup dalam dataset memiliki nilai rata-rata sebesar 31,88 miliar IDR dengan median 31,3 miliar IDR dan modus 1,87 miliar IDR. Ini menunjukkan meskipun rata-rata pendapatan berada di kisaran menengah, sebagian besar startup alah memiliki pendapatan yang relatif rendah. Nilai standar deviasinya yang cukup besar serta rentang datanya yang lebar mengindikasikan bahwa pendapatan startup sangat bervariasi dan tidak bersifat homogen.
Hasil uji normalitas Shapiro–Wilk menunjukkan bahwa data pendapatan tahunan tidak berdistribusi normal. Kondisi ini menandakan adanya variasi data yang besar serta kemungkinan nilai ekstrem, sehingga hasil analisis perlu dipahami sebagai gambaran umumnya saja , bukan representasi ideal
Analisis korelasi menunjukkan adanya hubungan positif yang sangat kuat antara Pendapatan_Tahunan_Miliar_IDR dan Nilai_Pelanggan_Juta_IDR dengan koefisien korelasi sebesar 0,997. Hubungan ini didukung oleh scatter plot yang membentuk pola menaik dan mendekati garis lurus, yang menandakan bahwa peningkatan pendapatan tahunan sejalan dengan peningkatan nilai pelanggan.
Hasil analisis regresi memperkuat temuan tersebut melalui persamaan model Y = 3,57 + 3,02X. Nilai konstanta sebesar 3,57 menunjukkan adanya nilai dasar pelanggan ketika pendapatan sangat rendah, sedangkan koefisien regresi sebesar 3,02 menunjukkan bahwa setiap kenaikan 1 miliar IDR pendapatan tahunan akan meningkatkan nilai pelanggan sebesar 3,02 juta IDR. Nilai R-squared sebesar 0,994 menunjukkan bahwa model regresi mampu menjelaskan 99,4% variasi nilai pelanggan, sehingga pendapatan tahunan dapat dikatakan sebagai faktor yang sangat dominan dalam menjelaskan nilai pelanggan pada dataset ini.

