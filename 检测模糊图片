#!/usr/bin/env python
# coding:utf-8
import os

import cv2
img_path = input('img_path:')
crop_dir = input('crop_dir:')
threshold = int(input('threshold:'))
blur_img=[]

def detect_blur():
    for file in os.listdir(img_path):
        domain = os.path.abspath(img_path)
        pic_path = os.path.join(domain, file)
        image = cv2.imread(pic_path)
        img2gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
        imageVar = cv2.Laplacian(img2gray, cv2.CV_64F).var()
        pic_name = pic_path[len(img_path)+1:-4]
        print(imageVar)
        if imageVar<threshold:
            print('模糊图片:'+pic_name)
            blur_img.append(pic_name)
            savepicture(image, crop_dir, str(pic_name) + ".jpg")
        else:print('正常图片')

def savepicture(img, path, name):
        cv2.imwrite(path + name, img)

detect_blur()
