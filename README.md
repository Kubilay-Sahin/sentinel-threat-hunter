# 🛡️ Sentinel: Cloud-Native Threat Detection Pipeline

![Status](https://img.shields.io/badge/Status-Active_Development-green)
![Platform](https://img.shields.io/badge/Platform-Google_Cloud-blue)
![Python](https://img.shields.io/badge/Python-3.10%2B-yellow)

## 📋 Executive Summary
**Sentinel**, siber güvenlik tehditlerini simüle eden, gerçek zamanlı olarak işleyen ve bulut tabanlı bir veri ambarında analiz eden uçtan uca (end-to-end) bir veri hattı projesidir. 

Bu proje, modern **DevSecOps** pratiklerini ve **Serverless** (Sunucusuz) mimariyi kullanarak; ölçeklenebilir, düşük maliyetli ve yüksek performanslı bir log analiz altyapısı kurmayı hedefler. Geleneksel log yönetiminin ötesine geçerek, büyük veri teknolojileri (BigQuery) ile siber saldırı paternlerini tespit eder.

## 🏗️ Architecture (Sistem Mimarisi)

Veri akışı şu aşamalardan oluşur:

1.  **Data Generation (Simülasyon):** Python tabanlı bir script, çeşitli siber saldırı senaryolarını (DDoS, SQL Injection, Brute Force) ve normal trafiği simüle eden JSON formatında loglar üretir.
2.  **Ingestion (Veri Alımı):** Loglar, **Google Cloud Pub/Sub** servisine "topic" bazlı olarak anlık iletilir. Bu sayede sistem, veri üreten ve tüketen kaynakları birbirinden ayırır (Decoupling).
3.  **Processing (İşleme):** Pub/Sub üzerindeki mesajlar, **Google Cloud Functions** (Serverless) tarafından tetiklenir. Bu fonksiyon veriyi temizler, doğrular ve yapılandırır.
4.  **Storage & Analytics (Depolama ve Analiz):** İşlenen veriler **Google BigQuery** veri ambarına yazılır. Burada SQL kullanılarak saldırı vektörleri analiz edilir.

---

## 🛠️ Tech Stack (Teknolojiler)

* **Language:** Python 3.12
* **Cloud Provider:** Google Cloud Platform (GCP)
* **Messaging:** Cloud Pub/Sub
* **Compute (Serverless):** Cloud Run Functions
* **Data Warehouse:** BigQuery
* **Version Control:** Git & GitHub

## 🚀 Key Features (Özellikler)

* **Real-Time Data Streaming:** Logların üretildiği an ile analiz edildiği an arasındaki gecikme (latency) minimize edilmiştir.
* **Scalability:** Pub/Sub ve Serverless mimari sayesinde, saniyede gelen log sayısı 10'dan 10.000'e çıksa bile altyapı otomatik olarak ölçeklenir.
* **Cybersecurity Simulation:** Gerçekçi saldırı senaryoları (Status 403, SQLi payloadları vb.) içerir.
* **Infrastructure as Code (IaC):** (Geliştirme aşamasında) Altyapı kod ile yönetilebilir.

---

## 💻 Installation & Usage (Kurulum ve Kullanım)

### Ön Gereksinimler
* Google Cloud hesabı ve aktif bir proje.
* Python 3.10+ ve `pip`.
* Google Cloud SDK (gcloud CLI).

### 1. Projeyi Klonlayın
```bash
  2. Sanal Ortamı Kurun
  Bash
  
  python -m venv venv
  # Windows için:
  .\venv\Scripts\activate
  # Mac/Linux için:
  source venv/bin/activate
