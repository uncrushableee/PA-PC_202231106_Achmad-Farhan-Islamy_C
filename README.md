# Project UAS

Nama: Achmad Farhan Islamy 

nim : 202231106

untuk membuat project ini kita perlu mengimport gambar dengan cara:

import cv2
import numpy as np
from matplotlib import pyplot as plt

penjelasan:
- OpenCV (cv2): Pustaka yang kuat untuk pemrosesan gambar secara real-time.
- NumPy (np): Pustaka fundamental untuk komputasi ilmiah yang menyediakan array dan fungsi matematika untuk keperluan pemrosesan gambar.
- Matplotlib (plt): Pustaka populer untuk membuat visualisasi seperti plot dan gambar di Python.

image_path = 'foto.jpeg'

penjelasan:
- mendefinisikan path atau lokasi gambar yang akan diproses.

image = cv2.imread(image_path)

penjelasan:
- membaca gambar dari path tersebut menggunakan openCV lalu menyimpan gambar tersebut didalam "image".

if image is None:;
    print("Gambar tidak dapat ditemukan:", image_path);
else:
    image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) # Mengkonversikan foto ke RGB
    gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) # Mengkonversikan foto ke skala Abu abu
    edges = cv2.Canny(gray_image, 100, 200) # Menerakan deteksi tepi canny
    contours, _ = cv2.findContours(edges, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE) # Menemukan kontur
    image_contours = image_rgb.copy() # Menyalin gambar asli untuk menggambar kontur
    cv2.drawContours(image_contours, contours, -1, (0, 255, 0), 3)

penjelasan:
- line 1 mengecek apakah gambar berhasil dibaca. jika tidak maka 'image' bernilai 'none', maka gambar tidak dapat ditemukan dan pesan kesalahan dicetak.
- jika ditemukan maka:
- - image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB): Mengonversi gambar dari format BGR (default OpenCV) ke RGB.
  - gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY): Mengonversi gambar ke skala abu-abu.
  - edges = cv2.Canny(gray_image, 100, 200): Menerapkan deteksi tepi Canny pada gambar skala abu-abu.
  - contours, _ = cv2.findContours(edges, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE): Menemukan kontur dalam gambar menggunakan hasil deteksi tepi.
  - image_contours = image_rgb.copy(): Membuat salinan dari gambar asli untuk menggambar kontur.
  - cv2.drawContours(image_contours, contours, -1, (0, 255, 0), 3): Menggambar semua kontur pada gambar salinan dengan warna hijau.

plt.figure(figsize=(15, 10)) # OUTPUT PERTAMA
plt.subplot(2, 3, 1)
plt.imshow(image_rgb)
plt.title('Original Image')
plt.axis('off')
plt.subplot(2, 3, 2)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')

penjelasan: 
- plt.figure(figsize=(15, 10)): Membuat sebuah figure dengan ukuran 15x10 inci.
Membuat subplot pertama dan kedua:
- plt.subplot(2, 3, 1): Subplot pertama dari grid 2x3.
- plt.imshow(image_rgb): Menampilkan gambar asli dalam format RGB.
- plt.title('Original Image'): Memberi judul "Original Image".
- plt.axis('off'): Menghilangkan sumbu dari plot.
- plt.subplot(2, 3, 2): Subplot kedua dari grid 2x3.
- plt.imshow(edges, cmap='gray'): Menampilkan hasil deteksi tepi Canny dalam skala abu-abu.
- plt.title('Canny Edge Detection'): Memberi judul "Canny Edge Detection".
- plt.axis('off'): Menghilangkan sumbu dari plot.


plt.subplot(2, 3, 4) # OUTPUT KEDUA
plt.imshow(image_rgb)
plt.title('Original Image')
plt.axis('off')

plt.subplot(2, 3, 5)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')

plt.subplot(2, 3, 6)
plt.imshow(image_contours)
plt.title('Contours Detection')
plt.axis('off')

plt.show()


penjelasan:
- Membuat subplot keempat, kelima, dan keenam:
- plt.subplot(2, 3, 4): Subplot keempat dari grid 2x3.
- plt.imshow(image_rgb): Menampilkan gambar asli dalam format RGB.
- plt.title('Original Image'): Memberi judul "Original Image".
- plt.axis('off'): Menghilangkan sumbu dari plot.
- plt.subplot(2, 3, 5): Subplot kelima dari grid 2x3.
- plt.imshow(edges, cmap='gray'): Menampilkan hasil deteksi tepi Canny dalam skala abu-abu.
- plt.title('Canny Edge Detection'): Memberi judul "Canny Edge Detection".
- plt.axis('off'): Menghilangkan sumbu dari plot.
- plt.subplot(2, 3, 6): Subplot keenam dari grid 2x3.
- plt.imshow(image_contours): Menampilkan gambar dengan kontur yang digambar.
- plt.title('Contours Detection'): Memberi judul "Contours Detection".
- plt.axis('off'): Menghilangkan sumbu dari plot.
- plt.show(): Menampilkan semua plot dalam figure.

