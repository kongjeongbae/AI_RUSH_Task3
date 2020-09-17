# AI RUSH 2020
![header](./readme_imgs/header.jpg)

https://campaign.naver.com/airush/

- 팀명: 3000
- 팀원: 공정배, 김홍엽
- 과제: 이용자 행동의 시계열 분석을 통한 비정상적인 행위 탐지
- 순위: 2위
- 상금: 700만원

코드 및 데이터는 네이버 검토 후 공개하겠습니다.



## Task: Anomaly Detection

Repo for training a baseline model for the AI Rush anomaly detection challenge.
The baseline model is a one hidden layer MLP.



## Model

Catboost, XGBoost Ensemble model



## File Structure

```
rush3-*
├── data_loader.py
├── evaluation.py
├── test
│   ├── test_data (folder)
│   │   ├── *.csv
│   └── test_label
└── train
    ├── train_data (folder)
    │   ├── *.csv
    └── train_label
```



## Important notes

- The function that's bind to NSML infer needs to output a pandas dataframe
- The dataframe looks like this

```
        a.csv  ...  z.csv
0        0.0   ...   0.0
1        0.0   ...   0.0
2        0.0   ...   0.0
3        0.0   ...   0.0
4        0.0   ...   0.0
...      ...   ...   ...
1819     NaN   ...   NaN
1820     NaN   ...   NaN
1821     NaN   ...   NaN
1822     NaN   ...   NaN
1823     NaN   ...   NaN
```

- as each csv file has variable length, the output dataframe has trailing NaNs.
- Each csv file is a **time series** of a user.
- Each csv file (or a time series) may or may not contain anomaly data.
- Note that baseline model did not use the fact that the given data is a set of time-series



## Run experiment

To run the baseline model training, run
```
nsml run -d rush3-1 -m "a message"
```



## Metric

F1 score