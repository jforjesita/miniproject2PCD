# ANALISIS HASIL PENGUJIAN 9 CITRA IJAZAH

[01_HighQuality_Enhanced.jpg]
Input:
01_HighQuality_Enhanced.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[02_LowContrast.jpg]
Input:
02_LowContrast.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[03_Blurred.jpg]
Input:
03_Blurred.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[04_HighNoise.jpg]
Input:
04_HighNoise.jpg

Output:
Nomor Ijazah : Tidak terbaca
Tanda Tangan : PRESENT
----------------------------------------

[05_LowResolution_Upsampled.jpg]
Input:
05_LowResolution_Upsampled.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[06_Faded_Underexposed.jpg]
Input:
06_Faded_Underexposed.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[07_ColorShift_WarmTint.jpg]
Input:
07_ColorShift_WarmTint.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[08_JPEGCompression_Artifacts.jpg]
Input:
08_JPEGCompression_Artifacts.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

[09_CombinedDegradation.jpg]
Input:
09_CombinedDegradation.jpg

Output:
Nomor Ijazah : 571012022000056
Tanda Tangan : PRESENT
----------------------------------------

Total gambar: 9

# 1. Penjelasan metode yang digunakan

a. Grayscale
Grayscale mengubah citra berwarna menjadi citra keabuan. Tujuannya menyederhanakan informasi warna sehingga pemrosesan citra dan pengenalan karakter dapat dilakukan dengan lebih mudah.

b. Image Enhancement
Image enhancement bertujuan meningkatkan kualitas citra agar nomor ijazah lebih mudah dikenali oleh OCR. Metode yang dapat dibandingkan adalah:

Mean Filter: mengurangi noise dengan menghitung rata-rata nilai piksel di sekitarnya, tetapi dapat membuat karakter menjadi lebih kabur.
Median Filter: mengurangi noise, khususnya salt-and-pepper noise, dengan mengambil nilai median dari piksel di sekitarnya.
Gaussian Filter: menghaluskan citra untuk mengurangi noise, tetapi dapat menghilangkan detail karakter yang kecil.
Sharpening: mempertajam tepi karakter sehingga bentuk huruf dan angka berpotensi menjadi lebih jelas.
CLAHE: meningkatkan kontras lokal agar karakter lebih terlihat dibandingkan latar belakang. Metode ini cocok untuk citra ijazah yang memiliki kontras rendah atau pencahayaan tidak merata.

c. Optical Character Recognition (OCR)
OCR menggunakan Tesseract untuk mengenali karakter pada area nomor ijazah yang telah dipotong dan ditingkatkan kualitasnya. Hasil OCR kemudian dibandingkan dengan nomor ijazah yang sebenarnya.

d. Deteksi tanda tangan
Area tanda tangan diproses menggunakan thresholding untuk memisahkan tinta dari latar belakang. Selanjutnya, morphology digunakan untuk mengurangi noise kecil. Jumlah dan rasio piksel tinta dianalisis untuk menentukan apakah terdapat indikasi tanda tangan (PRESENT) atau tidak terdeteksi (NOT DETECTED).

# 2 Menentukan enhancement terbaik berdasarkan CER
Berdasarkan hasil OCR, metode enhancement yang paling efektif adalah 01_HighQuality_Enhanced, 02_LowContrast, 03_Blurred, 05_LowResolution_Upsampled, 06_Faded_Underexposed, 07_ColorShift_WarmTint, 08_JPEGCompression_Artifacts, dan 09_CombinedDegradation, karena berhasil membaca nomor ijazah dengan benar sehingga memiliki nilai CER sebesar 0% untuk bagian nomor ijazah. Sementara itu, metode 04_HighNoise merupakan metode yang paling tidak efektif karena nomor ijazah tidak terbaca. Dengan demikian, delapan metode tersebut menunjukkan kinerja OCR yang sama baik berdasarkan CER, sehingga diperlukan indikator tambahan untuk menentukan metode yang paling unggul secara keseluruhan.
