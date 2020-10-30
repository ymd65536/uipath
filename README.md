
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

sVal.Replace("あ") ' True
sVal.Replace("か") ' False


```

