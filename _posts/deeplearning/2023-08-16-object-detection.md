---
title: "오브젝트 디텍션 개념 (수정중)"
excerpt: "간단하게 컨셉만 알아보자."

date: 2023-08-16 10:27:00 +0900
# last_modified_at: 2022-02-06

author_profile: false # 왼쪽부분 프로필을 띄울건지

header:
overlay_image: https://learn.g2.com/hubfs/G2CM_FI264_Learn_Article_Images_%5BObject_detection%5D_V1a.png
overlay_filter: 0.5 # 투명도

# teaser: /assets/images/my-awesome-post-teaser.jpg

categories:
  - deeplearning

# tags: - test - theme

# table of contents

toc: false # 오른쪽 부분에 목차를 자동 생성해준다.
toc_sticky: false
toc_label: "table of content" # toc 이름 설정
toc_icon: "bars" # 아이콘 설정
---

- NMS non maxium supression
  - 박스를 정렬하고 가장 높은 확률을 선택
  - 임계값을 넘는 상자는 제거
  - iou 계산
- iou 전체 나누기 겹치는 부분, 겹치는 정도
- 정확도와 재현율은 오브젝트 디텍션 메트릭 많이 사용된다.
  - 정확도가 높은 경우 추측이 너무 중하다.
  - 재현율이 높은 경우 추측을 쉽게 해서 상자가 많다.
- AP average precision 평균 정밀도
  - 0과 1사이로 단일 클래스에 대한 성능 정보 제공
- mAP 여러개 클래스로 구성된 클래스에 대해서 각각의 AP에 대한 평균
  - 혼동행렬을 보고 못찾는 특정 클래스를 확인해야 한다.
- mAP@0.5 정답과 예측의 iou가 50프로 이상일 떄 정답으로 판정
- 2 stage detector
  - 위치를 찾고 분류를 한다 r-cnn
  - 정확도는 상대적으로 높지만 검출속도가 늦다
- 1 stage detector
  - 물체의 위치와 분류를 한번에 처리 yolo
  - 속도를 빠르지만 정확도는 느리다
- classfication + localization
- sliding window
  - 여러 사이즈의 박스를 만들고 하나하나 움직이면서 박스 영역 안에 있는 오브젝트에 대해서 cnn를 돌린다. 확률이 높은 오브젝트를 기록해서 가장 높은 오브젝트를 추출.
- region proposal
  - 오브젝트가 있을 법한 지역을 탐색해서 cnn으로 탐지
  - r-cnn은 2000개의 박스를 cnn으로 탐지
  - 비교적 빠른 속도
- r-cnn regions with cnn
  - selective search로 2000개 박스 이용
  - roi를 warp시켜 cnn 적용
  - 전형적인 rcnn은 투스테이지 방식
- fast r-cnn
  - rcnn이 독립적으로 추론하는 문제를 해결했다.
  - 이미지를 cnn에 넣고 피처맵에 대해서 region proposal 시행
- yolo
  - region proposal은 속도가 너무 느림.
  - 이미지에 그리드를 그려 박스로 나누고 박스에 대해 cnn
- ssd
  - 싱글샷 디텍터
  - 예전 욜로는 작은 오브젝트는 찾기 어려웠다.
  - 욜로보다는 느리지만 정확도가 높다.
