
# PENJELASAN UAS PRAKTIKUM

# 1. **Mengimpor Pustaka yang Diperlukan**
    import numpy as np
    from PIL import Image, ImageOps
    import matplotlib.pyplot as plt

Langkah ini mengimpor pustaka yang diperlukan untuk manipulasi gambar dan visualisasi. `numpy` untuk operasi numerik (tidak digunakan dalam kode ini), `PIL` (Python Imaging Library) untuk memanipulasi gambar, dan `matplotlib` untuk menampilkan gambar.

# 2. **Memuat Gambar**
    image_path = 'me.jfif'  # Ganti ini dengan jalur   file foto Anda jika berbeda
    original_image = Image.open(image_path)
    
Pada tahap ini, gambar dimuat dari jalur file yang ditentukan dan disimpan dalam variabel `original_image`.

# 3. **Rotasi Gambar**
    rotated_image = original_image.rotate(45)
  
  Gambar asli dirotasi sebesar 45 derajat dan hasilnya disimpan dalam `rotated_image`.

# 4. **Ubah Ukuran (Resize) Gambar**
    resized_image = original_image.resize((100, 200))  # Mengubah ukuran gambar menjadi 100x200 piksel
    
Gambar asli diubah ukurannya menjadi 100x200 piksel dan hasilnya disimpan dalam `resized_image`.

# 5. **Memotong (Crop) Gambar**
    width, height = original_image.size
    left = width / 4
    top = height / 4
    right = 3 * width / 4
    bottom = 3 * height / 4
    cropped_image = original_image.crop((left, top, right, bottom))
    
  Gambar asli dipotong sehingga hanya bagian tengahnya yang diambil. Koordinat pemotongan dihitung berdasarkan ukuran gambar asli dan hasilnya disimpan dalam `cropped_image`.

# 6. **Membalik (Flip) Gambar**
    flipped_image = ImageOps.mirror(original_image)
    
Gambar asli dibalik secara horizontal dan hasilnya disimpan dalam `flipped_image`.

# 7. **Translasi Gambar**
    translated_image = Image.new("RGB", original_image.size)
    translated_image.paste(original_image, (100, 50))
    
Gambar asli dipindahkan (ditranslasi) sebesar (100, 50) piksel dari posisi asalnya dan ditempatkan pada gambar baru dengan ukuran yang sama dengan gambar asli. Hasilnya disimpan dalam `translated_image`.

# 8. **Menampilkan Hasil Manipulasi Gambar**
    fig, axes = plt.subplots(2, 3, figsize=(15, 10))
    axes = axes.ravel()
    
`matplotlib` digunakan untuk membuat subplot 2 baris dan 3 kolom dengan ukuran total 15x10 inci. Subplot ini akan digunakan untuk menampilkan gambar-gambar yang telah dimanipulasi.

    axes[0].imshow(original_image)
    axes[0].set_title("Citra Asli")

    axes[1].imshow(rotated_image)
    axes[1].set_title("After Rotated")

    axes[2].imshow(resized_image)
    axes[2].set_title("After Resized")

    axes[3].imshow(cropped_image)
    axes[3].set_title("After Cropped")

    axes[4].imshow(flipped_image)
    axes[4].set_title("After Flipped")

    axes[5].imshow(translated_image)
    axes[5].set_title("After Translated")

Setiap subplot digunakan untuk menampilkan gambar asli dan hasil dari berbagai manipulasi gambar dengan menggunakan `imshow`. Judul ditambahkan pada masing-masing subplot untuk menjelaskan jenis manipulasi yang dilakukan.

    python
    # Menghilangkan sumbu
    for ax in axes:
        ax.axis('off')
    
  Loop ini menghilangkan sumbu pada setiap subplot agar gambar terlihat lebih jelas tanpa gangguan dari sumbu.

    python
    plt.tight_layout()
    plt.show()
    
  `tight_layout` digunakan untuk memastikan tata letak subplot tidak saling bertumpang tindih, dan `show` digunakan untuk menampilkan jendela gambar.

# 9 Teori dan Jurnal yang mendukung projek terkait


## Teori Pemrosesan Citra Digital

1. **Rotasi Gambar**:
   - **Teori**: Rotasi adalah transformasi geometrik yang memutar sebuah citra terhadap suatu titik tertentu, biasanya pusat citra. Algoritma yang sering digunakan adalah bilinear interpolation atau nearest-neighbor interpolation.
   - **Referensi**: 
     - Gonzalez, R. C., & Woods, R. E. (2008). *Digital Image Processing* (3rd Edition). Prentice-Hall, Inc.

2. **Pengubahan Ukuran (Resize)**:
   - **Teori**: Mengubah ukuran citra melibatkan skala ulang piksel citra. Algoritma umum yang digunakan termasuk nearest-neighbor interpolation, bilinear interpolation, dan bicubic interpolation.
   - **Referensi**: 
     - Burger, W., & Burge, M. J. (2016). *Digital Image Processing: An Algorithmic Introduction Using Java* (2nd Edition). Springer.

3. **Pemotongan (Cropping)**:
   - **Teori**: Pemotongan adalah proses mengambil subregion dari sebuah citra. Ini sering digunakan untuk fokus pada area tertentu dari citra.
   - **Referensi**:
     - Jain, A. K. (1989). *Fundamentals of Digital Image Processing*. Prentice-Hall, Inc.

4. **Pembalikan (Flipping)**:
   - **Teori**: Pembalikan citra adalah transformasi yang menghasilkan citra cermin. Ini dapat dilakukan secara horizontal atau vertikal.
   - **Referensi**:
     - Pratt, W. K. (2007). *Digital Image Processing: PIKS Scientific Inside* (4th Edition). John Wiley & Sons, Inc.

5. **Translasi Gambar**:
   - **Teori**: Translasi adalah pergeseran posisi citra secara horizontal dan/atau vertikal. Ini dilakukan dengan menambahkan offset pada koordinat piksel.
   - **Referensi**:
     - Sonka, M., Hlavac, V., & Boyle, R. (2014). *Image Processing, Analysis, and Machine Vision* (4th Edition). Cengage Learning.
