# Analisis Sentimen: Fenomena "Tembok Ratapan Solo" (2026)

## Background

Project ini dibuat untuk tracking dan menganalisis percakapan publik terkait fenomena viral **"Tembok Ratapan Solo"** pada Februari 2026.

Fokus utamanya adalah memastikan apakah fenomena ini berpotensi jadi krisis reputasi serius, atau cuma bagian dari budaya digital seperti meme, humor, dan kreativitas netizen.

---

## Objective

* Mengukur proporsi kritik negatif serius dibanding konten bercanda.
* Memvalidasi apakah perlu tindakan dari tim PR/Humas.
* Membangun sistem alert otomatis jika sentimen negatif harian melewati batas aman.

---

## Tools & Tech Stack

* **Bahasa**: Python
* **Data Handling & Visualisasi**: Pandas, Matplotlib
* **Model Sentimen**: IndoBERT (via Hugging Face) untuk klasifikasi Bahasa Indonesia

---

## How It Works

### 1. Data Collection

Mengumpulkan ±5.000 percakapan dari:

* X (Twitter)
* YouTube

---

### 2. Text Preprocessing

Data dibersihkan dengan:

* Menghapus URL
* Menghapus mention (@username)
* Menghapus karakter khusus dan noise
* Normalisasi teks

Tujuannya supaya model NLP bisa baca konteks lebih akurat.

---

### 3. Sentiment Prediction

Teks yang sudah dibersihkan diproses menggunakan **IndoBERT** dan diklasifikasikan menjadi:

* Positif
* Netral
* Negatif

---

### 4. Sarkasme Correction (Post-Processing Logic)

Model AI sering miss konteks sarkasme atau humor.

Contoh:

> "Kreatif banget sindirannya"

Bisa terbaca negatif oleh model, padahal konteksnya apresiasi humor.

Solusi yang dipakai:

* Rule-based post-processing
* Keyword adjustment untuk konteks sarkasme
* Validasi manual pada sampel data

---

### 5. Monitoring & Alert System

Sistem monitoring harian dibuat untuk:

* Menghitung persentase sentimen negatif per hari
* Mengaktifkan alert jika sentimen negatif > 35%

Threshold krisis ditetapkan di angka **35%**.

---

## Key Findings

Setelah klasifikasi dan koreksi kontekstual, hasil akhirnya:

| Sentimen | Persentase |
| -------- | ---------- |
| Positif  | 49.0%      |
| Netral   | 32.4%      |
| Negatif  | 18.6%      |

---

## Interpretasi

* **Positif (49.0%)**
  Dominan. Banyak berisi apresiasi, humor, meme, dan kreativitas digital.

* **Netral (32.4%)**
  Konten informatif, pertanyaan lokasi, atau sekadar ikut tren.

* **Negatif (18.6%)**
  Kritik serius atau sindiran tajam.

---

## Kesimpulan

**Status: Aman**

Fenomena ini lebih condong ke arah hiburan dan budaya digital.

Dengan sentimen negatif sebesar **18.6%** (masih jauh di bawah ambang krisis 35%), belum diperlukan intervensi komunikasi atau strategi PR yang serius.

Monitoring tetap dijalankan untuk memastikan tidak ada lonjakan sentimen negatif di hari-hari berikutnya.
