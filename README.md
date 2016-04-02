# stylesheet
FLOCSS, BEM, Sassを使ったマルチクラス設計、コンポーネント指向のcssです。

## スタイルガイド
Hologramを使ってスタイルガイドを生成しています。
`docs/`以下に生成されたスタイルガイドがあります。

## タスクランナー
guardはRuby版のタスクランナーです。
gulpに比べると、各種プラグインは少ないですが、充分活躍してくれています。

## 設定
以下の手順で設定します。

### 必要なもの
* direnv
* Chrome拡張機能のライブリロード（ファイルのURLへのアクセスを許可しておく）

#### 1. binディレクトリを作ります
`bundle exec`を省略できるようにするための準備です。

```
mkdir bin
```

#### 2. gemをインストールします
```
bundle install --path vendor/bundle
```

#### 3. guardを`bundle exec`なしで使えるように`binstubs`します
```
bundle binstubs guard
```

#### 4. direnvを使って.envrcを作ります
環境変数の`$EDITOR`が設定してあれば、そのエディタが開きます

```
direnv edit .
```

#### 5. .envrcに以下の内容を書きます
```
export PATH=$PWD/bin:$PATH
```

#### 6. .envrcの内容を読み込み直します
```
direnv reload
```

#### 7. guardを起動します
```
guard
```
