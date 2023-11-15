# jhs

# 각 필요 요소 import
---------------------
import cv2
import numpy as np
from matplotlib import pyplot as plt

# Chosun.jpg 라는 이미지 파일을 불러오기
---------------------------------------
image = cv2.imread('Chosun.jpg') 
image_gray = cv2.imread('Chosun.jpg', cv2.IMREAD_GRAYSCALE)

# Chosun.jpg 띄우기
-------------------
b,g,r = cv2.split(image)
image2 = cv2.merge([r,g,b]) 
plt.imshow(image2)
plt.xticks([])
plt.yticks([])
plt.show()

# 블러 처리를 통한 외곽찾기
--------------------------
blur = cv2.GaussianBlur(image_gray, ksize=(5,5), sigmaX=0)
ret, thresh1 = cv2.threshold(blur, 127, 255, cv2.THRESH_BINARY)

# Canny() 를 사용한 외곽코드
---------------------------
# 이미지의 엣지만 돌려주는 Canny() 함수를 사용
edged = cv2.Canny(blur, 10, 250)
cv2.imshow('Edged', edged)
cv2.waitKey(0)
