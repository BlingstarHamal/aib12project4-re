# aib12project4

https://www.kaggle.com/datasets/divyansh22/dummy-astronomy-data

별-은하 이미지를 ResNet50을 이용해서 분류 하기

p4.ipynb 초기 진행 과정  
p4-es.ipynb early-stopping  == final file same ai_12_김상혁_project4.ipynb  
p4-nones.ipynb none-early-stopping  
p4-non-oversampling.ipynb non-oversampling  
Cutout Files 이미지 데이터  
requirments.txt pip 설치파일 
실제 코드를 실행시키면 모델폴더 및 데이터가 생성됩니다.  
깃허브 용량상 모델은 제외하고 업로드 하였습니다.   

# 은하 별 이중 분류 모델링 - ResNet50을 이용한 딥러닝

## 주제선정  
관측 자료의 종류 구분  

## 데이터
캐글 (ps://www.kaggle.com/datasets/divyansh22/dummy-astronomy-data)  
인도에 있는 1.3m 천체망원경으로 관측한 2k*2k 이미지를 64*64 컷아웃한 자료  
은하와 별로 구분 된 4천여개의 이미지  

## 전처리  
라벨링  
훈련 검증 테스트 데이터 분할
SMOTE 라이브러리로 오버샘플링( 기존 타겟 비율 1:3 -> 오버샘플링후 1:1 )  

## Resnet50 모델링  
MaxPooling Dropout BatchNormalization 옵션 추가  
AUC를 비롯한 다양한 성능 측정  
Learning rate, Early-Stopping 적용  

## 결론 및 한계
AUC ~ 0.88 성능이 좋아보이나 문제가 존재함  
과적합이 예상되어짐.-> 오버샘플링을 했을때도 큰 변화가 없음(0818)  
a. 이미지에 천체가 여러개 존재하는 것이 있는데, 피팅 과정에서 이미지 중심에 큰 가중치를 넣어야했지 않았나 싶지만 구현 실패
b. 실제 천문자료는 다양한 파장영역의 데이터를 가지고 있는데, 해당자료는 RGB만 표현함.  
c. 모델링을 이미지 중심에 가중치를 주고, Fits Format 자료를 이용하면 좀더 좋은 결과를 내놓을것이라 여겨짐  
