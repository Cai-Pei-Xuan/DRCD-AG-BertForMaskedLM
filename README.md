# DRCD-AG-BertForMaskedLM
使用台達電的資料集做Answer Generation任務並fine-turing BertForMaskedLM

## 檔案說明
### Data
- preprocess_data.py : 將台達電的資料處理成Answer Generation需要的input
```
# input_token範例:
# C:C1C2
# Q:Q1Q2
# A:A1A2[SEP]
# 由於A有3個token(包含[SEP]，因為要預測答案何時該停下)，所以input_data有3筆
# [CLS]C1C2[sep]Q1Q2[SEP][MASK]
# [CLS]C1C2[sep]Q1Q2[SEP]A1[MASK]
# [CLS]C1C2[sep]Q1Q2[SEP]A1A2[MASK]
```
- train.py : BertForMaskedLM的訓練
- predict.py : 輸入context和question來生成答案
- requestment.txt : 紀錄需要安裝的環境
## 使用說明
### train的順序
```
python train.py         # 如果想用訓練好的model可以去release下載，並將資料放入trained_model內，就可以跳過這步驟
```
### Demo
```
python predict.py
請輸入context
此時，薩曼王朝的一個王子「納斯爾」流亡到喀喇汗國境內，奧古爾恰克為了對付薩曼王朝，便接納了他，把他安置在了阿圖什。於是，在這位流亡的薩曼王朝王子的影響下，薩圖克·博格拉汗皈依了伊斯蘭教，並取名阿卜都·卡里姆。而納斯爾王子在促使薩圖克皈依伊斯蘭教的同時，也給了他藉助伊斯蘭教的力量奪回汗位的希望。後來的事實也證明，這一做法行之有效，在與其叔父奧古爾恰克的對抗中，來自伊斯蘭世界的志願軍起了重要的作用。955年，薩圖克·博格拉汗在奪回汗位後不久即逝世於阿圖什，當地至今還有他的墳墓。他本人在世期間，並沒有其他重要的政治活動。在其子木薩繼位後，繼續推行境內突厥人的伊斯蘭化。阿拉伯史書記載：960年這一年有二十萬帳突厥人接受了伊斯蘭教。薩圖克·博格拉汗之孫哈侖·博格拉汗自八剌沙袞出征河中地區的薩曼王朝，992年攻陷其都城布哈拉，999年，他聯合今阿富汗境內的另一突厥王朝，加茲尼王朝的君主馬合木共滅薩曼王朝，從此喀喇汗國奄有阿姆河以北中亞地區。
請輸入question
「納斯爾」是哪一個王朝的王子?
答案:薩曼王朝
```
## 環境需求
- python 3.6+
- pytorch 1.3+
- transformers 2.2+
- CUDA Version: 10.0
