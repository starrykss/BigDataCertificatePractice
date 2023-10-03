# 실기 시험 응시 팁

## 응시 환경 미리 체험하기
https://dataq.goorm.io/exam/116674/%EC%B2%B4%ED%97%98%ED%95%98%EA%B8%B0/quiz/1

## 시험 응시 제약 사항
- 라인별 실행 불가
- 그래프 시각화 불가
- 단축키 미제공
- 패키지 추가 설치 불가
- 콘텐츠는 복사, 붙여넣기 불가하며 코든느 복사, 붙여넣기 사용 가능
- 노트북(`ipynb`) 형식이 아니기 때문에 `print()` 함수를 사용해야만 출력 가능
- 실제 시험 환경에서는 1,000줄만 출력
- 자동 완성 기능 미제공

## 유용한 함수
### `help()`
- 키워드, 함수, 클래스, 메서드에 대해서 파라미터, 리턴값, 예시 사용법을 알려주는 내장 함수

### `dir()`
- 객체가 갖고 있는 변수와 메서드를 보여주는 내장 함수
- `sklearn`은 `dir()` 대신에 `__all__`을 이용해야 하위 모듈 확인이 가능하다.
    - `sklearn` 하위 모듈 내에는 `dir()`, `__all__` 둘 다 동일하나 `dir()`는 알파벳 순으로 정렬해준다.
    - 예를 들어 싸이킷런에서 앙상블 모듈을 사용하고 싶은데 기억이 나지 않을 경우, `print(sklearn.__all__)`을 통해 하위 모듈을 확인할 수 있다.

```py
import sklearn
```

- `sklearn`이 갖고 있는 변수와 메서드 확인

```py
print(dir(sklearn))
```

```text
['__SKLEARN_SETUP__', '__all__', '__builtins__', '__cached__', '__check_build', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '__version__', '_config', '_distributor_init',
'base', 'clone', 'config_context', 'exceptions', 'get_config', 'logger', 'logging', 'os', 'random', 'set_config', 'setup_module', 'show_versions', 'sys', 'utils']
```

- `sklearn`의 하위 모듈 확인
    - `ensemble`이 하위 모듈에 있는 것을 알 수 있다.

```py
print(dir(sklearn.__all__))    # 하위 모듈 출력
```

```text
['calibration', 'cluster', 'covariance', 'cross_decomposition', 'datasets', 'decomposition', 'dummy', 
'ensemble', 'exceptions', 'experimental', 'externals', 'feature_extraction', 'feature_selection', 'gaussian_process', 'inspection', 'isotonic', 'kernel_approximation', 
'kernel_ridge', 'linear_model', 'manifold', 'metrics', 'mixture', 'model_selection', 'multiclass', 'multioutput', 'naive_bayes', 'neighbors', 
'neural_network', 'pipeline', 'preprocessing', 'random_projection', 'semi_supervised', 'svm', 'tree', 'discriminant_analysis', 'impute', 'compose', 
'clone', 'get_config', 'set_config', 'config_context', 'show_versions']
```

- 실제 시험 환경에서 `import`하는 경우 특정 라이브러리도 임포트 해야 `help()`, `dir()` 에러가 발생하지 않는다.
- `ensemble` 모델을 불러오고 나서 해당 하위 모듈을 조회할 수 있다.
    - 앙상블 모델에서 랜덤 포레스트 분류기를 잊었다면 내부에서 `RandomForestClassifier` 확인이 가능하다.

> 잘못된 사용 예 (에러 발생)

```py
print(sklearn.ensemble.__all__) 
```

```text
AttributeError: module 'sklearn' has no attribute 'ensemble'
```

> 올바른 사용 예

```py
import sklearn.ensemble
```

```py
print(dir(sklearn.ensemble))
```

```text
['AdaBoostClassifier', 'AdaBoostRegressor', 'BaggingClassifier', 'BaggingRegressor', 'BaseEnsemble', 'ExtraTreesClassifier', 'ExtraTreesRegressor', 'GradientBoostingClassifier', 'GradientBoostingRegressor', 'IsolationForest', 'RandomForestClassifier', 'RandomForestRegressor', 'RandomTreesEmbedding', 'StackingClassifier', 'StackingRegressor', 'VotingClassifier', 'VotingRegressor', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '_bagging', '_base', '_forest', '_gb', '_gb_losses', '_gradient_boosting', '_iforest', '_stacking', '_voting', '_weight_boosting', 'typing']
```

```py
print(sklearn.ensemble.__all__)
```

```text
['BaseEnsemble', 'RandomForestClassifier', 'RandomForestRegressor', 'RandomTreesEmbedding', 'ExtraTreesClassifier', 'ExtraTreesRegressor', 'BaggingClassifier', 'BaggingRegressor', 'IsolationForest', 'GradientBoostingClassifier', 'GradientBoostingRegressor', 'AdaBoostClassifier', 'AdaBoostRegressor', 'VotingClassifier', 'VotingRegressor', 'StackingClassifier', 'StackingRegressor']
```



---
- [참고 사이트 1](https://potato-potahto.tistory.com/entry/%EB%B9%85%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%B6%84%EC%84%9D%EA%B8%B0%EC%82%AC-%EC%8B%A4%EA%B8%B0-%EC%8B%9C%ED%97%98-%ED%99%98%EA%B2%BD-%ED%8C%81)