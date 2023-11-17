## Image-Stitching-Python
# Panduan Cara Image Stitching Menggunakan Python dan OpenCV
Image Stitching adalah proses menggabungkan beberapa gambar menjadi satu gambar panorama yang lebih besar. Hal ini dilakukan dengan mencocokkan dan menyatukan bagian-bagian gambar yang tumpang tindih atau saling berdekatan. Teknik ini umumnya digunakan dalam fotografi panorama untuk mencakup sudut pandang yang lebih luas.

## Daftar Isi
   - [Tools Requirements](#Tools-Requirements)
   - [Input Image](#Input-Image)
   - [Condingan Python](#Condingan-Python)
   - [Execute the code](#Execute-the-code)
   - [Output](#Output)

## Tools Requirements
Sebelumnya itu pastikan update terlbih dahulu Operating System anda dengan cara `sudo apt update`. 
Berikut Tools yang perlu diinstal terlebih dahulu sebelum, menjalankan Image Stitching

    pip3 install numpy

Jika sudah lanjut ke tools yang kedua, dengan perintah berikut

    pip3 install opencv-python

OpenCV memiliki fungsi untuk melakukan penyesuaian geometri,menemukan titik kunci pada gambar yang dapat digunakan dalam proses pencocokan antar gambar.

    pip3 install imutils

## Input Image

   <div align="center">
     <div style="display:flex; flex-wrap:wrap;">
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114126.jpg" alt="1" width="200"/>
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114129.jpg" alt="1" width="200"/>
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114132.jpg" alt="1" width="200"/>
       <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image-input/image1/IMG_20231116_114134.jpg" alt="1" width="200"/>
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
## Execute the code
Step selanjutnya jalankan kodingan pythonya

    python3 <image stitching file> --images <images input direcotry> --output <image output directory>/<output name.png>
    
Contohnya

    python3 image_stitching.py --images image-input/image1 --output image-output/image1/output.png
    
Jika berhasil akan menghasilkan command seperti ini

 ```
    [INFO] loading image...
    [INFO] stitching images...
    [INFO] Image stitched and saves to image-output/image1/output.png
```
![Output](https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/execute%20codingan.png)

## Output
Output akan menghasilkan seperti dibawah ini

<p align="center">
  <img src="https://github.com/FakhriNaufal25/Image-Stitching-Python_Pemrosesan-Parallel/blob/main/Image%20Stitching%20Python/image%20stitching%20output.png" alt="Your Image Description">
</p>
