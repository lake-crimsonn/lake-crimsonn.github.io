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

# NMS 알고리즘 non maximum supression (수정중)

## NMS 알고리즘 non maximum supression

<figure class="half">
<img src="https://wikidocs.net/images/page/142645/NMS.png" alt="business-card-640" border="0">
</figure>

- 관측 되는 오브젝트의 스코어가 일정한 임계치 이상이면 바운딩 박스를 그려준다. 하지만 너무 많이 박스를 그려줘서 문제가 될 수 있다. 이 때 가장 신뢰도가 높은 하나의 박스만 남기고 다른 박스들은 다 지우는 알고리즘을 NMS라고 한다.
- 욜로의 NMS
  1. 측정된 컨피던스 스코어를 모두 모아 리스트에 담고 정렬한다.
  2. 컨피던스 스코어가 0.6이하인 박스는 모두 버립니다.
  3. 가장 스코어가 높은 박스와 다른 박스의 IoU를 비교합니다.
  4. IoU가 0.5 이상인 박스를 제거합니다.
  5. IoU가 낮은 박스들은 그대로 둡니다.
  6. 그 다음으로 스코어가 높은 박스를 기준으로 3번~5번 과정을 반복합니다.
- IoU는 박스들의 겹치는 정도를 말합니다. 전체 박스의 합집합 나누기 겹치는 부분 교집합.
