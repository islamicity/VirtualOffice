Berikut adalah panduan langkah demi langkah untuk membangun workflow di GitHub:

**1. Memahami Konsep Workflow**

Workflow di GitHub adalah proses otomatisasi yang dapat dipicu oleh peristiwa tertentu dalam repositori Anda, seperti push, pull request, atau event lainnya. Workflow terdiri dari satu atau lebih jobs, yang berisi serangkaian langkah (steps) yang akan dieksekusi. Langkah-langkah ini dapat berupa perintah shell, tindakan yang telah ditentukan sebelumnya (actions), atau kombinasi keduanya.

**2. Membuat File Workflow**

* Buat direktori `.github/workflows` di root repositori Anda.
* Di dalam direktori tersebut, buat file YAML baru. Nama file bisa apa saja, tetapi biasanya menggunakan format `[nama-workflow].yml`. Contoh: `build.yml`.

**3. Menulis File Workflow (YAML)**

Struktur dasar file workflow YAML:

```yaml
name: Nama Workflow Anda

on:
  push:
    branches:
      - main  # Cabang yang akan memicu workflow
  pull_request:
    branches:
      - main

jobs:
  nama-job:
    runs-on: ubuntu-latest  # Sistem operasi untuk menjalankan job
    steps:
      - name: Langkah 1
        uses: actions/checkout@v3  # Contoh action untuk checkout kode
      - name: Langkah 2
        run: npm install  # Contoh perintah shell
      - name: Langkah 3
        run: npm test
```

* **name:** Nama workflow Anda.
* **on:** Event yang memicu workflow (misalnya, push ke cabang `main`).
* **jobs:** Satu atau lebih job yang akan dijalankan.
* **runs-on:** Sistem operasi untuk menjalankan job (misalnya, `ubuntu-latest`).
* **steps:** Daftar langkah-langkah yang akan dieksekusi dalam job.

**4. Menggunakan Actions**

Actions adalah unit terkecil dari otomatisasi yang dapat digunakan kembali. Anda dapat menemukan actions yang dibuat oleh komunitas di GitHub Marketplace atau membuat actions Anda sendiri. Contoh penggunaan action:

```yaml
- name: Checkout repository
  uses: actions/checkout@v3
```

**5. Menjalankan Workflow**

Setelah Anda membuat dan menyimpan file workflow, GitHub akan secara otomatis menjalankan workflow sesuai dengan event yang Anda tentukan. Anda dapat melihat status dan log eksekusi workflow di tab **Actions** pada repositori Anda.

**Contoh Workflow Sederhana (Node.js)**

```yaml
name: Node.js CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [16.x]

    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'
      - run: npm ci
      - run: npm run build --if-present
      - run: npm test
```

**Tips:**

* Pelajari dokumentasi GitHub Actions untuk memahami lebih lanjut tentang fitur-fitur yang tersedia.
* Gunakan actions yang sudah ada untuk menghemat waktu dan tenaga.
* Uji workflow Anda secara teratur untuk memastikannya berfungsi dengan baik.

Semoga panduan ini membantu Anda membangun workflow yang efektif di GitHub!
