# employee-dataset
# Proyek Akhir: Menyelesaikan Permasalahan Turnover Karyawan pada Perusahaan Edutech

## 1. Business Understanding  
Perusahaan Edutech XYZ bergerak di bidang pengembangan platform pembelajaran daring yang terus berkembang pesat. Untuk menjaga kualitas layanan dan pertumbuhan, perusahaan perlu mempertahankan talenta kunci—mulai dari pengembang produk, tim R&D, hingga staf pendukung operasional. Namun, tingkat keluar-masuk karyawan (attrition) yang relatif tinggi mengancam stabilitas tim dan mengurangi efektivitas inisiatif strategis.

## 2. Permasalahan Bisnis  
- **Tingkat Attrition yang Meningkat**  
  Hanya 14% karyawan yang resign, tetapi tren kenaikan tahunan menunjukkan potensi gangguan tim.  
- **Identifikasi Faktor Utama**  
  Belum ada sistem yang memadai untuk memahami faktor-faktor penyebab resign, sehingga intervensi HR sifatnya reaktif.  
- **Alokasi Sumber Daya**  
  Tanpa prediksi risiko resign, anggaran untuk retention dipakai secara kurang tepat sasaran.

## 3. Cakupan Proyek  
- **Eksploratory Data Analysis (EDA)**  
  — Deskriptif distribusi demografi, kepuasan kerja, pola lembur, dsb.  
- **Statistical Testing**  
  — Chi-square untuk variabel kategorikal (BusinessTravel, MaritalStatus, OverTime)  
  — T-test untuk variabel numerik (Age, MonthlyIncome, dll.)  
- **Predictive Modeling**  
  — Pipeline: one-hot encoding → scaling → SMOTE → Random Forest  
  — Evaluasi: akurasi, confusion matrix, classification report  
- **Feature Importance**  
  — Ekstraksi dan visualisasi fitur paling berpengaruh  
- **Deployment & Dashboard**  
  — Export hasil prediksi & importance ke Excel/CSV  
  — Dashboard interaktif di Tableau Public  

## 4. Persiapan  
- **Sumber Data**  
  – `employee_data_imputed.csv` (data karyawan historis lengkap setelah imputasi)  
- **Setup Environment**  
  1. Clone repo ini  
  2. Buat virtual environment (contoh):  
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     pip install -r requirements.txt
     ```  
  3. Jalankan notebook di `colab/employee_attrition_modeling.ipynb`

## 5. Business Dashboard  
Dashboard interaktif yang menampilkan:  
- **Prediction Table**: daftar karyawan dengan probabilitas resign, kelas prediksi, dan tingkat risiko (High/Medium/Low)  
- **Risk Distribution**: bar/pie chart sebaran risiko resign  
- **Top-N High Risk**: highlight top 10 karyawan berisiko tinggi  
- **Feature Importance**: bar chart faktor-faktor utama pemicu resign  

**Link Tableau Public:**  
https://public.tableau.com/views/HRAttritionDashboard/Overview

## 6. Conclusion  
- Model Random Forest setelah SMOTE mencapai akurasi ~88% dalam memprediksi resign.  
- Faktor terkuat: **OverTime**, **YearsWithCurrManager**, dan **EnvironmentSatisfaction**.  
- Hanya 2 karyawan “High Risk” (prob ≥ 80%), sehingga program retensi dapat difokuskan pada segmen kecil.

## 7. Rekomendasi Action Items  
1. **Intervensi Lembur**  
   — Tinjau kebijakan lembur, berikan kompensasi atau fleksibilitas kerja bagi karyawan yang sering lembur.  
2. **Program Kepuasan Lingkungan Kerja**  
   — Tingkatkan engagement & well-being (survey rutin, kegiatan team bonding) untuk meningkatkan `EnvironmentSatisfaction`.  
3. **Retention Check-In dengan Manager**  
   — Buat jadwal meeting berkala antara karyawan dan manajer untuk memantau kepuasan & hambatan dalam pekerjaan—khususnya pada 18 karyawan “Medium Risk”.  
