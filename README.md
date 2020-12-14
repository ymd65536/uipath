
# はじめの一歩

UiPathで使える関数を調べる。  
結局のところ、何がどう使えるのかわからんので
調べることにした。  
ちなみにUiPathで利用する関数は」VB.Netをベースとする。

具体例とともに書く  

関数名、引数、戻り値を書く  
その際、データ型も書く  

アクティビティについても書く  
アクティビティはどういうときに使うかと
利用時の注意事項を書く

[UiPath 公式](https://docs.uipath.com/studio/lang-ja)

# 関数・メソッド一覧

## Split

[UiPath道場 - カンマ区切り文字列を分割する](http://www.uipath-dojo.com/purpose/string_split.html)

文字列分割の関数

Split(文字列,区切り文字) 

``` VB

Split("1,2,3",",")(0) ' 1
Split("1,2,3",",")(1) ' 2
Split("1,2,3",",")(2) ' 3

```


## Replace

文字列置換の**メソッド**  
**関数ではなくメソッド**

``` VB

' あらかじめ文字列変数sValを宣言しておく
' sVal = "あいうえお"

' 変数代入のアクティビティを利用
sVal = sVal.Replace("あ","か")

' sVal:かいうえお

```

## contains

文字列検索の**メソッド**
**関数ではなくメソッド**


``` VB

' あらかじめ文字列変数sValを宣言しておく
' sVal = "あいうえお"

sVal.contains("あ") ' True
sVal.contains("か") ' False


```

# 特殊なデータ型

## DataTable

> ザックリ言うと、表形式のデータを保存できるデータ型  
VBAでいうところの**IHTMLTableObject**に使い方が似ている。

|番号|名前|
|:---|:---|
|1|ジョン|
|2|リーナス|
|3|ジョブズ|

上記のようなDataTable型変数tblを作成した時の動きを考えると

``` VB

tbl.Rows(1)("名前") ' リーナス

tbl.Rows(1).item(1) ' リーナス

```

DataTableにヘッダ(列の説明)がない場合は参照する番号がズレる

``` VB

tbl.Rows(1).item(2)' リーナス

```

また、テーブルオブジェクトは意図して生成するか  
画面上、Excelなどから取得してオブジェクトを生成しなければならない。

オブジェクトを生成しなければならない理由としては  
スキーマ、列の定義が必要だからだと思われる。

データの追加、削除をデータテーブルに対して行う場合はアクティブを通して実行する必要がある。


# シナリオをより速く作るには

## アクティビティパターンを知ること
UIに対応するアクティビティを知る。  
例えば、実際に経験したことで  
OracleFormはSetTextアクティビティではなく  
TypeIntoアクティビティを使わないと
文字列を入力できない。 

## アクティビティの仕様を知ること
例えば、SetVisibleTextを使う場合は  
画面上に表示された文字列を取得するので  
事前に画面の最大化などをして画面表示の担保する必要がある。

## メタデータのことは後から考えること
利用するデータのデータ設計は必要だが  
それを最初に持ってくると効率化悪いので  
とりあえず、作ってみる。  
このときに重要なことは
メタデータをアクティビティに直接書かず  
変数で定義してからアクティビティに入れる。  
そして、変数の既定値にテスト用のメタデータを設定する。


## 同じサブシナリオを作らないこと
よくある動作はどこでも使えるので  
ライブラリ化することで再利用できる？？  

アクティビティに引数を渡すように作る。
例えば  
ブラウザの名前をつけて保存の場合は  
ファイルのフルパスを与える作りでライブラリ化することで
使いまわせるのでは

