# Dokumentasi API Flask

## 1️⃣ Pendahuluan

API ini digunakan untuk memprediksi kategori dana berdasarkan input kebutuhan, keinginan, uang saku, dan tabungan. API ini memiliki dua endpoint utama dan juga ini kolom / fitur yang ada di API ini : 

1. **KOLOM :**

   **Kebutuhan (int) : Nominal kebutuhan**

   **Keinginan (int) : Nominal keinginan**

   **Uang Saku (int) : Nominal uang saku**

   **Tabungan (int) : Nominal tabungan**

## 2️⃣ URL Base API

- Jika masih lokal:
  ```
  http://127.0.0.1:5000
  ```
- Jika menggunakan Ngrok:
  ```
  https://0adf-35-204-23-58.ngrok-free.app/predict/post
  ```

## 3️⃣ Endpoint API

### 📌 Metode: POST

- **Endpoint:** `/predict/post`

- **URL :** [https://0adf-35-204-23-58.ngrok-free.app/predict/post](https://0adf-35-204-23-58.ngrok-free.app/predict/post)

- **Deskripsi: Menggunakan body JSON untuk melakukan prediksi.**

- **Request Format (JSON):**

  ```json
  {
    "Kebutuhan": 5000000,
    "Keinginan": 250000,
    "Uang Saku": 3000000,
    "Tabungan": 5000000
  }
  ```

- **Response Format (JSON):**

  ```json
  {
    "prediction": 0,
    "prediction_label": "Kurang",
    "return": {
      "Kebutuhan": 230000,
      "Keinginan": 250000,
      "Uang Saku": 1000000,
      "Tabungan": 540000
    }
  }
  ```

### 📌 Metode: GET

- **Endpoint:** `/predict/get`
- **URL** : [http://127.0.0.1:5000/predict/get](http://127.0.0.1:5000/predict/get)
- **Deskripsi: Menerima parameter melalui URL untuk melakukan prediksi. Pengguna dapat mengganti nilai parameter langsung di URL (melalui search bar browser atau API client seperti Postman) tanpa perlu mengedit kode.**

  **Request Format (URL Params):**
  ```
  http://127.0.0.1:5000/predict/get?Kebutuhan=5000000&Keinginan=250000&Uang_Saku=1000000&Tabungan=540000
  ```
- **Response Format (JSON):**
  ```json
  {
    "prediction": 2,
    "prediction_label": "Lebih",
    "return": {   
      "Kebutuhan": 5000000,
      "Keinginan": 250000,
      "Uang Saku": 1000000,
      "Tabungan": 540000
    }
  }
  ```

## 4️⃣ Cara Menjalankan API (Untuk Dev BE & FE)

- **Jika menggunakan VS Code (lokal):**
  ```sh
  python app.py
  ```
- **Jika menggunakan Google Colab:**
  ```python
  from flask_ngrok import run_with_ngrok
  run_with_ngrok(app)
  app.run()
  ```
- **Gunakan Ngrok jika perlu expose ke Front-End:**
  ```sh
  !ngrok authtoken YOUR_NGROK_AUTH_TOKEN
  ```

**NOTE** : ***Metode Post*** hanya bisa dijalankan di ***google colab***
