import cv2
from matplotlib import pyplot as plt

#读取测试图片
im = cv2.imread("C:\\Users\\Administrator.X36KKQ2UTQSEZ5O\\Desktop\\ai_challenger_keypoint\\ai_challenger_keypoint_train_20170909\\keypoint_train_images_20170902\\000000328757.jpg")

x,y,w,h=40.65, 38.8, 418.38, 601.2

xmin = x
xmax = x + w
ymin = y
ymax = y + h

# xmin,ymin,xmax,ymax=188.24, 158.15, 314.25, 189.78

cv2.rectangle(im,(int(xmin),int(ymin)),(int(xmax),int(ymax)),(0,255,255),2)

plt.imshow(im,'brg')
plt.show()
