# YOLOv3 で物体検出チュートリアル（Mac)

参考にしたページ

https://qrunch.net/@Atom/entries/8p9CkQJmA1uhp8Qa

## 環境

macOS Catalina

Python 3.8.5

## YOLOv3ダウンロード＋インストール

まず、ホームディレクトリ直下にフォルダを作成。

例）yolo_test

以下、ホームディレクトリ直下に「yolo_test」というフォルダがある前提で進める。

YOLOv3のダウンロード方法は、２通り

1. ターミナル上でgit cloneコマンドを使用する
2. githubのページからダウンロードする

### ターミナル上でダウンロードする場合

1. ターミナルを起動後、先ほど作成したyolo_testに移動。

   ```
   cd yolo_test
   ```

   

2. 以下を入力して、ダウンロードを実行する。

   ```UNIX
   git clone https://github.com/pjreddie/darknet.git
   ```

3. cd darknetを入力して、darknetフォルダに移動

   ```
   cd darknet
   ```

4. make でビルド＋インストールを実施する

   ```
   make
   ```

### ブラウザでダウンロードする場合

[こちら](https://github.com/pjreddie/darknet)からzipファイルをダウンロード＋解凍。

フォルダの名前は「darknet-master」となっているが、中身は「darknet」と同じ。

ここでは、git cloneを使用してインストールした手順とわかりやすく合わせるため、フォルダ名を「darknet」に変更する。



Finderなど使用して、「darknet」フォルダを「yolo_test」フォルダ内に移動する。

その後、ターミナル上で「yolo_test」フォルダに移動。

```
cd yolo_test
```

cd darknetを入力して、darknetフォルダに移動

```
cd darknet
```

make でビルド＋インストールを実施する

```
make
```

### モデルデータのダウンロード

物体検知を行うため、続けて学習済みモデル(拡張子は.weights)をダウンロードする

```
curl https://pjreddie.com/media/files/yolov3.weights -O  
```

### 画像から物体検出

Finder で確認すると、darknetフォルダ内のdataフォルダには何枚かテスト用の画像が存在する。ここでは「dog.jpg」を使用して物体検出する。

```
./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg
```
使用するのはこちら
![dog](https://user-images.githubusercontent.com/68985919/91527629-13a5cb00-e941-11ea-8d92-2112c46fe9e2.jpg)


計算が開始され、結果が以下のように表示される。

```
data/dog.jpg: Predicted in 15.704717 seconds.
bicycle: 99%
truck: 92%
dog: 100%
```

これによると、bicycle, truck,dogが画像内で検出された。

結果の画像はdarknetフォルダ内に「predictions.jpg」として保存されている。

以下のコマンドで表示できる。

```
open predictions.jpg  
```
![predictions](https://user-images.githubusercontent.com/68985919/91527785-5f587480-e941-11ea-8560-29d0f2a194b1.jpg)



