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
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114126.jpg">
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114129.jpg">
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114132.jpg">
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114134.jpg">
     </div>
   </div>

## Condingan Python
Buatlah codingan image stitching pyhton dengan OpenCV

    ```py
    from imutils import paths
    import numpy as np
    import argparse
    import imutils
    import cv2

    ap = argparse.ArgumentParser()
    ap.add_argument("-i", "--images", type=str, required=True,
            help="path to input directory of images to stitch")
    ap.add_argument("-o", "--output", type=str, required=True,
            help="path to the output image")
    args = vars(ap.parse_args())

    print("[INFO] loading images...")
    imagePaths = sorted(list(paths.list_images(args["images"])))
    images = []

    for imagePath in imagePaths:
            image = cv2.imread(imagePath)
            images.append(image)

    print("[INFO] stitching images...")
    stitcher = cv2.createStitcher() if imutils.is_cv3() else cv2.Stitcher_create()
    (status, stitched) = stitcher.stitch(images)


    if status == 0:
            cv2.imwrite(args["output"], stitched)
            print("[INFO] Image stitched and saved to {}".format(args["output"]))

    else:
            print("[INFO] image stitching failed ({})".format(status))
    ```

