# 112-1 師大科技系程式語言
---
授課教師：蔡芸琤老師

姓名：劉彥谷

系級：科技系2年級

## 課程筆記區

[最新筆記](https://hackmd.io/@kennyliou/r1V4OLMlp) 

### Week 1 / Introduction
### Week 2 / Basics in Python
* Data Type
* 變數命名規則
  * 只能由英文字母、數字、底線或中文字所組成，建議使用英文字母
  
  * 英文字母大小寫是有差異的   
  
  * 不能是保留字或內建函數名稱 
  
  * 變數名稱不能有空白，空白可用底線代替

  * <img width="350" alt="截圖 2023-09-14 上午9 38 32" src="https://github.com/knyliu/PL/assets/131148428/faca76e2-b9fe-4883-8675-487f4ba2a18f" >

* set
```python=
set_1 = {"apple", "banana", "cherry"}

set_2 = {"orange", "apple", "melon"}

print(set_1 & set_2)
```
### Week 3 / Python 基礎 02
https://colab.research.google.com/drive/1Ba8oYWiPkpJi90jA8v3adj4bqKW5JBMU?usp=sharing#scrollTo=O0nzGW5_51zh
### Week 4 / Python 基礎 03
[Example Code](https://github.com/pecu/PL/blob/main/HW1/HW1-Part2.ipynb)
##### 預設三個問題
1. 年齡和收入的關係是甚麼？
1. 哪些工作類型更容易賺到高薪？哪些工作類型更容易賺到低薪？
1. 工作時間是否影響收入？
##### 讀入資料
```header=None```：把column的標題拿掉
```python=
import pandas as pd
data = pd.read_csv('adult.data.csv', header=None)
data.head()
```
![](https://hackmd.io/_uploads/HkOO_LGla.png)
##### Name the Column (Using the new name we want)
```python=
data.columns = ['age', 'workclass', 'fnlwgt', 'education', 'education_num',
              'marital_status', 'occupation', 'relationship', 'race', 'sex',
              'capital_gain', 'capital_loss', 'hours_per_week', 'native_country', 'income']

data.head()
```
![](https://hackmd.io/_uploads/S1ZnuUGxT.png)
##### groupby
```mean```平均
```agg```標準差
```median```中位數
```python=
# 以收入進行 groupby 找出年齡的分布
age_income = data.groupby('income')['age'].agg(['mean', 'std', 'median'])

age_income
```
![](https://hackmd.io/_uploads/H1VHtLMep.png)
##### count() / unstack()
```count```取得數量
```stack```將原本分組的資料從多級索引（MultiIndex）結構變為一個更方便查看的二維資料表格形式
例如：
將workclass欄位的不同值變成了income欄位的標籤，生成了一個以不同工作類別為列、不同收入水平為欄的資料表格。

```python=
#哪些工作類型更容易賺到高薪？哪些工作類型更容易賺到低薪？

# 計算每個工作類型中高收入和低收入的人數
income_by_job = data.groupby(['workclass', 'income'])['sex'].count().unstack()

income_by_job
```
![](https://hackmd.io/_uploads/rkdrnLMl6.png)
##### 
```python=
# 計算每個工作類型中，高收入與低收入人數佔該工作類型總人數的比例
income_by_job['high_income_ratio'] = income_by_job[' >50K'] / income_by_job.sum(axis=1)
income_by_job['low_income_ratio'] = income_by_job[' <=50K'] / income_by_job.sum(axis=1)

income_by_job
```
![](https://hackmd.io/_uploads/HJFSRLMgT.png)

## 作業連結區

### HW1 - Basics of Python

[HW1](https://github.com/knyliu/PL/blob/main/PL_HW1/PL_HW1.ipynb) 

### HW2 - Data Cleaning / Data Analysis / Data Visualization

[HW2](https://github.com/knyliu/PL/blob/main/PL_HW2/PL_HW2.ipynb) 

### HW3 - Web Crawler with LLM

[HW3](https://github.com/knyliu/PL/blob/main/PL_HW3/README.md) 

## 專題連結區


```
Markdown 語法說明：https://markdown.tw/
```
