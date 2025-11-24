![CI Status](https://github.com/AuuAhMales/ci-tbp-kelompok/actions/workflows/ci.yml/badge.svg)

# CI-TBP-Kelompok

Dokumentasi proyek Continuous Integration (CI) untuk mata kuliah Rekayasa Perangkat Lunak / DevOps.

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi **Continuous Integration (CI)** menggunakan **GitHub Actions** dengan fitur:

* Linting menggunakan **ESLint v9**
* Unit testing menggunakan **Jest**
* Workflow otomatis berjalan setiap kali terjadi *push* ke branch `main`

Tujuan proyek ini adalah memastikan kode yang dikembangkan tetap konsisten, bebas error, dan dapat diuji secara otomatis.

---

## 👥 Anggota Kelompok

* Moh. Syahrul R. Umar - F55124050
* Moh. Reza - F55124045
* Moh. Faqih Al Habsyi - F55124080
* Miftahul Hidayat - F55124048
* Moh. Nabil Syaputra - F55124079

---

## ⚙️ Teknologi & Tools yang Digunakan

| Tool               | Fungsi                                  |
| ------------------ | --------------------------------------- |
| **GitHub Actions** | Menjalankan workflow CI secara otomatis |
| **Node.js**        | Runtime aplikasi                        |
| **ESLint v9**      | Pemeriksaan kualitas kode               |
| **Jest**           | Unit testing                            |

---

## 🚀 Workflow CI

Workflow ini berjalan otomatis saat ada kode yang di-*push* ke branch `main`.
Tahapan workflow:

1. Checkout repository
2. Setup Node.js versi 18
3. Install dependencies
4. Fix permission ESLint & Jest
5. Jalankan linting
6. Jalankan unit test

Berikut lokasi file pipeline:

```
.github/workflows/ci.yml
```

---

## 📄 Isi file Workflow CI

```yml
name: Simple CI Pipeline

on:
  push:
    branches: ["main"]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: "18"

      - name: Install dependencies
        run: npm install

      - name: Fix ESLint permission
        run: chmod +x node_modules/.bin/eslint

      - name: Fix Jest permission
        run: chmod +x node_modules/.bin/jest

      - name: Run Linter
        run: npm run lint

      - name: Run Unit Tests
        run: npm test
```

---

## 🧪 Testing

Perintah untuk menjalankan unit test secara lokal:

```
npm test
```

Contoh file test (sample):

```js
test("sample test", () => {
  expect(1 + 1).toBe(2);
});
```

---

## 🧹 Linting

Linting menggunakan ESLint v9 dengan konfigurasi file:

```
eslint.config.js
```

Isi configurasi:

```js
const js = require("@eslint/js");

module.exports = [
  {
    languageOptions: {
      globals: {
        require: "readonly",
        module: "readonly",
        test: "readonly",
        expect: "readonly"
      }
    }
  },
  js.configs.recommended
];
```

---

## 🟢 Status CI Pipeline

Tambahkan badge status pipeline:

```
![CI Status](https://github.com/AuuAhMales/ci-tbp-kelompok/actions/workflows/ci.yml/badge.svg)
```

---

## ✔️ Kesimpulan

Proyek ini berhasil mengimplementasikan CI menggunakan GitHub Actions yang meliputi linting otomatis, unit testing, serta validasi kode setiap push. Workflow berjalan stabil dan memastikan kualitas kode tetap terjaga.

---

