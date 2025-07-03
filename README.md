# Green-Finance-Data-Analisis

# 🌱 Analisis Green Finance | Self-Learning Project
Hai, Sobat ETL! 👋

Apa kabar hari ini? Semoga tetap semangat dan sehat selalu yaa 💪

Selamat datang di repositori ini — repositori ini dibuat sebagai bagian dari **self-learning journey** untuk memahami dan menganalisis green finance, atau gampangnya: menganalisis cara keuangan yang digunakan untuk proyek peduli sama lingkungan 🌍💸. Proyek ini mendalami bagaimana data dapat digunakan untuk mengevaluasi dampak lingkungan dan finansial dari inisiatif keberlanjutan.

# 🎯 Tujuan Proyek
Tujuan utama dari proyek self-learning ini adalah:

- **Memahami konsep green finance dari sisi data**, termasuk bagaimana data digunakan untuk mengukur dampak dan risiko proyek berkelanjutan.

- Melihat **analisis green finance berdampak terhadap lingkungan dan sosial yang terukur**, dengan fokus pada metrik kunci seperti pengurangan emisi CO2, penciptaan lapangan kerja, dan peningkatan akses energi bersih.

- **Mengeksplorasi bagaimana kita dapat menggunakan data historis untuk memprediksi keberhasilan dan risiko proyek hijau**, termasuk penerapan teknik Machine Learning sederhana.

- **Membedah berbagai variabel dalam dataset yang relevan**, mulai dari data finansial, lingkungan, hingga sosial-ekonomi, dan memahami interkoneksinya dalam konteks keberlanjutan.


# 1. Deskripsi Green Finance

**Green Finance** adalah pendekatan keuangan inovatif yang mengarahkan investasi dan pembiayaan ke proyek-proyek dengan dampak positif dan terukur terhadap lingkungan. Fokus utamanya adalah mendukung transisi global menuju ekonomi rendah karbon dan berkelanjutan. Ini mencakup pembiayaan untuk berbagai inisiatif, antara lain:

- **Energi Terbarukan**: Investasi pada pembangkit listrik tenaga surya (PLTS), pembangkit listrik tenaga mikrohidro (PLTM), angin, panas bumi, dan biomassa.

- **Pengelolaan Limbah Berkelanjutan**: Proyek-proyek yang berfokus pada daur ulang, pengolahan limbah, dan pengurangan sampah.

- **Transportasi Ramah Lingkungan**: Pengembangan infrastruktur dan kendaraan listrik, transportasi publik rendah emisi, dan jalur sepeda.

- **Efisiensi Energi**: Peningkatan efisiensi di sektor industri, bangunan, dan rumah tangga.

- **Adaptasi dan Mitigasi Perubahan Iklim**: Proyek yang membantu komunitas beradaptasi dengan dampak perubahan iklim atau mengurangi emisi gas rumah kaca.


**Komponen Utama Green Finance:**
- **Investasi Hijau**: Ini merujuk pada proyek-proyek konkret yang dirancang untuk memberikan dampak lingkungan positif, seperti mengurangi emisi, menghemat energi, mengelola sumber daya secara berkelanjutan, atau mengkonservasi keanekaragaman hayati.

- **Instrumen Keuangan Hijau**: Meliputi berbagai produk dan layanan keuangan yang dirancang khusus untuk memfasilitasi investasi hijau:
  - **Green Bond**: Obligasi yang penerbitannya secara spesifik untuk membiayai proyek-proyek hijau.
  - **Green Loan**: Pinjaman yang ditujukan untuk proyek dengan manfaat lingkungan.
  - **ESG Fund (Environmental, Social, Governance Fund)**: Dana investasi yang memilih aset berdasarkan kriteria lingkungan, sosial, dan tata kelola perusahaan yang baik.


**Manfaat Green Finance:**
- **Pengurangan Risiko Jangka Panjang**: Membantu memitigasi risiko finansial dan operasional yang timbul dari perubahan iklim dan degradasi lingkungan.

- **Peningkatan Transparansi Lingkungan**: Mendorong sektor keuangan untuk lebih transparan dalam pelaporan dampak lingkungan dari investasi mereka.

- **Insentif Investor dan Penerbit**: Memberikan daya tarik bagi investor yang peduli lingkungan, seringkali melalui kondisi yang lebih menguntungkan (misalnya greenium, yaitu selisih imbal hasil yang lebih rendah pada green bond dibandingkan obligasi konvensional, menunjukkan permintaan yang tinggi).

## ⚖️ Regulasi Green Finance di Indonesia

Indonesia telah menunjukkan komitmen kuat terhadap keberlanjutan melalui pengembangan kerangka regulasi Green Finance yang progresif. Regulasi ini menjadi landasan bagi lembaga keuangan dan pelaku usaha untuk berinvestasi pada proyek-proyek hijau:

- **Taksonomi Hijau Indonesia (THI) – OJK 2022:**
  - Merupakan sistem klasifikasi komprehensif yang dikembangkan oleh Otoritas Jasa Keuangan (OJK) untuk menilai apakah sebuah kegiatan ekonomi tergolong "hijau" atau berkelanjutan.
  - THI menetapkan kriteria teknis dan sektor prioritas yang jelas, memberikan panduan bagi investor dan lembaga keuangan dalam mengidentifikasi dan membiayai proyek yang benar-benar memberikan manfaat lingkungan.


- **POJK No. 60/POJK.04/2017 tentang Penerbitan dan Persyaratan Efek Bersifat Utang dan Sukuk Berlandaskan Prinsip Syariah (Green Bond):**

  - Peraturan ini secara khusus mengatur penerbitan Green Bond di Indonesia.

  - Mencakup ketentuan mengenai pelaporan dampak lingkungan dari proyek yang dibiayai oleh Green Bond, serta penilaian kelayakan proyek hijau untuk memastikan integritas dan akuntabilitas.

- **POJK No. 51/POJK.03/2017 tentang Penerapan Keuangan Berkelanjutan bagi Lembaga Jasa Keuangan, Emiten, dan Perusahaan Publik:**

  - Mewajibkan lembaga keuangan untuk menyusun Rencana Aksi Keuangan Berkelanjutan (RAKB).

  - Mendorong penilaian portofolio berdasarkan prinsip keberlanjutan, termasuk analisis Green Net Present Value (GNPV) dan dampak lingkungan, sosial, dan tata kelola (ESG), yang mendorong integrasi faktor-faktor non-finansial dalam pengambilan keputusan investasi.

# 2. Analisis Field Dataset

Bagian ini akan menjelaskan setiap dataset yang digunakan dalam analisis, beserta rumus dan temuan kunci dari setiap pertanyaan tugas. Kode Python yang digunakan untuk menghasilkan analisis juga akan disertakan.

Sebelum kita masuk ke analisis per dataset, mari siapkan lingkungan kerja dan muat semua data yang diperlukan:

```Python

import pandas as pd
import numpy as np # Untuk penanganan NaN di pandas
import os

# Fungsi helper untuk pemuatan data yang robust
def load_data_robustly(file_name):
    """
    Memuat data dari file Excel dan menangani pengecualian (exceptions).
    """
    try:
        df = pd.read_excel(file_name)
        print(f"Data '{file_name}' berhasil dimuat.")
        return df
    except FileNotFoundError:
        print(f"ERROR: File '{file_name}' tidak ditemukan. Pastikan lokasi file sudah benar.")
        return None
    except Exception as e:
        print(f"ERROR saat memuat '{file_name}': {e}")
        return None

# Muat semua dataset yang relevan
df_economic = load_data_robustly('Data/Economic_Dataset.xlsx')
df_social = load_data_robustly('Data/Social_Dataset.xlsx')
df_environmental = load_data_robustly('Data/Environmental_Dataset.xlsx')
df_geospatial = load_data_robustly('Data/Geospatial_Dataset.xlsx')
df_financial = load_data_robustly('Data/Financial_Dataset.xlsx')

# Verifikasi semua data telah dimuat. Jika ada kegagalan, hentikan operasi.
if not all([df_economic, df_social, df_environmental, df_geospatial, df_financial]):
    print("\n[PERSIAPAN GAGAL] Tidak semua dataset dapat dimuat. Periksa nama file dan jalur.")
    #exit() # Hentikan eksekusi jika data utama tidak tersedia (bisa diaktifkan jika ini skrip berjalan independen)
else:
    print("\nSemua data klien siap untuk analisis awal.\n")
```
**2.1 Financial Dataset**
Financial_Dataset ini krusial untuk menganalisis kelayakan ekonomi dan risiko finansial dari setiap proyek. Ini berisi informasi langsung terkait investasi dan pembiayaan.

**📊 Struktur Dataset**

|`Nama Field`|Deskripsi Singkat|
|-|-
|`Project_ID`|Kode unik untuk mengidentifikasi setiap proyek (misal: PLTS-NTT-001).|
|`Investment_Cost`|Total dana yang diinvestasikan dalam proyek (dalam miliar rupiah). Ini adalah skala finansial proyek.|
|`Loan_Interest_Rate`|Suku bunga tahunan (%) yang diterapkan pada pinjaman proyek, memengaruhi biaya modal.|
|`Default_Risk_Score`|Skor risiko gagal bayar (0–100), menunjukkan probabilitas proyek tidak dapat memenuhi kewajiban finansialnya.|
|`Green_Bond_Spread`|Selisih imbal hasil (dalam basis poin, bps) antara green bond proyek ini dan obligasi biasa, mencerminkan greenium atau diskon/premium hijau.|


**📐 Rumus Green Net Present Value (GNPV)**

GNPV adalah metrik penting yang memperhitungkan tidak hanya arus kas finansial, tetapi juga nilai moneter dari eksternalitas lingkungan (misalnya, penghematan karbon).

$$GNPV = \sum_{t=1}^{N} \frac{(CF_t + E_t)}{(1+r)^t} - I_0$$
 
**Keterangan:**

- $GNPV$: **Green Net Present Value** (nilai kini bersih hijau).
* $CF_t$: Arus kas bersih konvensional pada tahun ke-($t$).
* $E_t$: Nilai eksternalitas lingkungan (misalnya pengurangan emisi CO₂, penghematan air) pada tahun ke-($t$).
* $r$: Tingkat diskonto (contoh: 0.05 untuk 5%).
* $t$: Tahun ke-($t$).
* $N$: Umur proyek (dalam tahun).
* $I_0$: Investasi awal proyek.


**✅ GNPV yang lebih tinggi menunjukkan proyek lebih layak secara finansial dan berkontribusi pada keberlanjutan lingkungan.** Proyek dianggap layak jika $GNPV
ge0$.

**2.2 Environmental Dataset**

`Environmental_Dataset` adalah kumpulan data vital yang merekam dampak lingkungan yang dihasilkan oleh setiap proyek energi hijau. Dataset ini sangat penting dalam mendukung keputusan investasi berbasis lingkungan (green investment), khususnya dalam rangka transisi energi bersih dan kebijakan pembiayaan hijau di Indonesia.

**📊 Struktur Dataset**

|Nama Kolom|Deskripsi Singkat|
|-|-
|`Project_ID`|Kode unik untuk mengidentifikasi setiap proyek (misal: PLTS-NTT-001).|
|`CO2_Reduction`|Estimasi pengurangan emisi karbon tahunan (dalam ton CO2e), metrik kunci untuk dampak iklim.|
|`Energy_Output`|Produksi energi tahunan (dalam satuan kWh atau MWh), menunjukkan kontribusi proyek terhadap pasokan energi.|
|`Environmental_Risk_Index`|Skor risiko lingkungan proyek (skala 0–100, makin tinggi skornya, makin berisiko). Ini mencakup risiko seperti dampak terhadap ekosistem lokal.|
|Konteks_Lingkungan|Deskripsi singkat kondisi lingkungan atau ekologi setempat, memberikan konteks geografis dan ekologis.|
|Peringkat_Dampak|Penilaian kualitatif terhadap dampak lingkungan secara keseluruhan (contoh: High / Medium / Low).|



**🌿 Rumus Carbon Return on Investment (CROI)**

CROI adalah metrik efisiensi yang mengukur seberapa efektif investasi dalam proyek lingkungan dalam menghasilkan pengurangan emisi karbon. Semakin tinggi CROI, semakin banyak karbon yang dikurangi per unit investasi.

$$CROI = \frac{\sum_{t=1}^{N}(R_t \times P_C)}{I_0}$$

**Keterangan:**
* $CROI$: **Carbon Return on Investment**.
* $R_t$: Emisi karbon yang berhasil dikurangi pada tahun ke-($t$) (ton CO₂e).
* $P_C$: Harga karbon per ton CO₂e (dalam Rupiah).
* $I_0$: Investasi awal proyek (dalam Rupiah).
* $N$: Umur proyek (dalam tahun).

✅ Nilai CROI yang lebih tinggi menandakan efisiensi karbon yang lebih baik per unit investasi.

## Soal 1: Conditional Statements (If-Else) and Arithmetic Operations
**Deskripsi**: Pemerintah ingin mengidentifikasi proyek PLTS dengan efisiensi pengurangan CO2 yang tinggi per unit investasi, dihitung sebagai pengurangan CO2 per juta rupiah.

**Pendekatan Analisis:**
Untuk menjawab pertanyaan ini, kami menggabungkan data lingkungan dan finansial untuk mendapatkan gambaran komprehensif. Kemudian, kami menyaring proyek berdasarkan Project_ID yang dimulai dengan "PLTS" dan menghitung rasio efisiensi. Rasio ini dikategorikan sebagai "High" atau "Low" menggunakan logika kondisional.

**Langkah-langkah Teknis:**

1. **Penggabungan Dataset:** Menggunakan fungsi `pd.merge()` untuk menggabungkan `df_environmental` dan `df_financial` berdasarkan kolom `Project_ID`. Metode `inner join` digunakan untuk memastikan hanya proyek yang ada di kedua dataset yang dianalisis.

2. **Penyaringan Data:** Memfilter `DataFrame` yang telah digabungkan untuk hanya menyertakan baris di mana Project_ID dimulai dengan string "PLTS" menggunakan metode string .str.startswith().
3. **Perhitungan Rasio Efisiensi:** Rasio dihitung dengan membagi `CO2_Reduction` (dalam ton CO2e) dengan `Investment_Cost` (yang dikonversi dari miliar rupiah menjadi juta rupiah dengan mengalikan 1000). Penanganan `ZeroDivisionError` diimplementasikan untuk kasus di mana `Investment_Cost` adalah nol, mengembalikan `NaN` dan kemudian menampilkannya sebagai "Tidak dapat dihitung".

4. **Klasifikasi Kondisional:** Fungsi `apply()` dengan lambda expression digunakan untuk membuat kolom `Category`. Jika `Ratio >= 0.5`, kategori adalah "High"; jika tidak, kategori adalah "Low". Penanganan `NaN` juga disertakan untuk rasio yang tidak dapat dihitung.

5. **Pencetakan Hasil:** Melakukan iterasi melalui baris `DataFrame` yang difilter dan mencetak `Project_ID`, `Ratio` (diformat dua desimal), dan `Category` menggunakan f-strings untuk output yang jelas dan mudah dibaca.

**Rumus Perhitungan:**

$$Efisiensi\ CO2 = \frac{CO2\_Reduction\ (ton\ CO2e)}{Investment\_Cost\ (miliar\ Rp) \times 1.000}\ ton\ CO2e/juta\ Rp$$

**Kode Python (`main_analysis.py`):**

```Python

# --- SOAL 1: Conditional Statements (If-Else) and Arithmetic Operations ---
print("\n--- SOAL 1: Efisiensi Pengurangan CO2 Proyek PLTS ---")
print("Tujuan: Mengidentifikasi proyek PLTS dengan efisiensi pengurangan CO2 tinggi per juta rupiah investasi.\n")

# 1. Gabungkan Environmental_Dataset dan Financial_Dataset menggunakan Project_ID.
merged_df_q1 = pd.merge(df_environmental, df_financial, on='Project_ID', how='inner')

# 2. Untuk PLTS projects (Project_ID starts with "PLTS"), compute the ratio: CO2_Reduction / (Investment_Cost * 1_000_000).
# Catatan: Investment_Cost dalam billion rupiah. Untuk rasio per juta rupiah, kita kalikan 1_000 (karena 1 miliar = 1000 juta).
plts_projects = merged_df_q1[merged_df_q1['Project_ID'].str.startswith('PLTS')].copy()

# Hitung rasio, pastikan Investment_Cost tidak nol untuk menghindari ZeroDivisionError
plts_projects['Ratio'] = plts_projects.apply(
    lambda row: row['CO2_Reduction'] / (row['Investment_Cost'] * 1000) if row['Investment_Cost'] != 0 else np.nan,
    axis=1
)

# 3. Use if-else to classify the ratio as "High" (≥ 0.5 tons CO2e/million Rp) or "Low" (< 0.5).
plts_projects['Category'] = plts_projects['Ratio'].apply(lambda x: "High" if x >= 0.5 else "Low" if not pd.isna(x) else "N/A")

# 4. Display results as: "Project_ID: Ratio (Category)" using f-strings.
print("Output Hasil Analisis Soal 1:")
for index, row in plts_projects.iterrows():
    if not pd.isna(row['Ratio']):
        print(f"{row['Project_ID']}: {row['Ratio']:.2f} ({row['Category']})")
    else:
        print(f"{row['Project_ID']}: Tidak dapat dihitung (Biaya Investasi nol atau hilang)")
print("\n" + "-" * 80 + "\n")
```
**Output Hasil Analisis Soal 1 (Contoh):**

```
PLTS-JATIM-001: 0.45 (Low)
PLTS-SULSEL-001: 0.50 (High)
PLTS-JABW-001: 0.50 (High)
```

**Interpretasi Hasil Soal 1:**
Dari analisis ini, terlihat bahwa proyek-proyek PLTS seperti **PLTS-SULSEL-001** dan **PLTS-JABW-001** menunjukkan efisiensi pengurangan CO2 yang tinggi (0.50 ton CO2e per juta rupiah investasi atau lebih). Ini berarti setiap satu juta rupiah yang diinvestasikan pada proyek-proyek ini menghasilkan pengurangan emisi CO2 yang signifikan, menjadikannya sangat menarik dari perspektif dampak lingkungan dan efisiensi investasi. Sebaliknya, proyek PLTS-JATIM-001 memiliki efisiensi yang sedikit lebih rendah (0.45), yang masih berkontribusi pada pengurangan CO2 tetapi tidak seefisien proyek kategori "High". Informasi ini krusial bagi pemerintah atau investor untuk mengarahkan pendanaan ke proyek-proyek yang menawarkan dampak lingkungan terbaik per unit investasi.

# Soal 2: For Loop and Lists

**Deskripsi:** Pemerintah perlu menghitung rata-rata pengurangan CO2 di seluruh proyek PLTM untuk menilai dampak lingkungan kolektif mereka.

**Pendekatan Analisis:**
Tugas ini berfokus pada penggunaan for loop dan lists untuk memproses data. Kami akan mengekstrak data pengurangan CO2 khusus untuk proyek PLTM, lalu menghitung total dan rata-rata secara manual menggunakan loop.

**Langkah-langkah Teknis:**

- **Ekstraksi Data:** Melakukan iterasi melalui `df_environmental`. Setiap `Project_ID` diperiksa apakah dimulai dengan "PLTM" menggunakan .`startswith()`. Jika ya, nilai `CO2_Reduction` ditambahkan ke sebuah list bernama `pltm_co2_reductions`.

- **Agregasi Manual:** Sebuah *for loop* terpisah digunakan untuk menjumlahkan semua nilai dalam `pltm_co2_reductions` dan menghitung jumlah proyek PLTM. Pendekatan ini secara eksplisit menunjukkan pemahaman tentang bagaimana *for loop* digunakan untuk agregasi.

- **Perhitungan Rata-rata:** Rata-rata dihitung dengan membagi total pengurangan CO2 dengan jumlah proyek PLTM. Penanganan kasus di mana tidak ada proyek PLTM (untuk menghindari `ZeroDivisionError`) juga disertakan.

- **Pencetakan Hasil:** Hasil rata-rata ditampilkan, dibulatkan ke bilangan bulat terdekat (`.0f`).

**Rumus Perhitungan:**

$$Rata-rata\ CO2\_Reduction\ PLTM = \frac{\sum CO2\_Reduction_{PLTM}}{Jumlah\ Proyek\ PLTM}$$

**Kode Python (`main_analysis.py`):**

```Python

# --- SOAL 2: For Loop and Lists ---
print("\n--- SOAL 2: Rata-rata Pengurangan CO2 Proyek PLTM ---")
print("Tujuan: Menilai dampak lingkungan kolektif proyek PLTM dengan menghitung rata-rata pengurangan CO2 mereka.\n")

# 1. Gunakan Environmental_Dataset.xlsx. (df_environmental sudah dimuat di awal)
# 2. Buat list dari nilai CO2_Reduction untuk proyek PLTM (Project_ID starts with "PLTM").
pltm_co2_reductions = []
for index, row in df_environmental.iterrows():
    if row['Project_ID'].startswith('PLTM'):
        pltm_co2_reductions.append(row['CO2_Reduction'])

# 3. Gunakan for loop untuk menghitung total CO2 reduction dan jumlah proyek PLTM.
total_co2_reduction_pltm = 0
count_pltm_projects = 0
for co2_val in pltm_co2_reductions:
    total_co2_reduction_pltm += co2_val
    count_pltm_projects += 1

# 4. Hitung dan tampilkan rata-ratanya.
average_co2_reduction_pltm = 0
if count_pltm_projects > 0:
    average_co2_reduction_pltm = total_co2_reduction_pltm / count_pltm_projects
else:
    print("Tidak ada proyek PLTM yang ditemukan dalam dataset.")

print("Output Hasil Analisis Soal 2:")
print(f"Average CO2 Reduction for PLTM Projects: {average_co2_reduction_pltm:.0f} tons CO2e")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal 2 (Contoh):**

`Average CO2 Reduction for PLTM Projects: 31500 tons CO2e`

**Interpretasi Hasil Soal 2:**
Rata-rata pengurangan CO2 untuk proyek PLTM adalah **31,500 ton CO2e**. Angka ini memberikan gambaran kolektif tentang kontribusi proyek-proyek PLTM terhadap mitigasi perubahan iklim. Meskipun mungkin lebih kecil dibandingkan proyek PLTS skala besar, kontribusi ini penting dalam portofolio energi terbarukan Indonesia, terutama karena PLTM sering beroperasi di lokasi terpencil dan dapat memberikan manfaat energi terdesentralisasi. Rata-rata ini menjadi metrik dasar untuk membandingkan kinerja lingkungan antar jenis proyek dan menginformasikan kebijakan di masa mendatang.

# Soal 3: While Loop and User Input

**Deskripsi:** Pemerintah membutuhkan alat untuk memeriksa status lahan dan tingkat konflik sosial dengan memasukkan `Project_ID` secara interaktif.

**Pendekatan Analisis:**
Soal ini menguji kemampuan dalam menangani input pengguna dan mengelola alur program menggunakan while loop. Sebuah dictionary digunakan untuk penyimpanan data yang efisien, memungkinkan pencarian data sosial proyek secara cepat.

**Langkah-langkah Teknis:**

1. **Persiapan Data:** `df_social` dikonversi menjadi sebuah dictionary (`social_data_dict`) di mana `Project_ID` menjadi kunci dan nilai adalah sebuah dictionary yang berisi kolom-kolom lain untuk baris tersebut. Ini memungkinkan pencarian data yang sangat cepat berdasarkan `Project_ID`.

2. **While Loop Interaktif:** Sebuah while loop tak terbatas (while True) digunakan untuk terus meminta input Project_ID dari pengguna. Loop akan berhenti ketika pengguna mengetik "DONE".

3. **Penanganan Input:**

  - Input pengguna diproses (`.strip().upper()`) untuk menghilangkan spasi berlebih dan mengubahnya menjadi huruf kapital agar pencarian tidak case-sensitive.

  - Jika input adalah "DONE", loop dihentikan dengan `break`.

  - Jika `Project_ID` ditemukan dalam `social_data_dict`, informasi Land_Status dan `Tingkat_Konflik` ditampilkan.

  - Jika `Project_ID` tidak ditemukan, pesan "Project not found" ditampilkan.

**Kode Python (`main_analysis.py`):**

```Python

# --- SOAL 3: While Loop and User Input ---
print("\n--- SOAL 3: Pemeriksa Status Lahan dan Tingkat Konflik Proyek ---")
print("Tujuan: Menyediakan alat interaktif untuk memeriksa status lahan dan tingkat konflik sosial proyek.\n")

# 1. Gunakan Social_Dataset.xlsx. (df_social sudah dimuat di awal)
# Buat dictionary untuk akses cepat data sosial
social_data_dict = df_social.set_index('Project_ID').to_dict('index')

print("Output Hasil Analisis Soal 3:")
print("Masukkan Project_ID untuk melihat detail (ketik 'DONE' untuk selesai):")
while True:
    project_id_input = input("Enter Project_ID: ").strip().upper()

    if project_id_input == "DONE":
        print("Selesai.")
        break
    elif project_id_input in social_data_dict:
        data = social_data_dict[project_id_input]
        print(f"{project_id_input} - Land Status: {data['Land_Status']}, Tingkat Konflik: {data['Tingkat_Konflik']}")
    else:
        print("Project not found")
print("\n" + "-" * 80 + "\n")
```
**Output Hasil Analisis Soal 3 (Contoh Interaksi):**

```
Output Hasil Analisis Soal 3: Masukkan Project_ID untuk melihat detail (ketik 'DONE' untuk selesai):
Enter Project_ID: PLTS-NTT-001
PLTS-NTT-001 - Land Status: Adat, Tingkat Konflik: High
Enter Project_ID: INVALID-ID
Project not found
Enter Project_ID: PLTS-JATIM-001
PLTS-JATIM-001 - Land Status: Negara, Tingkat Konflik: Low
Enter Project_ID: DONE
Selesai.
```

**Interpretasi Hasil Soal 3:**
Alat interaktif ini memungkinkan pengguna untuk dengan cepat mencari informasi kritis mengenai status lahan dan tingkat konflik sosial dari setiap proyek. Misalnya, dengan memasukkan **"PLTS-NTT-001"**, kita dapat segera melihat bahwa status lahannya adalah "Adat" dengan **"Tingkat Konflik: High"**, yang mengindikasikan potensi tantangan dalam akuisisi lahan atau penerimaan komunitas. Sebaliknya, **"PLTS-JATIM-001"** menunjukkan **"Land Status: Negara"** dan **"Tingkat Konflik: Low"**, yang mungkin berarti jalur proyek yang lebih mulus dari perspektif sosial. Kemampuan untuk secara instan mengakses data ini sangat berharga untuk penilaian risiko awal dan perencanaan strategi keterlibatan masyarakat.

# Soal 4: Dictionary and Conditional Filtering

**Deskripsi:** Pemerintah mencari proyek dengan daya tarik investasi tinggi dan tingkat konflik sosial rendah untuk meminimalkan risiko.

**Pendekatan Analisis:**
Soal ini menggabungkan penggunaan dictionary dan conditional filtering. Data dari dua dataset berbeda digabungkan, kemudian diproses ke dalam dictionary untuk mempermudah pemfilteran berdasarkan kriteria ganda.

**Langkah-langkah Teknis:**

- **Penggabungan Data:** `df_economic` dan `df_social` digabungkan menggunakan `pd.merge()` berdasarkan `Project_ID`. Ini penting karena kriteria yang diinginkan tersebar di dua *dataset* tersebut (`Daya_Tarik_Investasi` dari ekonomi dan `Tingkat_Konflik` dari sosial).

- **Pembentukan Dictionary:** Sebuah dictionary baru (`project_criteria_dict`) dibuat. Setiap `Project_ID` dijadikan kunci, dan nilai yang terkait adalah sebuah tuple yang berisi `Daya_Tarik_Investasi` dan `Tingkat_Konflik` untuk proyek tersebut. Pendekatan ini mengkonsolidasi informasi yang relevan untuk setiap proyek.

- **Pemfilteran Kondisional:** Sebuah *for loop* digunakan untuk mengiterasi melalui `items()` dari `project_criteria_dict`. Di dalam *loop*, pernyataan `if` digunakan untuk memeriksa dua kondisi secara bersamaan: `Daya_Tarik_Investasi harus` "High" DAN `Tingkat_Konflik` harus "Low". Proyek yang memenuhi kedua kriteria ini ditambahkan ke *list* `filtered_projects_q4`.

- **Pencetakan Hasil:** Daftar `Project_ID` yang difilter dicetak. Jika tidak ada proyek yang memenuhi kriteria, pesan yang sesuai akan ditampilkan.

**Kode Python (`main_analysis.py`):**

```Python

# --- SOAL 4: Dictionary and Conditional Filtering ---
print("\n--- SOAL 4: Proyek dengan Daya Tarik Investasi Tinggi dan Konflik Rendah ---")
print("Tujuan: Mengidentifikasi proyek yang optimal dengan daya tarik investasi tinggi dan risiko konflik sosial rendah.\n")

# 1. Gabungkan Economic_Dataset.xlsx dan Social_Dataset.xlsx menggunakan Project_ID.
merged_df_q4 = pd.merge(df_economic, df_social, on='Project_ID', how='inner')

# 2. Buat dictionary dengan Project_ID sebagai keys dan tuple (Daya_Tarik_Investasi, Tingkat_Konflik) sebagai values.
project_criteria_dict = {}
for index, row in merged_df_q4.iterrows():
    project_criteria_dict[row['Project_ID']] = (row['Daya_Tarik_Investasi'], row['Tingkat_Konflik'])

# 3. Gunakan for loop dengan if untuk memfilter proyek di mana Daya_Tarik_Investasi == "High" dan Tingkat_Konflik == "Low".
filtered_projects_q4 = []
for project_id, criteria in project_criteria_dict.items():
    if criteria[0] == "High" and criteria[1] == "Low":
        filtered_projects_q4.append(project_id)

# 4. Tampilkan Project_IDs yang difilter.
print("Output Hasil Analisis Soal 4:")
print("Projects with High Investment Attractiveness and Low Conflict:")
if filtered_projects_q4:
    for project_id in filtered_projects_q4:
        print(project_id)
else:
    print("Tidak ada proyek yang memenuhi kriteria ini dalam dataset.")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal 4 (Contoh):**

```
Projects with High Investment Attractiveness and Low Conflict:
PLTS-JATIM-001
PLTS-SULSEL-001
PLTS-JABW-001
```

**Interpretasi Hasil Soal 4:**

Analisis ini berhasil mengidentifikasi proyek-proyek yang paling menjanjikan dari sudut pandang ekonomi dan sosial. Proyek-proyek seperti **PLTS-JATIM-001, PLTS-SULSEL-001**, dan **PLTS-JABW-001** memenuhi kriteria **"Daya Tarik Investasi: High"** dan **"Tingkat Konflik: Low"**. Ini berarti proyek-proyek ini tidak hanya menarik secara finansial tetapi juga memiliki penerimaan komunitas yang baik dan risiko sosial yang minimal, menjadikannya pilihan investasi yang optimal bagi pemerintah yang ingin meminimalkan potensi hambatan dan memastikan keberlanjutan proyek dalam jangka panjang.

# Soal 5: Functions and Arithmetic

**Deskripsi:** Pemerintah perlu menghitung total investasi untuk proyek-proyek dengan efisiensi lokasi tinggi.

**Pendekatan Analisis:**

Soal ini menekankan penggunaan fungsi (`def`) untuk mengorganisir kode dan melakukan perhitungan aritmatika. Data lokasi dan finansial digabungkan, dan fungsi yang dibuat akan memproses data ini untuk menjumlahkan investasi dari proyek-proyek yang memenuhi kriteria lokasi.

**Langkah-langkah Teknis:**

- **Penggabungan Data:** `df_geospatial` dan `df_financial` digabungkan berdasarkan `Project_ID` untuk mendapatkan informasi `Efisiensi_Lokasi` dan `Investment_Cost` dalam satu `DataFrame`.

- **Definisi Fungsi** (`calculate_total_investment`):

  - Fungsi ini menerima satu argumen: sebuah `DataFrame` yang telah digabungkan.

  - Di dalamnya, sebuah for loop mengiterasi setiap baris `DataFrame`.

  - Kondisi `if row['Efisiensi_Lokasi'] == "High"` digunakan untuk memfilter proyek.

  - Jika kondisi terpenuhi, `Investment_Cost` dari proyek tersebut ditambahkan ke `total_investment`.

  - Fungsi mengembalikan total investasi.

- **Pemanggilan Fungsi dan Pencetakan Hasil:** Fungsi `calculate_total_investment` dipanggil dengan `DataFrame` gabungan sebagai argumen. Hasilnya kemudian dicetak dengan format yang rapi, dibulatkan hingga dua desimal, dan diberi satuan "billion Rp".

**Rumus Perhitungan:**

$$Total\ Investasi\ (Efisiensi\ Lokasi\ Tinggi) = \sum_{Proyek\ i\ dengan\ Efisiensi\ Lokasi\ Tinggi} Investment\_Cost_i$$
​
Kode Python (`main_analysis.py`):

```Python

# --- SOAL 5: Functions and Arithmetic ---
print("\n--- SOAL 5: Total Investasi untuk Lokasi Efisiensi Tinggi ---")
print("Tujuan: Menghitung akumulasi investasi pada proyek-proyek yang berlokasi sangat efisien.\n")

# 1. Gabungkan Geospatial_Dataset.xlsx dan Financial_Dataset.xlsx.
merged_df_q5 = pd.merge(df_geospatial, df_financial, on='Project_ID', how='inner')

# 2. Definisikan fungsi calculate_total_investment.
def calculate_total_investment(data_frame):
    """
    Menghitung total Investment_Cost untuk proyek dengan Efisiensi_Lokasi "High".

    Args:
        data_frame (pd.DataFrame): DataFrame gabungan dari data Geospatial dan Financial.

    Returns:
        float: Total Investment_Cost dalam billion Rp.
    """
    total_investment = 0
    for index, row in data_frame.iterrows():
        if row['Efisiensi_Lokasi'] == "High":
            total_investment += row['Investment_Cost']
    return total_investment

# 3. Panggil fungsi dan tampilkan hasilnya.
total_inv_high_efficiency = calculate_total_investment(merged_df_q5)
print("Output Hasil Analisis Soal 5:")
print(f"Total Investment for High-Efficiency Locations: {total_inv_high_efficiency:.2f} billion Rp")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal 5 (Contoh):**

`Total Investment for High-Efficiency Locations: 330.00 billion Rp`

**Interpretasi Hasil Soal 5:**
Analisis ini menunjukkan bahwa total investasi untuk proyek-proyek yang berlokasi dengan efisiensi tinggi adalah **330.00 miliar Rp**. Angka ini sangat penting untuk pengalokasian sumber daya. Lokasi dengan efisiensi tinggi (misalnya, karena iradiasi surya optimal, kedekatan dengan jaringan listrik, atau aksesibilitas yang baik) seringkali menawarkan potensi pengembalian investasi yang lebih besar dan risiko operasional yang lebih rendah. Oleh karena itu, mengetahui total investasi di area-area ini membantu pemerintah dan investor dalam mengidentifikasi seberapa besar modal yang telah diarahkan ke proyek-proyek dengan potensi keberhasilan yang lebih tinggi.

# Soal 6: Modules and Error Handling
**Deskripsi:** Pemerintah memerlukan alat yang dapat digunakan kembali untuk menghitung efisiensi pengurangan CO2 dengan penanganan kesalahan.

**Pendekatan Analisis:**
Soal ini berfokus pada modularitas dan penanganan kesalahan (`try-except`). Sebuah fungsi untuk menghitung efisiensi CO2 dibuat dalam modul terpisah (`green_analysis.py`), dan kemudian diimpor serta diuji di skrip utama. Penanganan kesalahan diterapkan untuk kasus `ZeroDivisionError` dan tipe input yang tidak valid.

**Langkah-langkah Teknis:**

- **Pembuatan Modul:** File `green_analysis.py` dibuat (seperti yang sudah kita siapkan), berisi fungsi `compute_co2_efficiency`. Fungsi ini menghitung rasio `CO2_Reduction` terhadap `Investment_Cost` (dikonversi ke juta rupiah).

- **Penanganan Kesalahan dalam Modul:**

  - `try-except ZeroDivisionError`: Blok `try-except` digunakan untuk menangkap kondisi di mana `Investment_Cost` adalah nol setelah dikonversi ke juta rupiah, mengembalikan pesan "Cannot compute: Investment Cost is zero."

  - `try-except ValueError`: Ditambahkan untuk menangani kasus di mana `CO2_Reduction` atau `Investment_Cost` bukan angka, mengembalikan pesan "Cannot compute: Invalid input types (non-numeric)."

  - `try-except Exception`: Sebagai penanganan umum untuk *error* lain yang tidak terduga.

- **Import Modul:** Di `main_analysis.py`, fungsi `compute_co2_efficiency` diimpor dari `green_analysis.py`. Penanganan `ImportError` juga ditambahkan jika modul tidak dapat ditemukan.

- **Pengujian Fungsi:** Fungsi ini diuji pada beberapa data proyek contoh, termasuk skenario di mana `Investment_Cost` adalah nol dan input adalah tipe yang salah, untuk menunjukkan bahwa penanganan kesalahan bekerja dengan baik.

**Rumus Perhitungan:**

$$Efisiensi\ CO2 = \frac{CO2\_Reduction\ (ton\ CO2e)}{Investment\_Cost\ (miliar\ Rp) \times 1.000}\ ton\ CO2e/juta\ Rp$$
  
Kode Python (`green_analysis.py`):

```Python

# green_analysis.py

def compute_co2_efficiency(co2_reduction, investment_cost_billion_rp):
    """
    Menghitung efisiensi pengurangan CO2 per juta rupiah investasi.

    Args:
        co2_reduction (float/int): Pengurangan CO2 dalam ton CO2e.
        investment_cost_billion_rp (float/int): Biaya investasi dalam miliar rupiah.

    Returns:
        float: Efisiensi CO2 dalam ton CO2e per juta rupiah investasi, atau None jika terjadi error.
    """
    try:
        # Pastikan input adalah numerik
        if not isinstance(co2_reduction, (int, float)) or not isinstance(investment_cost_billion_rp, (int, float)):
            raise ValueError("Input CO2_Reduction and Investment_Cost must be numeric.")

        investment_cost_million_rp = investment_cost_billion_rp * 1000  # Konversi miliar ke juta

        if investment_cost_million_rp == 0:
            raise ZeroDivisionError("Investment Cost is zero, cannot compute efficiency.")

        efficiency = co2_reduction / investment_cost_million_rp
        return efficiency
    except ZeroDivisionError as zde:
        return f"Cannot compute: {zde}"
    except ValueError as ve:
        return f"Cannot compute: {ve}"
    except Exception as e:
        return f"An unexpected error occurred: {e}"
```

**Kode Python (dalam `main_analysis.py` untuk menguji modul):**

```Python

# --- SOAL 6: Modules and Error Handling ---
print("\n--- SOAL 6: Komputasi Efisiensi Pengurangan CO2 dengan Error Handling ---")
print("Tujuan: Membuat alat yang dapat digunakan kembali dan tangguh untuk menghitung efisiensi CO2, dengan penanganan kesalahan yang robust.\n")

# Coba impor fungsi dari green_analysis.py
try:
    from green_analysis import compute_co2_efficiency
    print("Fungsi 'compute_co2_efficiency' berhasil diimpor dari 'green_analysis.py'.")
except ImportError:
    print("ERROR: Modul 'green_analysis.py' tidak ditemukan. Pastikan file berada di direktori yang sama atau di PYTHONPATH.")
    compute_co2_efficiency = None # Set to None if import fails to avoid further errors

if compute_co2_efficiency:
    print("Output Hasil Analisis Soal 6:")
    # Contoh penggunaan pada proyek yang ada
    # Misal PLTS-NTT-001 dari df_environmental dan df_financial
    # Project_ID: PLTS-NTT-001, CO2_Reduction: 50000, Investment_Cost: 100 miliar Rp
    co2_val_p1 = 50000
    inv_cost_p1 = 100
    result_p1 = compute_co2_efficiency(co2_val_p1, inv_cost_p1)
    print(f"PLTS-NTT-001: Efisiensi = {result_p1:.2f} ton CO2e/juta Rp" if isinstance(result_p1, float) else f"PLTS-NTT-001: {result_p1}")

    # Contoh skenario ZeroDivisionError
    co2_val_zero_inv = 10000
    inv_cost_zero = 0
    result_zero_inv = compute_co2_efficiency(co2_val_zero_inv, inv_cost_zero)
    print(f"TEST-ZERO-INV: {result_zero_inv}")

    # Contoh skenario ValueError (tipe data salah)
    co2_val_invalid_type = "invalid"
    inv_cost_invalid_type = 50
    result_invalid_type = compute_co2_efficiency(co2_val_invalid_type, inv_cost_invalid_type)
    print(f"TEST-INVALID-TYPE: {result_invalid_type}")
else:
    print("Tidak dapat menjalankan pengujian Soal 6 karena fungsi tidak dapat diimpor.")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal 6 (Contoh):**

`Fungsi 'compute_co2_efficiency' berhasil diimpor dari 'green_analysis.py'.
Output Hasil Analisis Soal 6:
PLTS-NTT-001: Efisiensi = 0.50 ton CO2e/juta Rp
TEST-ZERO-INV: Cannot compute: Investment Cost is zero, cannot compute efficiency.
TEST-INVALID-TYPE: Cannot compute: Input CO2_Reduction and Investment_Cost must be numeric.`

**Interpretasi Hasil Soal 6:**

Implementasi `compute_co2_efficiency` dalam modul terpisah dan pengujiannya menunjukkan pentingnya modularitas dan penanganan kesalahan yang robust. Fungsi ini berhasil menghitung efisiensi untuk input yang valid, dan secara graceful menangani kasus `Investment_Cost` nol (`ZeroDivisionError`) dan input non-numerik (`ValueError`). Hal ini memastikan bahwa alat analisis tetap andal bahkan ketika menghadapi data yang tidak sempurna atau skenario ekstrem, sebuah praktik krusial dalam rekayasa perangkat lunak dan analisis data dunia nyata.

# Soal 7: Rata-rata Output Energi dengan Penanganan Data Hilang

**Deskripsi:** Pemerintah perlu menghitung rata-rata output energi dari proyek terpilih, sambil menangani data yang hilang atau tidak valid secara graceful.

**Pendekatan Analisis:**

Soal ini menguji kemampuan untuk mengelola data yang hilang atau tidak valid dalam perhitungan agregasi. Pendekatan ini menggunakan kombinasi dictionary lookup dan validasi data sebelum melakukan perhitungan rata-rata.

**Langkah-langkah Teknis:**

1. **Persiapan Data Lookup:** `df_environmental` dikonversi menjadi sebuah dictionary (`environmental_data_lookup`) untuk akses cepat ke data berdasarkan `Project_ID`.

2. **Daftar Proyek Target:** Dibuat sebuah *list* `target_projects_q7` yang berisi `Project_ID` yang ingin dianalisis. *List* ini sengaja mencakup *ID* yang valid dan tidak valid untuk demonstrasi penanganan *error*.

3. **Iterasi dan Validasi Data:** Sebuah for loop mengiterasi melalui `target_projects_q7`.

 - Menggunakan `environmental_data_lookup.get()` untuk mencoba mengambil data output energi. Ini menghindari `KeyError` jika `Project_ID` tidak ditemukan.

 - Memeriksa apakah data yang diambil `pd.notna()` dan merupakan numerik menggunakan `isinstance()`.

 - Jika data valid, nilai `Energy_Output` ditambahkan ke `valid_energy_outputs` dan valid_project_count.

 - Jika data tidak ditemukan atau tidak valid, pesan peringatan yang sesuai dicetak.

4. **Perhitungan Rata-rata:** Total `Energy_Output` dibagi dengan `valid_project_count`. Penanganan `ZeroDivisionError` disertakan jika tidak ada proyek valid yang ditemukan.

5. **Pencetakan Hasil:** Rata-rata output energi ditampilkan.

**Rumus Perhitungan:**

$$Rata-rata\ Energy\ Output = \frac{\sum Energy\_Output_{Valid}}{Jumlah\ Proyek\ Valid}$$


Kode Python (`main_analysis.py`):

```Python

# --- SOAL 7: Rata-rata Output Energi dengan Penanganan Data Hilang ---
print("\n--- SOAL 7: Rata-rata Output Energi dengan Penanganan Data Hilang ---")
print("Tujuan: Menghitung rata-rata output energi dari proyek terpilih, sambil menangani data yang hilang atau tidak valid secara graceful.\n")

# 1. Gunakan Environmental_Dataset.xlsx. (df_environmental sudah dimuat di awal)
# Buat dictionary untuk akses cepat data lingkungan
environmental_data_lookup = df_environmental.set_index('Project_ID').to_dict('index')

# 2. Definisikan daftar Project_ID yang ingin dianalisis (contoh, termasuk ID yang mungkin hilang)
target_projects_q7 = ['PLTS-NTT-001', 'PLTM-JATENG-002', 'PLTA-BALI-005', 'PLTS-JABW-001', 'PROYEK-TIDAK-ADA']

valid_energy_outputs = []
valid_project_count = 0

print("Output Hasil Analisis Soal 7:")
print("Memproses proyek-proyek terpilih untuk rata-rata output energi:")
for project_id in target_projects_q7:
    project_data = environmental_data_lookup.get(project_id) # Gunakan .get() untuk menghindari KeyError
    if project_data and pd.notna(project_data.get('Energy_Output')):
        energy_output = project_data.get('Energy_Output')
        if isinstance(energy_output, (int, float)): # Pastikan itu numerik
            valid_energy_outputs.append(energy_output)
            valid_project_count += 1
        else:
            print(f"  Peringatan: Data Energy_Output untuk '{project_id}' tidak valid (bukan numerik).")
    else:
        print(f"  Peringatan: Project_ID '{project_id}' tidak ditemukan atau data Energy_Output hilang/kosong.")

average_energy_output_q7 = 0
if valid_project_count > 0:
    average_energy_output_q7 = sum(valid_energy_outputs) / valid_project_count
else:
    print("Tidak ada proyek valid dengan data Energy_Output yang ditemukan.")

print(f"Rata-rata Output Energi untuk Proyek Valid: {average_energy_output_q7:.0f} kWh")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal 7 (Contoh):**

`Output Hasil Analisis Soal 7:
Memproses proyek-proyek terpilih untuk rata-rata output energi:
  Peringatan: Project_ID 'PLTA-BALI-005' tidak ditemukan atau data Energy_Output hilang/kosong.
  Peringatan: Project_ID 'PROYEK-TIDAK-ADA' tidak ditemukan atau data Energy_Output hilang/kosong.
Rata-rata Output Energi untuk Proyek Valid: 40000 kWh`

**Interpretasi Hasil Soal 7:**
Analisis ini berhasil menghitung rata-rata *output* energi sambil secara *graceful* menangani `Project_ID` yang tidak ada (`PLTA-BALI-005`, `PROYEK-TIDAK-ADA`) atau data `Energy_Output` yang mungkin hilang atau tidak valid. Dengan menggunakan `.get()` dan validasi tipe data, skrip ini memastikan bahwa perhitungan hanya dilakukan pada data yang valid dan relevan, serta memberikan pesan peringatan yang jelas untuk kasus yang tidak bisa diproses. Ini adalah demonstrasi penting dari robustness dan penanganan data yang tidak sempurna, yang merupakan hal yang umum terjadi dalam dataset dunia nyata. Rata-rata output energi **40000 kWh** ini penting untuk mengevaluasi kontribusi rata-rata proyek terhadap pasokan energi bersih.

Soal Bonus: Memprediksi Daya Tarik Investasi dengan AI (Machine Learning)
Deskripsi: Menggunakan Machine Learning, khususnya Decision Tree Classifier, untuk memprediksi daya tarik investasi proyek berdasarkan fitur-fitur ekonomi, lingkungan, dan finansial.

**Pendekatan Analisis:**
Ini adalah tugas **klasifikasi**. Kita akan menggunakan `DecisionTreeClassifier` dari *scikit-learn*. Langkah-langkahnya meliputi penggabungan data, pra-pemrosesan (penanganan nilai hilang), pembagian data (pelatihan/pengujian), pelatihan model, evaluasi, dan prediksi.

**Konsep Pembelajaran Mesin yang akan kita gunakan:**

- **Fitur (X):** Variabel *input* atau independen yang akan kita gunakan untuk membuat prediksi. Dalam kasus ini, `GDP_Growth`, `CO2_Reduction`, dan `Investment_Cost`.

- **Target (y):** Variabel *output* atau dependen yang ingin kita prediksi. Di sini, `Daya_Tarik_Investasi` (yang memiliki nilai 'High' atau 'Low').

- `train_test_split`: Fungsi ini membagi dataset kita menjadi dua bagian: satu untuk melatih model (training set) dan satu lagi untuk menguji seberapa baik model berkinerja pada data yang belum pernah dilihat (test set). Ini penting untuk menghindari overfitting.

- `DecisionTreeClassifier`: Sebuah algoritma pembelajaran mesin yang membuat serangkaian keputusan seperti pohon untuk mengklasifikasikan data. Ini cocok untuk target kategorikal.

- `fit()`: Metode yang digunakan untuk "melatih" model. Selama proses ini, model belajar pola dari data pelatihan.

- `predict()`: Metode yang digunakan untuk membuat prediksi baru setelah model dilatih.

- `accuracy_score`: Metrik evaluasi yang menunjukkan proporsi prediksi yang benar dari total prediksi. Semakin tinggi akurasinya, semakin baik modelnya.

**Kode Python (`main_analysis.py`):**

```Python

# --- Import library Machine Learning yang diperlukan ---
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# --- SOAL BONUS: Memprediksi Daya Tarik Investasi dengan AI ---
print("\n--- SOAL BONUS: Memprediksi Daya Tarik Investasi dengan AI ---")
print("Tujuan: Menggunakan Machine Learning untuk memprediksi daya tarik investasi proyek.\n")

# 1. Gabungkan semua dataset yang relevan untuk model ML
# Menggunakan 'outer' join untuk memastikan semua Project_ID dari ketiga df dipertahankan
df_ml_full = pd.merge(df_economic, df_environmental, on='Project_ID', how='outer')
df_ml_full = pd.merge(df_ml_full, df_financial, on='Project_ID', how='outer')

# 2. Persiapan Data: Pilih Fitur (X) dan Target (y)
features_for_ml = ['GDP_Growth', 'CO2_Reduction', 'Investment_Cost']
target_for_ml = 'Daya_Tarik_Investasi'

# --- Penanganan Nilai Hilang (Pre-processing) ---
# Untuk fitur numerik: isi nilai yang hilang dengan rata-rata kolom
for col in features_for_ml:
    if df_ml_full[col].isnull().any():
        col_mean = df_ml_full[col].mean()
        df_ml_full[col] = df_ml_full[col].fillna(col_mean)
        print(f"Mengisi nilai hilang di '{col}' dengan rata-rata: {col_mean:.2f}")

# Untuk target kategorikal: hapus baris yang targetnya hilang (atau isi dengan mode/strategi lain)
if df_ml_full[target_for_ml].isnull().any():
    print(f"Menghapus baris dengan nilai hilang di kolom target '{target_for_ml}'.")
    df_ml_full.dropna(subset=[target_for_ml], inplace=True)

# Verifikasi setelah penanganan nilai hilang
if df_ml_full.empty:
    print("ERROR: DataFrame kosong setelah penanganan nilai hilang. Tidak dapat melanjutkan ML.")
    #exit() # Opsional: keluar jika data kosong

# Definisi Fitur (X) dan Target (y) setelah pembersihan
X = df_ml_full[features_for_ml]
y = df_ml_full[target_for_ml]

# 3. Bagi data menjadi set pelatihan dan pengujian (80% training, 20% testing)
# random_state memastikan bahwa pembagian data sama setiap kali kode dijalankan, untuk reproduktifitas.
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

print(f"\nData dibagi: {len(X_train)} sampel pelatihan, {len(X_test)} sampel pengujian.")

# 4. Inisialisasi dan latih Model Decision Tree Classifier
dt_model = DecisionTreeClassifier(random_state=42) # random_state untuk hasil yang konsisten
dt_model.fit(X_train, y_train)

# 5. Evaluasi Model
y_predictions = dt_model.predict(X_test)
accuracy = accuracy_score(y_test, y_predictions)
print(f"\nAkurasia Model pada Data Uji: {accuracy:.2f}") # Format ke 2 angka desimal

# 6. Prediksi untuk Proyek Baru
# Data proyek baru harus dalam format DataFrame dengan kolom yang sama dengan fitur pelatihan.
# Contoh skenario: Proyek dengan pertumbuhan GDP 5.0%, pengurangan CO2 70.000 ton, dan biaya investasi 150 miliar Rp.
new_project_scenario = pd.DataFrame([[5.0, 70000, 150]], columns=features_for_ml)
predicted_attractiveness = dt_model.predict(new_project_scenario)

print(f"\nPrediksi Daya Tarik Investasi untuk Proyek Baru (GDP_Growth=5.0, CO2_Reduction=70000, Investment_Cost=150): {predicted_attractiveness[0]}")
print("\n" + "-" * 80 + "\n")
```

**Output Hasil Analisis Soal Bonus (Contoh):**

```
Mengisi nilai hilang di 'GDP_Growth' dengan rata-rata: 4.80
Mengisi nilai hilang di 'CO2_Reduction' dengan rata-rata: 45000.00
Mengisi nilai hilang di 'Investment_Cost' dengan rata-rata: 95.00
Menghapus baris dengan nilai hilang di kolom target 'Daya_Tarik_Investasi.

Data dibagi: 8 sampel pelatihan, 2 sampel pengujian.

Akurasia Model pada Data Uji: 0.50

Prediksi Daya Tarik Investasi untuk Proyek Baru (GDP_Growth=5.0, CO2_Reduction=70000, Investment_Cost=150): High
```


**Interpretasi Hasil Soal Bonus:**

Tantangan bonus ini memperkenalkan Anda pada dasar-dasar **Pembelajaran Mesin (Machine Learning)**. Model `Decision Tree Classifier` dilatih pada data historis untuk memprediksi `Daya_Tarik_Investasi` proyek berdasarkan `GDP_Growth`, `CO2_Reduction`, dan `Investment_Cost`. Akurasi model pada data uji menunjukkan seberapa baik model dapat menggeneralisasi ke data baru. Meskipun akurasi dapat bervariasi tergantung pada dataset yang lebih besar, model ini dapat memberikan prediksi cepat untuk proyek baru, seperti yang ditunjukkan oleh prediksi "High" untuk proyek skenario tertentu. Ini menyoroti potensi AI dalam mendukung pengambilan keputusan investasi yang lebih efisien di sektor *Green Finance*.

## 🛠️ Cara Menjalankan Proyek Ini
Untuk menjalankan analisis ini di lingkungan lokal Anda:

1. **Clone Repositori:**

```Bash

git clone https://github.com/YOUR_USERNAME/Green-Finance-Analysis.git
cd Green-Finance-Analysis
```

(*Ganti `YOUR_USERNAME` dengan nama pengguna GitHub Anda*)

2. **Struktur Folder:** Pastikan Anda memiliki struktur folder yang benar seperti yang dijelaskan di awal `README.md` ini:

```
Green-Finance-Analysis/
├── Data/
│   ├── Economic_Dataset.xlsx
│   ├── Environmental_Dataset.xlsx
│   ├── Financial_Dataset.xlsx
│   ├── Geospatial_Dataset.xlsx
│   └── Social_Dataset.xlsx
├── main_analysis.py
├── green_analysis.py
├── README.md
└── .gitignore
```

Pastikan semua file `.xlsx` berada di dalam folder `Data/`.

3. **Buat Virtual Environment (Opsional, tapi Direkomendasikan):**

```Bash

python -m venv venv
# Di Windows:
.\venv\Scripts\activate
# Di macOS/Linux:
source venv/bin/activate
```

4. **Instal Dependensi:**

```Bash

pip install pandas openpyxl scikit-learn numpy
```

5. **Jalankan Skrip Utama:**

```Bash

python main_analysis.py
```

Skrip ini akan menjalankan semua analisis dan menampilkan output di konsol. Untuk Soal 3, Anda akan diminta untuk memasukkan input secara interaktif.

**🤝 Kontribusi**

Proyek ini adalah bagian dari perjalanan *self-learning*. Saran, *feedback*, atau kontribusi sangat diterima! Jika Anda memiliki ide untuk perbaikan, silakan buka issue atau buat *pull request*.

**📄 Lisensi**
Proyek ini dilisensikan di bawah Lisensi MIT.
