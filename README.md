# 다변량 데이터 분석 프로젝트
### 요약
인구 수와 사교육비, 1인당 소득이 해법수학의 시도별 지점 수와 상관관계가 있는지 살펴보았다. 그 중에 가장 확실한 상관관계를 나타내는 인구 수를 시군구까지 확장해서 해법수학 및 경쟁사의 지점 수와 상관관계를 구하고 그 차이를 구했다. 그 결과 해법수학이 경쟁사보다 인구수와 지점 수의 강한 상관관계를 나타내서 해법수학이 경쟁사에 비해 인구수에 비례해서 지점을 내고 있다는 것을 알 수 있었다.

---

### 방법
1. 인구수와 사교육비, 1인당 소득 중 어떤 통계량이 지점 수 데이터와 상관관계가 있을지 알아보기 위해 각 통계량과 지점 수를 이용해 scatter plot을 그렸다.
1. 시군구별 인구 데이터와 해법수학, 경쟁사의 지점 수 데이터를 이용해 상관관계를 분석한다. 시군구별 인구수와 지점수로 산점도를 그리고 피어슨 상관계수를 구했다. 그 후에 해법수학의 상관계수가 경쟁사의 상관계수보다 유의미하게 클 것이라는 가설을 검정했다.  
1. 유의수준 0.05 하에 귀무가설은 상관계수의 유의미한 차이가 없는 것이며, 대립가설은 해법수학의 상관계수가 경쟁사의 상관계수보다 유의미하게 높다는 것으로 설정했다.  
1. 상관계수끼리의 차이는 Z-검정을 통해 알아볼 수 있다. 하지만 상관계수는 -1부터 1 사이의 값이므로 먼저 Fisher transformation을 통해 정규분포의 범위로 늘려주어야 할 필요가 있다. Fisher transformation의 공식은 아래와 같다.
   $$r' = 0.5 \times \ln \left\lvert 1 + r \over 1 - r \right\rvert \quad※(r = 상관계수)$$
1. 이후 transformation된 𝑟₁\`과 𝑟₂\`을 이용해 Z-score를 구한다. Z-score를 구하는 공식은 아래와 같다.
   $$Z = \frac{r_1' - r_2'}{\sqrt{\frac{1}{N_1 -3}+\frac{1}{N_2 - 3}}} \quad ※(N = 표본\,수)$$  
1. 마지막으로 Z-score를 정규분포표에 대조해 p-value를 구하고 p<0.05이면 귀무가설을 기각한다.  

### 결과

| (a) <img src="https://github.com/jjun2648/Multivariate_analysis/blob/main/images/%EC%8B%9C%EB%8F%84_%EC%9D%B8%EA%B5%AC%EC%88%98_%EC%A7%80%EC%A0%90%EC%88%98.png"> <p> (b) <img src="https://github.com/jjun2648/Multivariate_analysis/blob/main/images/%EC%82%AC%EA%B5%90%EC%9C%A1%EB%B9%84_%EC%A7%80%EC%A0%90%EC%88%98.png"> <p> (c) <img src="https://github.com/jjun2648/Multivariate_analysis/blob/main/images/%EA%B0%9C%EC%9D%B8%EC%86%8C%EB%93%9D_%EC%A7%80%EC%A0%90%EC%88%98.png"> |
|:--:|
| <b> [Figure1] (a) 시도별 인구수에 따른 해법수학 지점 수 (b) 시도별 사교육비와 해법수학 지점 수 (c) 시도별 1인당 소득과 해법수학 지점 수 </b> |
어떤 통계량이 지점 수 데이터와 상관관계가 있을지 알아보기 위해 각 통계량과 지점 수를 이용해 scatter plot을 그렸다. 인구 수와 지점 수가 강력한 상관관계를 나타내는 것을 볼 수 있다.

| (a) <img src="https://github.com/bigdata4th-first-line/Smarthb/blob/main/images/%ED%95%B4%EB%B2%95%EC%88%98%ED%95%99_%EC%9D%B8%EA%B5%AC_%EC%A7%80%EC%A0%90%EC%88%98.png"> <p> (b) PearsonRResult(statistic=0.86, pvalue=2.95e-68) <p> (c) <img src="https://github.com/bigdata4th-first-line/Smarthb/blob/main/images/%EA%B2%BD%EC%9F%81%EC%82%AC_%EC%9D%B8%EA%B5%AC_%EC%A7%80%EC%A0%90%EC%88%98.png"> <p> (d) PearsonRResult(statistic=0.73, pvalue=1.31e-39) <p> (e) Z-score = 3.79, p-value = 7.50e-05|
|:--:|
| <b> [Figure2] (a) 시군구별 인구수에 따른 해법수학 지점 수 (b) 시군구별 인구수와 해법수학 지점 수 사이의 상관계수 및 p-value (c) 시군구별 인구수에 따른 경쟁사 지점 수 (d) 시군구별 인구수와 경쟁사 지점 수 사이의 상관계수 및 p-value (e) 해법수학과 경쟁사 사이의 상관계수 차이 검정 결과 </b> |
해법수학과 경쟁사 모두 인구수와 지점수 사이의 강력한 상관관계를 나타냈다. 이후 두 상관관계 중 해법수학이 더 강력한 상관관계를 나타낸다는 가설을 증명하기 위해 상관계수의 차이를 검정했다. Z-score는 3.79로 나타났고 유의확률이 유의수준 0.05보다 작기 때문에 귀무가설을 기각하고 대립가설을 채택해서 해법수학과 인구수의 상관계수가 경쟁사와와 인구수의 상관계수보다 높다고 주장할 수 있다.

### 사용 라이브러리
numpy Python package (version 1.25.1)  
Matplotlib Python package (version 3.7.2)  
pandas Python package (version 1.5.3)  
plotly Python package (version 5.9.0)  
scipy Python package (version 1.10.0)  
seaborn Python package (version 0.12.2)  
