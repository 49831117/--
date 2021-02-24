# NLTK Book
> NLTK：The Natural Language Toolkit 
> 
> 待讀：[NLTK Book](https://www.nltk.org/book/)

----

> note
>
> `pip jieba` 中文斷詞常用套件

- 辨識文章類型、正負向輿論(https://www.nltk.org/book/ch02.html)
- 斷詞：`tokenize`
- 詞性套件 pos tag
  - 判斷動詞
    1. pip install jieba
    2. [ckip](http://ckipsvr.iis.sinica.edu.tw/)
    3. 文字雲 word cloud
- 停用詞 stopwords 
https://zh.wikipedia.org/wiki/GPT-3

----

## Word2Vec

1. one hot
   1. 喪失前後關聯性
   2. 維度太大
2. 基於統計 
   1. 詞頻 [TF-IDF](https://zh.wikipedia.org/wiki/Tf-idf)
   2. 共現矩陣 co-occurence matrix
3. 基於預測: 資料量要夠大
   1. word embedding- 常用於文本處理
   2. [skip- gram model](https://medium.com/@pocheng0118/word2vec-from-scratch-skip-gram-cbow-98fd17385945)
   3. cbow


----
>> https://kknews.cc/zh-tw/tech/8g9lk44.html NN CNN RNN LSTM
>> 類神經網路 有權種植

## CNN
- 捲積神經
  1. 影像輸入(經常用以分析影像)
  2. 卷積、磁化、卷積、磁化、...看你要疊幾次  (取特徵的概念)
  3. 得到綠波完後的結果 (最後得到 feature map)
  4. 無前/後處理
  5. 無記憶


## RNN 遞歸神經網路
https://brohrer.mcknote.com/zh-Hant/how_machine_learning_works/how_rnns_lstm_work.html
- NLP 處理
  1. 有記憶(RNN)/無記憶(NN、CNN)神經網路的差別
    - 如：地點
        有記憶:有出發地及目的地的意義
        無記憶:僅僅只是地點
  2. 考慮前/後處理
    - 所以處理自然語言較推薦使用 RNN 而非 CNN
- 基本上就是使用 LSTM


## LSTM 長短期記憶
- 輸入閘門、遺忘閘門、輸出閘門
  - 靠參數調整控制
- 相關應用：
  1. [IMDB (Keras)](https://keras.io/api/datasets/imdb/)
  2. 聊天機器人(包含意圖理解、回覆)
- 和 GRU 類似概念，差別在於 gate 的設定不同(GRU較快)

>> NLP 有時序性問題



