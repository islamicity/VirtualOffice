Baik, mari kita bedah langkah demi langkah workflow GitHub Actions dengan nama `CI` yang Anda berikan:

**Penjelasan Workflow**

Workflow ini adalah contoh paling dasar bagaimana menjalankan serangkaian perintah otomatis saat ada perubahan (push) pada kode di repositori GitHub Anda. Tujuan utamanya adalah memberikan gambaran awal tentang cara kerja GitHub Actions, bukan untuk membangun atau mendeploy proyek secara nyata.

**Langkah-demi-Langkah**

1. **`name: CI`:**
   - Ini adalah nama workflow yang akan muncul di tab "Actions" di repositori GitHub Anda.

2. **`on: [push]`:**
   - Ini adalah event trigger yang akan menjalankan workflow. Dalam hal ini, workflow akan dipicu setiap kali ada push (perubahan kode yang dikirim) ke repositori.

3. **`jobs:`**
   - Bagian ini mendefinisikan pekerjaan (job) yang akan dilakukan dalam workflow. Dalam contoh ini, hanya ada satu job dengan nama `build`.

4. **`build:`**
   - Nama dari job yang akan dijalankan.

5. **`runs-on: ubuntu-latest`:**
   - Job ini akan dieksekusi di dalam sebuah runner (lingkungan virtual) yang berjalan di sistem operasi Ubuntu versi terbaru.

6. **`steps:`**
   - Ini adalah bagian inti dari job, yang berisi daftar langkah-langkah (step) yang akan dijalankan secara berurutan.

7. **`- uses: actions/checkout@v1`:**
   - Ini adalah langkah pertama yang menggunakan action `checkout` dari GitHub. Action ini akan mengunduh kode dari repositori Anda ke dalam runner, sehingga langkah-langkah selanjutnya bisa mengakses dan memanipulasi kode tersebut.

8. **`- name: Run a one-line script`:**
   - Ini adalah nama dari langkah kedua. Anda bisa memberikan nama yang lebih deskriptif sesuai dengan tujuan langkah tersebut.

9. **`run: echo Hello, world!`:**
   - Ini adalah perintah yang akan dijalankan di dalam runner. Perintah ini sangat sederhana, hanya mencetak teks "Hello, world!" ke konsol.

10. **`- name: Run a multi-line script`:**
    - Nama dari langkah ketiga, yang akan menjalankan skrip dengan beberapa baris.

11. **`run: |`:**
    - Tanda `|` digunakan untuk menunjukkan bahwa perintah berikutnya akan ditulis dalam beberapa baris.

12. **`echo Add other actions to build,`**
    - Baris pertama dari skrip multi-baris, mencetak teks "Add other actions to build," ke konsol.

13. **`echo test, and deploy your project.`**
    - Baris kedua dari skrip multi-baris, mencetak teks "test, and deploy your project." ke konsol.

**Hasil Akhir**

Ketika workflow ini dijalankan, Anda akan melihat output seperti ini di tab "Actions" di repositori GitHub Anda:

```
Run echo Hello, world!
Hello, world!
Run echo Add other actions to build,
Add other actions to build,
echo test, and deploy your project.
test, and deploy your project.
```

**Catatan Penting:**

* Contoh workflow ini hanya untuk demonstrasi. Untuk membangun dan mendeploy proyek secara nyata, Anda perlu menambahkan langkah-langkah yang relevan, seperti menginstal dependensi, menjalankan tes, dan mengirimkan artefak ke lingkungan produksi.
* Workflow GitHub Actions dapat dikonfigurasi dengan sangat fleksibel untuk memenuhi kebutuhan otomatisasi proyek Anda.
