# Median Filtering

1. import cv2

2. import numpy as np

3. from matplotlib import pyplot as plt

pada line 1,2 dan 3 untuk Mengimpor library yang diperlukan: OpenCV untuk pemrosesan gambar, NumPy untuk operasi array, dan Matplotlib untuk menampilkan gambar.

4. image = cv2.imread('Pawai SMP.jpg')

pada line 4 untuk Membaca gambar dari file dengan path yang diberikan. Gambar dibaca dalam mode warna (BGR).

5. image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

pada line 5 ini untuk Mengkonversi gambar dari BGR (format default OpenCV) ke RGB (format yang digunakan oleh Matplotlib).

6. image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

pada line 6 ini untuk Mengkonversi gambar dari BGR ke grayscale untuk keperluan median filtering.

7. median_filtered = cv2.medianBlur(image_gray, 5)

lalu pada line 7 berfungsi untuk Menerapkan median filtering dengan kernel 5x5 pada gambar grayscale. Filter median menggantikan nilai piksel dengan median dari nilai nilai piksel di sekitarnya, yang membantu mengurangi noise.

8. plt.figure(figsize=(10, 5))

9. plt.subplot(1, 2, 1)

10. plt.title('Original Image')
  
11. plt.imshow(image_rgb)

12. plt.subplot(1, 2, 2)

13. plt.title('Median Filtered Image (Grayscale)')

14. plt.imshow(median_filtered, cmap='gray')

15. plt.show()

untuk line 8,9,10,11,12,13,14,15 digunakan untuk Menampilkan gambar asli berwarna dan hasil median filtering dalam mode grayscale menggunakan Matplotlib.

# ------------------------------------------------------------------------------

# Mean Filtering

1. import cv2

2. import numpy as np

3. from matplotlib import pyplot as plt

pada line 1,2,3 digunakan untuk Mengimpor library yang diperlukan: OpenCV untuk pemrosesan gambar, NumPy untuk operasi array, dan Matplotlib untuk menampilkan gambar.

7. def mean_filtering(image, kernel_size):

  #Padding gambar
  
8. pad_size = kernel_size // 2
  
9. padded_image = np.pad(image, pad_size, mode='constant', constant_values=0)

  #Inisialisasi hasil filter
  
10. mean_filtered = np.zeros_like(image)

  #Iterasi hasil filter
  
11. for i in range(image.shape[0]):
  
12. for j in range(image.shape[1]):

  #Ekstrasi neighborhood
  
13. neighborhood = padded_image[i:i+kernel_size, j:j+kernel_size]

  #Rata rata nilai piksel
  
14. mean_filtered [i, j] = np.mean(neighborhood)

15. return mean_filtered

pada line 7,8,9,10,11,12,13,14,15 ini merupakan fungsi dari mean filtering yang mana :

- Padding Gambar: Menambahkan padding pada gambar untuk menghindari masalah di tepi gambar.

- Inisialisasi Hasil Filter: Membuat array kosong untuk hasil filter.

- Iterasi Setiap Piksel: Mengiterasi setiap piksel dalam gambar asli

- Ekstraksi Neighborhood: Mengambil neighborhood dari setiap piksel.

- Rata-rata Nilai Piksel: Menghitung rata-rata nilai dari neighborhood dan menetapkannya ke piksel hasil.

16. image = cv2.imread('Pawai SMP.jpg', cv2.IMREAD_GRAYSCALE)

line 16 untuk Membaca gambar dalam mode grayscale.

17. mean_filtered = mean_filtering(image, 5)

line 17 untuk Menerapkan mean filtering dengan kernel 5x5.

18. plt.figure(figsize=(10, 5))

19. plt.subplot(1, 2, 1)

20. plt.title('Original Image')

21. plt.imshow(image, cmap='gray')

22. plt.subplot(1, 2, 2)

23. plt.title('Mean Filtered Image')

24. plt.imshow(mean_filtered, cmap='gray')

25. plt.show()

Untuk line 18,19,20,21,22,23,24,25 untuk Menampilkan gambar asli dalam mode grayscale dan hasil mean filtering menggunakan Matplotlib.
