# lol데이터분석

## 1.서론
미드라이너의 경기 데이터를 분석해 승패에 가장 큰 영향을 미치는 주요 지표를 찾아내고, 이를 기반으로 실력 평가 모델을 구축하고자 한다.<br>

분석에 사용된 데이터는 final_target_data.json 파일로, 각 매치별 미드라이너와 상대 미드라이너의 경기 지표를 포함하고 있다. <br>
- 라인전 이전: 전투 지표 7개 (at14killsRatio, at14deathsRatio 등)
- 라인전 이후: 전투 지표 7개 (af14killsRatio, af14deathsRatio 등)
- 승리 여부: targetWin 컬럼

## 2. 데이터 준비 및 전처리
라인전 이전과 이후 지표를 각각 'combat_at14'와 'combat_af14'로 구분

