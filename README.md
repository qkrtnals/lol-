# lol데이터분석

## 1.서론
미드라이너의 경기 데이터를 분석해 승패에 가장 큰 영향을 미치는 주요 지표를 찾아내고, 이를 기반으로 실력 평가 모델을 구축하고자 한다.<br>

분석에 사용된 데이터는 final_target_data.json 파일로, 각 매치별 미드라이너와 상대 미드라이너의 경기 지표를 포함하고 있다. <br>
- 라인전 이전: 전투 지표 7개 (at14killsRatio, at14deathsRatio 등)
- 라인전 이후: 전투 지표 7개 (af14killsRatio, af14deathsRatio 등)
- 승리 여부: targetWin 컬럼

## 2. 데이터 준비 및 전처리
라인전 이전과 이후 지표를 각각 'combat_at14'와 'combat_af14'로 구분<br>
![image](https://github.com/user-attachments/assets/18f17186-d839-4d73-b795-16cf4c06c316) <br>

라인전 이전과 이후 지표의 평균값을 계산하고, 두 지표 간의 차이를 'combat_diff'라는 새 컬럼으로 추가 <br>
![image](https://github.com/user-attachments/assets/226cfbf3-50f6-4a1e-ba69-b97f7a63290c) <br>

## 3. 모델 학습 및 분석
승리 여부를 예측하기 위해 로지스틱 회귀(Logistic Regression) 모델을 사용했습니다. 독립 변수로 combat_at14, combat_af14, combat_diff를 선택했으며, 종속 변수는 targetWin <br>
모델이 예측한 승리 확률과 실제 결과를 비교했을 때, 상당히 높은 예측 성능을 보였다. <br>
<br>
모델 학습 후, 예측 성능은 **정확도(Accuracy)**와 AUROC로 평가
- 정확도 81.25%
  모델이 예측한 승리 확률과 실제 결과를 비교했을 때, 상당히 높은 예측 성능을 보였다. <br>
  ![image](https://github.com/user-attachments/assets/4146b199-784e-4fce-8fb3-1d7da2afe95c)

  
## 4. 결론
이번 분석을 통해 라인전 이후의 지표가 승패에 중요한 영향을 미친다는 점을 확인했고, 단순한 지표 평균과 차이만으로도 실력 평가에 유의미한 결과를 도출할 수 있다는걸 알았다.
