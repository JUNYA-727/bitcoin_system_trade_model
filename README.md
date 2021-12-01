# Description
Tensorflow LSTM､LightGBM+Optunaでモデルを作成して､2つのモデルで実際の相場でシミュレーションを行い､どちらのほうが利益が高いのか比較しました.
利益率の高い方のモデルを更に改良して実際にAPIを用いて使用したいと思います｡

# Requirement
 開発に使用したライブラリなど
 
* tensorflow 2.5.0
* TA-Lib 0.4.20
* numpy 1.19.2
* pandas 1.2.3
* matplotlib 3.4.1
* lightgbm　3.2.1

# Model Features
モデルの概要
シミュレーションの結果(横軸が時間､縦軸が儲け)
* ①TensorflowでLSTM(Long Short-Term Memory)ネットワークで買いか売りか検討するの3つの選択肢のモデル

![content1 (1)](https://user-images.githubusercontent.com/61785070/144104036-5d903780-9cbe-40d3-8a81-7de310bb4994.png)
* ②TensorflowでLSTM(Long Short-Term Memory)ネットワークで買いか売りか2つの選択肢のモデル

![content2 (1)](https://user-images.githubusercontent.com/61785070/144104060-10714013-6c31-4648-ad5e-69dc089928ef.png)
* ③LightGBMで買いか売りか検討する3つの選択肢のモデル

![content4 (1)](https://user-images.githubusercontent.com/61785070/144104086-f47ec34e-fdd2-4efc-8e91-f7c735f09415.png)
* ④LightGBMで買いか売りか2つの選択肢のモデル

![content3 (1)](https://user-images.githubusercontent.com/61785070/144104075-b2715d01-22c3-4b95-b1da-05bdac38016a.png)
* ⑤LightGBMで特徴量としてLSTMのように何個か前までの特徴量を加えて､買いか売りか検討する3つの選択肢のモデル

![content6 (1)](https://user-images.githubusercontent.com/61785070/144104102-a9fbd57f-570f-425f-9946-0873653e88cb.png)
* ⑥LightGBMで特徴量としてLSTMのように何個か前までの特徴量を加えて､買いか売りか2つの選択肢のモデル

![content5 (1)](https://user-images.githubusercontent.com/61785070/144104095-d93c50c6-0037-49e0-9642-37a2219621b0.png)

### 考察　
複雑な深層学習での学習より､決定木の勾配ブースティングでの学習の方が精度が高いということがわかった｡

特に､選択肢が3つより､2つを選択するモデルのが精度が高い｡また､Tensorflowはグラフから見てわかるように上下の波が大きいため安定性がかなり悪い｡結果としてはlightgbm+optunaで売りか買いかを学習させるモデルが一番安定性も高く､利益率が高いと予想される｡

Tensorflowの方もoptimizerやネットワークの組み方等で精度が向上すると考えることもできるが､複雑なネットワークより簡易的なアルゴリズムのほうが良いかもしれない.

# Data Informations
データはBTC/USDで15分足を使用する｡

[データの取得に使用したサイト](http://nipper.work/btc/index.php?market=bitFlyer&coin=BTCUSD&periods=900&after=1625182500&before=1637969700)

# Installation
 
Requirementで列挙したライブラリなどのインストール方法(MacOS)
```bash
pip install tensorflow 
```
```bash
brew install ta-lib
pip install TA-Lib
```
```bash
pip install numpy
```
```bash
pip install pandas
```
```bash
pip install matplotlib
```
```bash
pip install lightgbm
```


# Author
* k.junya0727@gmail.com
* 具体的な詳細であったり､質問等ございましたらご気軽に連絡ください
