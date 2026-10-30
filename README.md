# 밀 낟알 품종 분류 데이터셋 (Seeds)

수행평가용 데이터입니다. 밀 낟알(씨앗)의 **크기와 모양**을 잰 7가지 수치로 그 낟알이 **3가지 품종(Kama, Rosa, Canadian)** 중 어느 것인지 분류하는 데이터셋입니다.

- 출처: UCI Machine Learning Repository — [Seeds](https://archive.ics.uci.edu/dataset/236/seeds) (CC BY 4.0)
- 원작자: Małgorzata Charytanowicz, Jerzy Niewczas, Piotr Kulczycki, Piotr Kowalski, Szymon Łukasik, Sławomir Żak (Polish Academy of Sciences, 2010)
- 인용: Charytanowicz, M., Niewczas, J., Kulczycki, P., Kowalski, P., Łukasik, S., & Żak, S. (2010). Seeds [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5H30K

## 파일 구성

| 파일 | 설명 |
|---|---|
| `seeds.csv` | 수행평가용 데이터 (CSV, 헤더 포함) |
| `README.md` | 데이터 및 속성 안내 (이 문서) |

> 수행평가는 **Google Colab**에서 진행합니다. 아래 **데이터 불러오기** 코드로 데이터를 불러온 뒤, 이후 과정은 스스로 해결해 보세요.

## 데이터 개요

| 항목 | 내용 |
|---|---|
| 샘플(행) 수 | 210개 |
| 열 수 | 8개 (특성 7 + 품종 1) |
| 결측치 | 없음 |
| 클래스 분포 | Kama(1) 70개, Rosa(2) 70개, Canadian(3) 70개 — 각 33.3% |

## 데이터는 어떻게 만들어졌나?

폴란드 루블린의 농업연구소 실험 밭에서 키운 밀 3품종에서 낟알을 70개씩 무작위로 골랐습니다.
낟알을 **연X선(soft X-ray)** 으로 촬영하면 내부 구조까지 선명하게 보이는데, 이 사진을 컴퓨터로 분석해 낟알의 넓이·둘레·길이·폭 등 **7가지 수치**를 측정했습니다.
길이 단위는 **mm(밀리미터)**, 넓이 단위는 **mm²** 입니다.

## 속성(열) 설명

### 정답(타깃)

| 열 이름 | 설명 | 값 |
|---|---|---|
| `variety` | **밀 품종 (예측해야 할 정답)** | `1` = Kama, `2` = Rosa, `3` = Canadian |

> 숫자 1, 2, 3은 품종의 **이름표**일 뿐, 크기나 순서를 뜻하지 않습니다.

### 낟알의 7가지 특징

| 번호 | 열 이름 | 한글 이름 | 설명 | 값의 범위 |
|---|---|---|---|---|
| 1 | `area` | 넓이 | 낟알 단면의 면적 (A, mm²) | 10.59 ~ 21.18 |
| 2 | `perimeter` | 둘레 | 낟알 테두리의 길이 (P, mm) | 12.41 ~ 17.25 |
| 3 | `compactness` | 조밀도 | 4π × 넓이 / 둘레² — **원에 가까울수록 1에 가까움** | 0.8081 ~ 0.9183 |
| 4 | `kernel_length` | 낟알 길이 | 낟알의 가장 긴 방향 길이 (mm) | 4.899 ~ 6.675 |
| 5 | `kernel_width` | 낟알 폭 | 낟알의 너비 (mm) | 2.630 ~ 4.033 |
| 6 | `asymmetry_coef` | 비대칭 계수 | 낟알 모양이 좌우로 얼마나 비대칭인지 — 클수록 비대칭 | 0.7651 ~ 8.456 |
| 7 | `groove_length` | 홈 길이 | 낟알 가운데 파인 **홈(고랑)의 길이** (mm) | 4.519 ~ 6.550 |

모든 특성 값은 실수(소수)입니다.

## 데이터 불러오기 (Google Colab)

Colab 새 노트북의 코드 셀에 아래 코드를 붙여넣고 실행하세요.

```python
import pandas as pd

url = "https://raw.githubusercontent.com/thiskorea81/Seeds/main/seeds.csv"
df = pd.read_csv(url)

print(df.shape)       # (210, 8)
df.head()
```

이후 과정은 스스로 해결해 보세요.
