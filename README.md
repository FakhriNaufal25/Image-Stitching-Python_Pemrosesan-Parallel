## Image-Stitching-Python
# Panduan Cara Image Stitching Menggunakan Python dan OpenCV
Image Stitching adalah proses menggabungkan beberapa gambar menjadi satu gambar panorama yang lebih besar. Hal ini dilakukan dengan mencocokkan dan menyatukan bagian-bagian gambar yang tumpang tindih atau saling berdekatan. Teknik ini umumnya digunakan dalam fotografi panorama untuk mencakup sudut pandang yang lebih luas.

## Daftar Isi
   - [Tools Requirements](#Tools-Requirements)
   - [Input Image](#Input-Image)
   - [Condingan Python](#Condingan-Python)
   - [Execute the code](#Execute-the-code)

## Tools Requirements
Sebelumnya itu pastikan update terlbih dahulu Operating System anda dengan cara `sudo apt update`. 
Berikut Tools yang perlu diinstal terlebih dahulu sebelum, menjalankan Image Stitching

    pip3 install numpy

Jika sudah lanjut ke tools yang kedua, dengan perintah berikut

    pip3 opencv-python

OpenCV memiliki fungsi untuk melakukan penyesuaian geometri,menemukan titik kunci pada gambar yang dapat digunakan dalam proses pencocokan antar gambar.

    pip3 install imutils

## Input Image

   <div align="center">
     <div style="display:flex; flex-wrap:wrap;">
       <img src=>
       <img src=>
       <img src=>
       <img src=>
     </div>
   </div>


