# 🧠 Workflow CI/CD: Prediksi Kesehatan Mental

Proyek ini merupakan implementasi Continuous Integration (CI) menggunakan MLflow Project dan GitHub Actions untuk otomatisasi training model prediksi kesehatan mental.

Model ini dibangun untuk memprediksi apakah seseorang membutuhkan treatment terkait kesehatan mental berdasarkan faktor-faktor demografis dan kondisi pekerjaan.

---

## 🎯 Tujuan Proyek

* Mengembangkan **model prediksi kesehatan mental**
* Melakukan **tracking dan logging eksperimen** menggunakan MLflow
* Mengimplementasikan **Continuous Integration (CI)** dengan GitHub Actions
* Menghasilkan **model terbaru** setiap terjadi perubahan pada kode sumber (push/pull request)

---

## 📊 Dataset

Dataset yang digunakan merupakan hasil preprocessing dengan fitur-fitur berikut:

| Fitur                       | Deskripsi                                        |
| --------------------------- | ------------------------------------------------ |
| Age                         | Usia responden                                   |
| Gender                      | Jenis kelamin                                    |
| self\_employed              | Status wiraswasta                                |
| family\_history             | Riwayat keluarga terkait kesehatan mental        |
| work\_interfere             | Dampak kesehatan mental terhadap pekerjaan       |
| no\_employees               | Jumlah karyawan di perusahaan                    |
| remote\_work                | Status kerja jarak jauh                          |
| tech\_company               | Bekerja di perusahaan teknologi                  |
| benefits                    | Fasilitas kesehatan mental                       |
| care\_options               | Pilihan perawatan kesehatan mental               |
| wellness\_program           | Program kesehatan mental di tempat kerja         |
| seek\_help                  | Kemudahan mendapatkan bantuan kesehatan mental   |
| anonymity                   | Perlindungan privasi terkait kesehatan mental    |
| leave                       | Kemudahan cuti untuk kesehatan mental            |
| mental\_health\_consequence | Dampak isu kesehatan mental terhadap karir       |
| phys\_health\_consequence   | Dampak kesehatan fisik terhadap karir            |
| coworkers                   | Dukungan rekan kerja                             |
| supervisor                  | Dukungan dari atasan                             |
| mental\_health\_interview   | Kenyamanan bicara isu mental saat interview      |
| phys\_health\_interview     | Kenyamanan bicara kesehatan fisik saat interview |
| mental\_vs\_physical        | Kesetaraan antara isu mental dan fisik           |
| obs\_consequence            | Pernah mengalami konsekuensi akibat isu mental   |

**Target prediksi:** `treatment` (1 = Perlu Treatment, 0 = Tidak Perlu Treatment)

---

## 📁 Struktur Direktori

```
Workflow-CI/
├── .github/workflows/       # Berisi konfigurasi GitHub Actions CI
│   └── ci.yml
├── MLProject/               # MLflow Project folder
│   ├── MLProject            # Konfigurasi MLflow Project
│   ├── conda.yaml           # Environment dependencies (conda)
│   ├── modelling.py         # Script training model
│   └── mental_health_cleaned.csv  # Dataset hasil preprocessing
└── README.md
```

---

## ⚙️ Konfigurasi MLflow Project

File `MLproject` mendeskripsikan proyek MLflow beserta parameter yang digunakan:

```yaml
name: mental-health-prediction

entry_points:
  main:
    parameters:
      n_estimators: {type: int, default: 100}
      random_state: {type: int, default: 42}
    command: "python modelling.py --n_estimators {n_estimators} --random_state {random_state}"
```

---

## 🚀 Cara Menjalankan Proyek

### ✅ Persyaratan

* Python 3.8 atau lebih baru
* Conda/Miniconda
* MLflow >= 2.0
* Git

### 🔧 Jalankan Proyek secara Lokal

1. Clone repository:

```bash
git clone https://github.com/nfvalenn/Workflow_CI.git
cd Workflow_CI
```

2. Jalankan MLflow Project:

```bash
mlflow run . --env-manager=local
```

3. Menjalankan dengan parameter khusus (opsional):

```bash
mlflow run . -P n_estimators=200 -P random_state=42 --env-manager=local
```

---

## 🔄 Workflow CI/CD (GitHub Actions)

Setiap terjadi push atau pull request ke repository ini, GitHub Actions akan menjalankan alur berikut:

1. Checkout repository
2. Setup Python environment
3. Install dependencies
4. Menjalankan training model dengan MLflow
5. Melakukan logging hasil eksperimen ke MLflow Tracking

---

## 🙋‍♀️

| Nama                           | Username Dicoding |                                                                                                                                    |
| ------------------------------ | ----------------- |
| **Nabila Febriyanti Valentin** | nfvalenn          |
---
