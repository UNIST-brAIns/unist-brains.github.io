---
title: "Brand New Style"
tags: style-transfer
---

작성자: 김선욱



# Style-Transfer
![Style_Transfer_Sample](/assets/Style_Transfer_Sample.png)

**스타일 트랜스퍼**(style transfer)란 스타일 이미지(style image)가 주어졌을 때, 해당 이미지를 그대로 필터처럼 사용하는 것이 아닌 특징(feature)을 추출하여 타겟으로 삼는 콘텐츠 이미지(content image)에 전이(transfer)시키는 기법입니다. 이러한 특징을 스타일(style)이라고 부르며, 이를 실현하기 위해 **생성적 적대 신경망(GAN, Generative Adverserial Networks)** 등이 사용됩니다.

## 역사 & 구성
스타일 트랜스퍼는 2015년 Leon A. Gatys 등의 [A Neural Algorithm of Artistic Style](https://paperswithcode.com/paper/a-neural-algorithm-of-artistic-style)이라는 논문에서 제안되었습니다. 그는 University of Tübingen 박사과정에서 DCNN(Deep Convolution Neural Networks)에 대해 연구하던 중 이미지의 스타일과 콘텐츠가 분리될 수 있음을 발견했고, 분리된 스타일을 다른 콘텐츠 이미지(content image)와 결합해보자는 아이디어를 떠올리면서 스타일 트랜스퍼의 시대가 열리게 된 것입니다.

## 학습 & 전이
스타일 트랜스퍼 기법을 이용한 전이는 크게 두 가지 방법으로 이루어집니다.

**1) Pre-trained Model based Style-Transfer**
학습된 모델을 기반으로 콘텐츠 이미지와 스타일 이미지를 결합하여 새로운 이미지를 생성하는 방식입니다. 이미지 2개만으로도 스타일 트랜스퍼가 가능하다는 장점이 있으며, 최근에는 [Demo Website](https://reiinakano.com/arbitrary-image-stylization-tfjs/)를 통해 여러 스타일 이미지를 결합하여 새로운 스타일을 만든 후, 이를 콘텐츠 이미지에 적용하는 UX(User Experience)를 제공하기도 합니다.

![Style_Transfer_Demo](/assets/Style_Transfer_Demo.png)

단, 이러한 방식은 콘텐츠 이미지나 스타일 이미지를 교체해야할 수도 있으며, 그만큼 조합할 수 있는 경우의 수와 변수가 너무 많다는 단점이 있습니다.

**2) GAN based Style-Transfer**

최근에 각광받고 있는 방식으로 학습된 GAN 모델을 바탕으로 투입된 콘텐츠 이미지를 스타일 트랜스퍼 해주는 방식입니다. 1번의 방식으로 스타일 트랜스퍼를 진행하다보면 모델의 스타일이 어떠한 한 스타일로 수렴된다는 느낌을 지울 수 없는 경우가 많습니다. GAN 모델을 이용한 방식은 스타일 이미지들을 학습하여 투입된 콘텐츠 이미지를 학습해온 스타일 기반으로 재생성함으로써 완전히 새로운 시도를 가능하도록 합니다.

단, 학습을 위해서 방대하고 다양하며 선별된 스타일 이미지 데이터셋이 필요로 하며, 저작권 등의 문제로 인해 원하는 스타일을 지닌 데이터셋의 확보의 어려움을 겪을 수도 있습니다.


| | Pre-trained Model-based  | GAN-based |
| ------------- | ------------- | ------------- |
|**입력(Input)**  | 콘텐츠 이미지(content image)  | 콘텐츠 이미지(content image)|
| | 스타일 이미지(style image)   | - |
| **장점(Pros)**  | 비교적 덜 복잡한 학습 과정 | 자연스러운 결과물 & 다양성 확보 |
| **단점(Cons)**  | 너무 많은 경우의 수 & 변수  | 데이터셋 확보의 어려움 |

## 응용 & 활용

해당 섹션(section)에서는 흥미를 돋우기 위해 글 없이 github에 있는 응용 사례를 사진으로 간단히 첨부하도록 하겠습니다. 링크는 Project Website거나 PaperWithCode이며 이를 통해 Github, 논문 PDF 등에 접속해서 직접 재현해보고 학술적 내용에 대한 공부를 해볼 수 있으므로 *UNIST의 격투기형 교육* 이 글을 시작으로 한 번 해보도록 합시다! ~~참고로 UNIST 교수님이 저자인 논문도 있다~~

**1) 사진 표정 & 구도 변화
[Diagonal Attention and Style-based GAN for Content-Style Disentanglement in Image Generation and Translation (ICCV 2021)](https://paperswithcode.com/paper/diagonal-attention-and-style-based-gan-for)**

> **구도 변화**

![1_1](/assets/1_1.jpg)

> **표정 변화**

![1_2](/assets/1_2.jpg)

> **피부색 변화**

![1_3](/assets/1_3.jpg)

**2) 사진 속 인물 나이 변화
[Scaling-up Disentanglement for Image Translation (ICCV 2021)](https://www.vision.huji.ac.il/overlord/)**

![2](/assets/2.jpg)

**3) 고양이-강아지 변환 & 고양이 종 바꾸기
[Continuous and Diverse Image-to-Image Translation via Signed Attribute Vectors (2021)](https://helenmao.github.io/SAVI2I/)
[Rethinking the Truly Unsupervised Image-to-Image Translation (ICCV 2021)](https://paperswithcode.com/paper/rethinking-the-truly-unsupervised-image-to)
[QS-Attn: Query-Selected Attention for Contrastive Learning in I2I Translation (CVPR 2022)](https://paperswithcode.com/paper/qs-attn-query-selected-attention-for)**

![3_0](/assets/3_0.png)

![3](/assets/3.png)

![3_1](/assets/3_1.png)

**4) 스케치 스타일 트랜스퍼
[Complementary, Heterogeneous and Adversarial Networks for Image-to-Image Translation (IEEE TIP, 2021)](http://aiart.live/chan/)**

![4](/assets/4.jpg)

**5) 애니메이션 & 코믹스 스타일 트랜스퍼
[SPatchGAN: A Statistical Feature Based Discriminator for Unsupervised Image-to-Image Translation (ICCV 2021)](https://paperswithcode.com/paper/spatchgan-a-statistical-feature-based)
[https://utkarshojha.github.io/few-shot-gan-adaptation/ (CVPR 2021)](https://github.com/utkarshojha/few-shot-gan-adaptation)
[StyleGAN-NADA: CLIP-Guided Domain Adaptation of Image Generators (2021)](https://stylegan-nada.github.io/)**

![5](/assets/5.jpg)

![5_1](/assets/5_1.gif)

![5_2](/assets/5_2.jpg)

**6) 명화 스타일 트랜스퍼
[A Style-Aware Content Loss for Real-time HD Style Transfer (ECCV 2018)](https://compvis.github.io/adaptive-style-transfer/)**

![6](/assets/6.jpg)

## Style-Transfer과 앞으로의 10년

![Loving_Vincent](/assets/Loving_Vincent.jpg)

빈센트 반 고흐의 전기를 다룬 영화 **러빙 빈센트(Loving Vincent)**는 107명의 아티스트가 그린 6만 5000장 유화 작품으로 구성된 영화입니다. 현재 Netflix를 통해서도 볼 수 있는 이 영화는 개봉 당시였던 2017년 주목을 받았으며, 탄탄한 작품성과 색다른 시도로 크게 호평을 받았습니다.

> 리빙 빈센트의 한 장면

![Loving_Vincent_jpg](/assets/Loving_Vincent.gif)

스타일 트랜스퍼가 영상에도 적용되기 시작한 지금, 해당 영화를 만들기 위해서는 더 이상 107명의 전문 아티스트를 섭외하여 고흐풍의 그림을 그릴 필요없이 만들어진 영상을 학습된 모델을 통해 스타일 트랜스퍼하면 될 것입니다.

이처럼 스타일 트랜스퍼는 영화, 만화, 애니메이션 등 다양한 시각예술 분야에서 예술가들의 노동을 줄여주며, **누구나 쉽게 예술을 할 수 있는 환경**을 만들어가고 있습니다. 기술은 필연적으로 사람들의 행동 양식을 바꿉니다. 10년 전에는 잉크와 종이로 가득한 만화가의 작업실이, 지금은 좋은 사양의 컴퓨터와 액정 타블렛으로 바뀐 것처럼 다양한 인공지능 기법이 바꾸어갈 앞으로의 10년을 기대해보며 글을 줄입니다 :)
