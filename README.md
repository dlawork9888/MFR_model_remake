# MFR model remake
## MFR은 지금 리메이크 중!
- kaggle의 gtzan 데이터셋을 이용합니다!
  - 10개의 장르, 각 장르당 100개의 음악 샘플을 제공
  - 
### 용량 초과 파일
(.gitignore에서 확인 가능)
```
- music_raw_data 폴더 (gtzan 데이터셋의 genres_original과 동일)
https://drive.google.com/drive/folders/1dpYLCEJ4Sh2rW_G_Y8rsJGakEh-vg3ED?usp=drive_link
- extracted_mfccs_and_labels.npz (MFCC 계수 40)
https://drive.google.com/file/d/1pPnMvljMY39c8nWpGoLHFMoHV5-_RMn9/view?usp=drive_link
```

### 바꾸고자 하는 방향
- 기존 모델은 MFCC, Chromagram, Tempogram을 오디오에서 추출,
- 위 세 가지를 조합하여 하나의 음원을 3채널 이미지 형태의 데이터로 변환합니다.(시간 차원, 주파수 차원, 채널)
- Tempogram, Chromagram의 영향보다 MFCC가 가지는 영향이 더 크다고 판단하여 MFCC만을 이용, 대신 20 계수가 아닌 40계수로 더 많은 정보를 추출할 수 있도록 바꾸고자 합니다.

### # 2024.03.08
- 우선 정확한 분류기를 만들려고 하였으나, loss 폭발 발생!
- 또한, 데이터셋이 그렇게 깔끔하진 않은 탓도 있는 듯 합니다.
  - 음악의 장르라는 주관성(실제로 레게 장르의 샘플들은 레게라고 안느껴지는 샘플이 많음)
  - 비정형 데이터
- 뭐, 어차피 타협할거니 상관없습니다 !
- 베이스 모델의 epoch 20 즈음 부터 val loss가 폭발하기 시작합니다 ! (early stopping 필요 !)

  
