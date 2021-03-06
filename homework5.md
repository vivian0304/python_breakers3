## Pandas 사용법과 전처리, EDA를 중심으로 정리

### 데이터 분석
- 데이터 분석이란?
    - 인사이트를 도출하기 위해 알고리즘과 수학적 처리과정을 적용하여 해당 정보에 대한 결론을 도출하고 패턴을 찾기 위한 목적으로 데이터를 다루는 과학
- 데이터 분석의 과정
    - Exploratory Data Analysis
        - 문제 정의
        - 시각화 & 변수 탐색
    - Data preprocessing
        - 적절한 데이터 처리
        - 정규화
        - 교차검증 설정
    - Feature Engineering
        - 변수 생성
        - 차원 축소
        - 특징 추출
    - Modeling
        - 예측 모델링
        - 분류 모델링
        - 결과 해석
- 데이터 분석이 가장 중요한 것은 무엇일까?
    - 바로 데이터 그 자체이다!
        - 데이터 분석 과정의 80%는 변수 탐색, 데이터 다듬기, 분석에 더 적합하게 하는 것으로 이루어져 있다!
- 데이터 분석 시 파이썬에서는 pandas를 활용할 수 있다!

따라서 지금부터 pandas의 사용법에 대해 알아보도록 하겠다!

### Pandas 사용법
- 출처
    - https://github.com/koptimizer/Python_Breakers
- 데이터 오브젝트 : 데이터를 담고 있는 그릇
    - Series : 인덱스라는 한 가지 기준에 의해 데이터 저장
    - DataFrame : 인덱스와 컬럼이라는 두 기준에 의해 표 형태처럼 데이터 저장
        - dataframe을 만들기 위해서는 같은 길이의 1차원 선형 자료형 여러 개가 필요함
        - **보통 pandas를 통해서는 DataFrame을 많이 사용하게 됨!**
            - 따라서 아래부터는 DataFrame을 기준으로 pandas의 사용법을 알아보게 될 것이다
- Dataframe의 특징
    - DataFrame으로 저장된 데이터들에 통계함수를 직접적으로 사용가능
    - 다양한 포맷으로 import/exprt 가능
    - 행에 대한 접근은 DataFrame.loc[인덱스 이름] 혹은 .iloc["정수형 위치 인덱스"]
    - 열에 대한 접근은 DataFrame["열이름"] 혹은 ["정수형 위치 인덱스"]
    - DataFrame의 깊은 복사는 s.copy()
    - 데이터 확인하기
        - .head()/.tail() : 맨 앞이나 뒤의 자료들 몇 개를 알아보고 싶을 때 사용
        - .index : DataFrame의 인덱스를 알아보고 싶을 때 사용
        - .columns : DataFrame의 컬럼을 알아보고 싶을 때 사용
        - .valus : DataFrame의 numpy데이터를 알아보고 싶을 때 사용
        - .describe() : 생성했던 DataFrame의 간단한 통계 정보 보여줌
        - .T : DataFrame에서 index와 column을 바꾼 형태의 DataFrame
- Dataframe의 자세한 사용법은 아래 링크를 참고하길 바란다
    - https://dandyrilla.github.io/2017-08-12/pandas-10min/

pandas를 통해 데이터 분석을 완료하였다면 전처리를 통해 데이터를 분석 가능한 상태로 만들어야 한다

### 전처리
- 전처리의 필요성
    - 데이터셋은 보통 바로 분석이 불가능할 정도로 지저분(messy)함
    - 분석이 가능한 상태로 만드는 것이 Data Preprocessing
- 전처리 과정
    - 데이터 확인
        - .head()/.tail()/.info()/.describe() 등
    - 데이터 표준화
        - 데이터 타입 확인 후 더 어울리는 타입으로 변경
        - 데이터 표준화를 통해 가독성 상승
    - 결측치 처리
        - 결측치 : 비어있는 값(0과는 다름)
        - 결측치 처리를 해야하는 이유
            - 결측치로 인한 모델링 불가
            - 각종 통계치 확인 불가
        - 결측치 처리 방법
            - 삭제 : 간편하지만 데이터 수가 적어짐
            - 대체 : 다른 관측치들의 평균값, 최빈값, 중간값, 인근값 등으로 대체
            - 예측 값 삽입 : 관측치들만을 이용해 결측치를 예측하는 모델을 만들어 결측치 예측

전처리를 통해 분석 가능한 상태인 데이터셋을 분석할 수 있게 되었다.
그럼 우리는 어떤 방식으로 분석할 수 있을까?
여기서는 EDA의 시각화를 소개해보도록 하겠다

### EDA
- EDA(Exploratory Data Analysis)란?
    - 주어진 데이터 셋을 통해 탐색적으로 충분한 정보를 찾는 분석 방법
    - EDA를 통한 인사이트 도출과 가설설정은 분석의 큰 토대가 됨
- EDA에서 시각화를 하는 이유가 무엇일까?
    - 요약 통계 정보만으로는 데이터를 정확하게 볼 수 없기 때문이다!
- 데이터 시각화 : 그래프의 종류
    - Bar : 히스토그램, 막대그래프
    - Line : 꺽은선 그래프, 방사형 그래프
    - Pie : 원 그래프
- EDA로 시각화를 할 때 가장 중요하게 생각해야 할 점
    - 어떤 방식으로 시각화 했을때 우리 눈에 가장 효율적으로 잘 보일지!
        - why? 결국은 EDA를 하는 이유가 '정보'를 찾기 위한 과정이기 때문! 정보를 잘 찾으려면 우리 눈에 잘 보여야 하고, 그게 그 자체로 시각화가 잘 되어 의미 있어야 한다!
- 이상치 
    - 이상치란 : 전체적인 데이터/샘플 범위에서 동떨어진 관측값 -> 모델을 크게 왜곡시킬 가능성이 있음
        - **이상치와 결측치를 헷갈리지 맙시당!**
    - 이상치 결정 방법 : 시각화를 통해 확인 후 결정
    - 이상값 처리
        - 단순 삭제 : 단순 오타, 주관식 설문 등의 비현실적 응답, 처리과정에서의 오류 등에서 사용
        - 대체 : 평균, 중간값, 중앙값으로 대체
        - 이상치가 자연발생 했을 경우
            - 변수화, 리샘플링, 케이스 분리 해석 등
