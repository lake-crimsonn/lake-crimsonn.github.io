---
title: "OpenCV로 문서 반듯하게 펴기"
excerpt: "다리미가 아닙니다. OpenCV입니다."

date: 2023-08-12 09:38:00 +0900
# last_modified_at: 2022-02-06

author_profile: false # 왼쪽부분 프로필을 띄울건지

header:
# overlay_image: https://images.unsplash.com/photo-1501785888041-af3ef285b470?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80
# overlay_filter: 0.5 # 투명도

# teaser: /assets/images/my-awesome-post-teaser.jpg

categories:
  - python-skills

# tags: - test - theme

# table of contents

toc: false # 오른쪽 부분에 목차를 자동 생성해준다.
toc_sticky: false
toc_label: "table of content" # toc 이름 설정
toc_icon: "bars" # 아이콘 설정
---

<figure align="center">
<a href="https://ibb.co/f8dyKSY"><img src="https://i.ibb.co/ZHzFwJ6/business-card-640.jpg" alt="business-card-640" border="0" width="50%" height="50%"></a>
<a href="https://ibb.co/cr8PDxt"><img src="https://i.ibb.co/G5MXcFk/card-fixed.png" alt="card-fixed" border="0" width="47%" height="50%"></a>
<figcaption align="center">화질은 떨어집니다</figcaption>
</figure>

```python
import cv2
import numpy as np
# from google.colab.patches import cv2_imshow  # 코랩에서 돌리는 경우

src = cv2.imread('_data/images/business-card_640.jpg')
print('카드 사이즈:', src.shape)

# 카드 사이즈 변환해주기
w, h = 720, 480
srcQuad = np.array([[160, 207],[395, 112],[487, 221],[239, 327]], np.float32)  # 그림판으로 찍어본 현재 좌표값
dstQuad = np.array([[0, 0], [w-1, 0], [w-1, h-1], [0, h-1]], np.float32)  # 이동하는 곳의 좌표값

pers = cv2.getPerspectiveTransform(srcQuad, dstQuad)  # 원근변환

dst = cv2.warpPerspective(src, pers, (w, h))  # 적용
cv2_imshow("img", dst)
cv2.waitKey()
cv2.destroyAllWindows()
```
