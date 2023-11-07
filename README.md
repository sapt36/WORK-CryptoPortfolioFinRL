# CryptoFinRL
 Undergraduate senior project

###  `[原始程式執行結果雲端連結(+44%)]` [link](https://drive.google.com/drive/folders/1UOkK9s2VT85rEGZUi_tc_dO1ZZhvYcOd?usp=sharing)
###  `[專題海報製作WORD連結]` [link](https://docs.google.com/document/d/1O0SIYdF8UCiFH5vOIVQ1MKQ8Owug0RxzUYmPVbZCoIM/edit)
 
# 實驗說明
## 歷史幣價資料取得
* 幣安API [link](https://binance-docs.github.io/apidocs/websocket_api/cn/#185368440e)
## 幣種
* BTC
* ETH
* BNB
* SOL
* BUSD
## 資料切分
* 訓練時間段 : 2020/10/17 ~ 2021/10/17
* 測試時間段 : 2021/10/18 ~ 2023/10/25
## 避險機制
### 邏輯
#### 比特幣做為加密貨幣的元老，其走勢往往能牽動其他的加密貨幣，例如比特幣大漲時會帶動其他小幣可能一起漲，甚至漲得更多，但比特幣大跌時同樣也會讓其他小幣一起大跌，如同加密貨幣的大盤
### 原理
#### 利用比特幣的大盤特性計算一種動能指標來判斷當前市場是樂觀情緒(利於做多)還是悲觀情緒(不利於做多)

#### 在比特幣動能<0時判定為不利於做多的市場，將所有幣種賣出並轉換成穩定幣以度過進一步下跌風險

#### 在比特幣動能>0後判定為利於做多的市場，再將穩定幣換成各個幣種以吃到瞬間漲幅

### 特徵
* 眾多技術指標
* SuperTrend 指標
* Catch22 時間序列特徵
* 過去平均跌幅
* 微軟QLib 開高低收特徵
### 模型
* 強化學習演算法 A2C [link](https://github.com/openai/baselines/tree/master/baselines/a2c)
## 回測結果分析
* 比較基準為100%持有比特幣
#### 重要的衡量指標
* Alpha : 相對於大盤(比特幣)的超額報酬，愈高愈好，表示無考慮風險的賺錢能力
* Sharp Ratio : 承受一單位的風險可以獲得多少單位的報酬，愈高愈好，表示有考慮風險的賺錢能力
* CAGR : 年複合增長率，平均一年成長了多少%，愈高愈好
* Calmar Ratio : CAGR/Max Drawdown，愈高愈好，表示考慮最大風險的賺錢能力
* Mean Drawdown : 平均跌幅，愈低愈好，表示一期間內平均跌了多少%，表示抗跌能力
* Max Drawdown : 最大跌幅，愈低愈好，表示曾經跌了多少%
* Prob of Losing Money : 一期間內虧錢期間佔了多少%，愈低愈好，表示虧錢期間的長短
#### 從報酬的角度來看
* 2021年末的短暫牛市報酬大於單純持有比特幣
* 2023年比特幣從低點反彈並有幾段牛市，因此模型表現不如單純持有比特幣
* 2021/10/18~2023/10/25 獲利表現 44% 勝單純持有比特幣的-43%
#### 從風險的角度來看
* 2022年熊市可以透過避險機制避開數次大跌，跌幅遠低於單純持有比特幣
* 最大回撤 -41% 勝單純持有比特幣的76%
* 平均回撤 -17% 勝單純持有比特幣的55%
## 結論
#### 長期持有加密貨幣是一件高風險高報酬的事情，例如單純持有比特幣，雖然上漲時漲幅高，但下跌時跌幅也很高，並且很依靠進場的位置，是否屬於低點。本研究使用A2C強化學習模型並配合避險機制風控一個長期持有加密貨幣的投資組合，實驗結果表明可以在報酬與風險中間達到一個不錯的平衡，為投資人提供一個除了單純持有比特幣以外的新選擇。

## 報告問題猜測
1. 強調避險機制 -> 用cumulative performance的圖講
2. 2022/10 ftx倒閉事件大跌 躲不過
3. Action.csv 看權重(action.py)

## 注意事項
1. 連接雲端，並安裝完套件 執行階段 -> 重新啟動執行階段
2. 結束時要點擊 執行階段 -> 中斷連線並刪除執行階段(以防過度使用colab免費GPU)
3. 每次執行皆須重複以上流程

## 主要參考文獻
###  `[FinRL: Financial Reinforcement Learning]` [link](https://github.com/AI4Finance-Foundation/FinRL)

## 特徵參考
###  `[SUPERTREND]` [link](https://tw.tradingview.com/scripts/supertrend/)
###  `[Technical Analysis Library in Python]` [link](https://github.com/bukosabino/ta)
###  `[pycatch22 - CAnonical Time-series CHaracteristics in python]` [link](https://github.com/bukosabino/ta)
###  `[Qlib: An AI-oriented Quantitative Investment Platform]` [link](https://github.com/microsoft/qlib)

  
