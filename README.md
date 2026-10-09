# miniproject2PCD
# Prototipe OCR Nomor Ijazah dan Deteksi Tanda Tangan

# 1. Deskripsi Program

Program ini dibuat untuk mengolah citra dokumen ijazah menggunakan teknik *Image Processing* dan *Optical Character Recognition* (OCR). Program bertujuan untuk membaca nomor ijazah secara otomatis dan mendeteksi keberadaan tanda tangan pada citra dokumen.

Tahapan yang dilakukan meliputi pemuatan citra, prapemrosesan gambar, pemotongan area nomor ijazah dan tanda tangan (*Region of Interest* atau ROI), pembacaan teks menggunakan Tesseract OCR, serta pemeriksaan keberadaan tanda tangan.

# 2. Persiapan Sebelum Menjalankan Program

Pastikan perangkat lunak dan pustaka berikut telah tersedia:

* Python.
* Visual Studio Code dengan ekstensi Python dan Jupyter.
* OpenCV untuk pemrosesan citra.
* Pytesseract sebagai penghubung Python dengan Tesseract OCR.
* NumPy untuk pengolahan array citra.
* Matplotlib untuk menampilkan gambar.

Instal pustaka Python melalui terminal VS Code jika belum tersedia:

```python
pip install opencv-python pytesseract numpy matplotlib
```

Tesseract OCR juga harus sudah terinstal di komputer. Pastikan program dapat menemukan lokasi instalasi Tesseract sebelum menjalankan tahap OCR.

# 3. Menyiapkan File Citra

Letakkan seluruh gambar ijazah yang akan diuji di folder yang sama dengan notebook Jupyter. Format gambar yang dapat digunakan antara lain JPG, JPEG, PNG, BMP, dan TIFF.

Program akan membaca gambar berdasarkan ekstensi file yang telah ditentukan. Pastikan nama file benar dan gambar dapat dibuka.

# 4. Menjalankan Kode Secara Berurutan

Jalankan setiap cell dari atas ke bawah menggunakan tombol **Run Cell** atau kombinasi tombol `Shift + Enter`.

# Tahap 1 — Import Library dan Membaca Daftar Gambar

Tahap ini mengimpor pustaka yang dibutuhkan, mencari file gambar di folder kerja, dan menyiapkan struktur penyimpanan hasil pemrosesan setiap gambar.

# Tahap 2 — Prapemrosesan Citra

Pada tahap ini, gambar dibaca menggunakan OpenCV, disesuaikan orientasinya apabila diperlukan, diubah menjadi citra grayscale, dan ditingkatkan kontrasnya menggunakan CLAHE.

Prapemrosesan bertujuan membantu memperjelas karakter dan area dokumen sebelum dilakukan OCR. Pastikan orientasi gambar sudah benar dan tidak melakukan rotasi tambahan yang tidak diperlukan.

# Tahap 3 — Menentukan Area ROI

ROI merupakan bagian tertentu dari gambar yang menjadi fokus analisis. Pada program ini, ROI digunakan untuk menentukan area nomor ijazah dan area tanda tangan.

Koordinat ROI perlu disesuaikan dengan posisi objek pada gambar. Tampilkan hasil crop terlebih dahulu untuk memastikan area nomor ijazah tidak terpotong dan area tanda tangan sudah tercakup.

# Tahap 4 — Membaca Nomor Ijazah dengan OCR

Gambar pada area nomor ijazah diperbesar dan diproses sebelum dikirim ke Tesseract OCR. Hasil OCR kemudian disaring untuk memperoleh rangkaian angka yang diduga merupakan nomor ijazah.

Hasil pembacaan harus diperiksa kembali karena OCR dapat salah mengenali karakter, melewatkan angka, atau membaca teks lain di sekitar nomor ijazah.

# Tahap 5 — Mendeteksi Tanda Tangan

Program memeriksa area tanda tangan untuk menentukan apakah terdapat indikasi tanda tangan berdasarkan metode deteksi yang digunakan.

Status `PRESENT` menunjukkan bahwa program mendeteksi indikasi tanda tangan pada area tersebut. Status ini tidak menjamin bahwa tanda tangan benar-benar autentik atau milik orang yang berwenang.

# Tahap 6 — Menampilkan Hasil

Tahap terakhir menampilkan nama file, hasil pembacaan nomor ijazah, status deteksi tanda tangan, dan jumlah gambar yang telah diproses.

Bandingkan hasil dari setiap gambar untuk mengetahui apakah metode prapemrosesan dan penentuan ROI sudah bekerja dengan baik.

# 5. Cara Menjalankan Ulang Program

Jika terdapat perubahan pada kode prapemrosesan atau koordinat ROI, jalankan ulang cell secara berurutan mulai dari tahap prapemrosesan, penentuan ROI, OCR, hingga penampilan hasil.

Hal ini penting agar hasil yang ditampilkan berasal dari citra dan koordinat terbaru, bukan dari hasil pemrosesan sebelumnya.

# 6. Evaluasi Hasil

Evaluasi dilakukan dengan memeriksa apakah nomor ijazah terbaca lengkap dan sesuai dengan nomor sebenarnya pada dokumen. Untuk mengukur kinerja OCR secara kuantitatif, hasil pembacaan dapat dibandingkan dengan teks acuan (*ground truth*) menggunakan Character Error Rate (CER).

Semakin kecil nilai CER, semakin sedikit kesalahan karakter yang dihasilkan OCR. Sementara itu, hasil deteksi tanda tangan perlu dibandingkan dengan kondisi gambar sebenarnya untuk mengetahui apakah sistem menghasilkan deteksi yang sesuai.
