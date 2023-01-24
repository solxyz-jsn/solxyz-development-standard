# フォーマッター設定

## 目次

  - [インデント](#インデント)
    - [タブポリシー](#タブポリシー)
    - [折り返しされた行のインデントにスペースを使用](#折り返しされた行のインデントにスペースを使用)
    - [インデントサイズ](#インデントサイズ)
    - [タブサイズ](#タブサイズ)
    - [テキストブロックのインデント](#テキストブロックのインデント)
    - [インデントされる要素](#インデントされる要素)
      - [クラス本文内の宣言](#クラス本文内の宣言)
      - [列挙型宣言内の宣言](#列挙型宣言内の宣言)
      - [列挙型定数内の宣言](#列挙型定数内の宣言)
      - [注釈宣言内の宣言](#注釈宣言内の宣言)
      - [レコード宣言内の宣言](#レコード宣言内の宣言)
      - [メソッド/コンストラクター内のステートメント](#メソッドコンストラクター内のステートメント)
      - [ブロック内のステートメント](#ブロック内のステートメント)
      - [switch本文内のステートメント](#switch本文内のステートメント)
      - [case本文内のステートメント](#case本文内のステートメント)
      - [breakステートメント](#breakステートメント)
      - [空行](#空行)
    - [列の項目配置](#列の項目配置)
      - [フィールド宣言](#フィールド宣言)
      - [変数宣言](#変数宣言)
      - [割り当てステートメント](#割り当てステートメント)
      - [位置合わせにスペースを使用](#位置合わせにスペースを使用)
      - [独立したグループを分離するブランク行](#独立したグループを分離するブランク行)
  - [波括弧の位置](#波括弧の位置)
    - [クラスまたはインターフェース宣言](#クラスまたはインターフェース宣言)
    - [匿名クラス宣言](#匿名クラス宣言)
    - [コンストラクター宣言](#コンストラクター宣言)
    - [メソッド宣言](#メソッド宣言)
    - [列挙宣言](#列挙宣言)
    - [列挙定数本文](#列挙定数本文)
    - [レコード宣言](#レコード宣言)
    - [レコードコンストラクター](#レコードコンストラクター)
    - [注釈型宣言](#注釈型宣言)
    - [ブロック](#ブロック)
    - [caseステートメント内のブロック](#caseステートメント内のブロック)
    - [switchステートメント](#switchステートメント)
    - [配列初期化子](#配列初期化子)
    - [空の配列初期化子を1行に保持](#空の配列初期化子を1行に保持)
    - [ラムダ本文](#ラムダ本文)
  - [丸括弧の位置](#丸括弧の位置)
    - [メソッド/コンストラクター宣言](#メソッドコンストラクター宣言)
    - [メソッド/コンストラクター呼び出し](#メソッドコンストラクター呼び出し)
    - [列挙定数宣言](#列挙定数宣言)
    - [レコード宣言](#レコード宣言-1)
    - [注釈](#注釈)
    - [ラムダ宣言](#ラムダ宣言)
    - [if, while および do while ステートメント](#if-while-および-do-while-ステートメント)
    - [for ステートメント](#for-ステートメント)
    - [switchステートメント](#switchステートメント-1)
    - [try文節](#try文節)
    - [catch文節](#catch文節)
  - [空白](#空白)
    - [宣言](#宣言)
      - [クラス](#クラス)
        - [クラスの左波括弧の前](#クラスの左波括弧の前)
        - [匿名クラスの左波括弧の前](#匿名クラスの左波括弧の前)
        - [implement節内のコンマの前](#implement節内のコンマの前)
        - [implement節内のコンマの後](#implement節内のコンマの後)
        - [permits節内のコンマの前](#permits節内のコンマの前)
        - [permits節内のコンマの後](#permits節内のコンマの後)
      - [フィールド](#フィールド)
        - [複数フィールド宣言内のコンマの前](#複数フィールド宣言内のコンマの前)
        - [複数フィールド宣言内のコンマの後](#複数フィールド宣言内のコンマの後)
      - [ローカル変数](#ローカル変数)
        - [複数ローカル宣言内のコンマの前](#複数ローカル宣言内のコンマの前)
        - [複数ローカル宣言内のコンマの後](#複数ローカル宣言内のコンマの後)
      - [コンストラクター](#コンストラクター)
        - [左丸括弧の前](#左丸括弧の前)
        - [左丸括弧の後](#左丸括弧の後)
        - [右丸括弧の前](#右丸括弧の前)
        - [空の丸括弧の間](#空の丸括弧の間)
        - [左波括弧の前](#左波括弧の前)
        - [パラメータ内のコンマの前](#パラメータ内のコンマの前)
        - [パラメータ内のコンマの後](#パラメータ内のコンマの後)
        - ['throws'節内のコンマの前](#throws節内のコンマの前)
        - ['throws'節内のコンマの後](#throws節内のコンマの後)
      - [メソッド](#メソッド)
        - [左丸括弧の前](#左丸括弧の前-1)
        - [左丸括弧の後](#左丸括弧の後-1)
        - [右丸括弧の前](#右丸括弧の前-1)
        - [空の丸括弧の間](#空の丸括弧の間-1)
        - [左波括弧の前](#左波括弧の前-1)
        - [パラメータ内のコンマの前](#パラメータ内のコンマの前-1)
        - [パラメータ内のコンマの後](#パラメータ内のコンマの後-1)
        - [可変引数パラメータ内の省略符号の前](#可変引数パラメータ内の省略符号の前)
        - [可変引数パラメータ内の省略符号の後](#可変引数パラメータ内の省略符号の後)
        - ['throws'節内のコンマの前](#throws節内のコンマの前-1)
        - ['throws'節内のコンマの後](#throws節内のコンマの後-1)
      - [ラベル](#ラベル)
        - [コロンの前](#コロンの前)
        - [コロンの後](#コロンの後)
      - [注釈](#注釈-1)
        - [@の後](#の後)
        - [左丸括弧の前](#左丸括弧の前-2)
        - [左丸括弧の後](#左丸括弧の後-2)
        - [コンマの前](#コンマの前)
        - [コンマの後](#コンマの後)
        - [右丸括弧の前](#右丸括弧の前-2)
      - [列挙型（Enum）](#列挙型enum)
        - [宣言の左波括弧の前](#宣言の左波括弧の前)
        - [定数間のコンマの前](#定数間のコンマの前)
        - [定数間のコンマの後](#定数間のコンマの後)
        - [定数引数の左丸括弧の前](#定数引数の左丸括弧の前)
        - [定数引数の左丸括弧の後](#定数引数の左丸括弧の後)
        - [定数引数の空の丸括弧の間](#定数引数の空の丸括弧の間)
        - [定数引数のコンマの前](#定数引数のコンマの前)
        - [定数引数のコンマの後](#定数引数のコンマの後)
        - [定数引数の右丸括弧の前](#定数引数の右丸括弧の前)
        - [定数本文の左波括弧の前](#定数本文の左波括弧の前)
      - [注釈型](#注釈型)
        - [@の前](#の前)
        - [@の後](#の後-1)
        - [左波括弧の前](#左波括弧の前-2)
        - [注釈型メンバーの左丸括弧の前](#注釈型メンバーの左丸括弧の前)
        - [注釈型メンバーの丸括弧の間](#注釈型メンバーの丸括弧の間)
      - [レコード](#レコード)
        - [左丸括弧の前](#左丸括弧の前-3)
        - [左丸括弧の後](#左丸括弧の後-3)
        - [レコード・コンポーネントのコンマの前](#レコードコンポーネントのコンマの前)
        - [レコード・コンポーネントのコンマの後](#レコードコンポーネントのコンマの後)
        - [右丸括弧の前](#右丸括弧の前-3)
        - [宣言の左波括弧の前](#宣言の左波括弧の前-1)
        - [レコード・コンストラクターの左波括弧の前](#レコードコンストラクターの左波括弧の前)
      - [ラムダ](#ラムダ)
        - [矢印演算子の前](#矢印演算子の前)
        - [矢印演算子の後](#矢印演算子の後)
    - [制御ステートメント](#制御ステートメント)
      - [ブロック](#ブロック-1)
        - [左波括弧の前](#左波括弧の前-3)
        - [右波括弧の後](#右波括弧の後)
      - [if else](#if-else)
        - [左丸括弧の前](#左丸括弧の前-4)
        - [左丸括弧の後](#左丸括弧の後-4)
        - [右丸括弧の前](#右丸括弧の前-4)
      - [for](#for)
        - [左丸括弧の前](#左丸括弧の前-5)
        - [左丸括弧の後](#左丸括弧の後-5)
        - [右丸括弧の前](#右丸括弧の前-5)
        - [初期化内のコンマの前](#初期化内のコンマの前)
        - [初期化内のコンマの後](#初期化内のコンマの後)
        - [インクリメント内のコンマの前](#インクリメント内のコンマの前)
        - [インクリメント内のコンマの後](#インクリメント内のコンマの後)
        - [セミコロンの前](#セミコロンの前)
        - [セミコロンの後](#セミコロンの後)
        - [コロンの前](#コロンの前-1)
        - [コロンの後](#コロンの後-1)
      - [switch](#switch)
        - [case内のコロンの前](#case内のコロンの前)
        - [default内のコロンの前](#default内のコロンの前)
        - [caseの矢印の前](#caseの矢印の前)
        - [caseの矢印の後](#caseの矢印の後)
        - [defaultの矢印の前](#defaultの矢印の前)
        - [defaultの矢印の後](#defaultの矢印の後)
        - [case式のコンマの前](#case式のコンマの前)
        - [case式のコンマの前](#case式のコンマの前-1)
        - [左丸括弧の前](#左丸括弧の前-6)
        - [左丸括弧の後](#左丸括弧の後-6)
        - [右丸括弧の前](#右丸括弧の前-6)
        - [左波括弧の前](#左波括弧の前-4)
      - [whileおよびdo while](#whileおよびdo-while)
        - [左丸括弧の前](#左丸括弧の前-7)
        - [左丸括弧の後](#左丸括弧の後-7)
        - [右丸括弧の前](#右丸括弧の前-7)
      - [synchronized](#synchronized)
        - [左丸括弧の前](#左丸括弧の前-8)
        - [左丸括弧の後](#左丸括弧の後-8)
        - [右丸括弧の前](#右丸括弧の前-8)
      - [try-with-resources](#try-with-resources)
        - [左丸括弧の前](#左丸括弧の前-9)
        - [左丸括弧の後](#左丸括弧の後-9)
        - [セミコロンの前](#セミコロンの前-1)
        - [セミコロンの後](#セミコロンの後-1)
        - [右丸括弧の前](#右丸括弧の前-9)
      - [catch](#catch)
        - [左丸括弧の前](#左丸括弧の前-10)
        - [左丸括弧の後](#左丸括弧の後-10)
        - [右丸括弧の後](#右丸括弧の後)
      - [assert](#assert)
        - [コロンの前](#コロンの前-2)
        - [コロンの後](#コロンの後-2)
      - [return](#return)
        - [括弧で囲まれた式の前](#括弧で囲まれた式の前)
      - [throw](#throw)
        - [括弧で囲まれた式の前](#括弧で囲まれた式の前-1)
      - [セミコロンの前](#セミコロンの前-2)
    - [式](#式)
      - [関数呼び出し](#関数呼び出し)
        - [左丸括弧の前](#左丸括弧の前-11)
        - [左丸括弧の後](#左丸括弧の後-11)
        - [右丸括弧の後](#右丸括弧の後-1)
        - [空の丸括弧の間](#空の丸括弧の間-2)
        - [メソッド引数内のコンマの前](#メソッド引数内のコンマの前)
        - [メソッド引数内のコンマの後](#メソッド引数内のコンマの後)
        - [オブジェクト割り振り引数内のコンマの前](#オブジェクト割り振り引数内のコンマの前)
        - [オブジェクト割り振り引数内のコンマの後](#オブジェクト割り振り引数内のコンマの後)
        - [明示的コンストラクター呼び出し内のコンマの前](#明示的コンストラクター呼び出し内のコンマの前)
        - [明示的コンストラクター呼び出し内のコンマの後](#明示的コンストラクター呼び出し内のコンマの後)
      - [単項演算子](#単項演算子)
        - [後置演算子の前](#後置演算子の前)
        - [後置演算子の後](#後置演算子の後)
        - [接頭演算子の前](#接頭演算子の前)
        - [接頭演算子の前](#接頭演算子の前-1)
        - [単項演算子の前](#単項演算子の前)
        - [単項演算子の後](#単項演算子の後)
        - [否定演算子の後](#否定演算子の後)
      - [2項演算子](#2項演算子)
        - [乗法演算子の前](#乗法演算子の前)
        - [乗法演算子の後](#乗法演算子の後)
        - [加法演算子の前](#加法演算子の前)
        - [加法演算子の後](#加法演算子の後)
        - [文字列連結演算子の前](#文字列連結演算子の前)
        - [文字列連結演算子の後](#文字列連結演算子の後)
        - [シフト演算子の前](#シフト演算子の前)
        - [シフト演算子の後](#シフト演算子の後)
        - [関係演算子の前](#関係演算子の前)
        - [関係演算子の後](#関係演算子の後)
        - [ビット演算子の前](#ビット演算子の前)
        - [ビット演算子の後](#ビット演算子の後)
        - [論理演算子の前](#論理演算子の前)
        - [論理演算子の後](#論理演算子の後)
      - [条件](#条件)
        - [疑問符の前](#疑問符の前)
        - [疑問符の後](#疑問符の後)
        - [コロンの前](#コロンの前-3)
        - [コロンの後](#コロンの後-3)
      - [歳入](#歳入)
        - [代入演算子の前](#代入演算子の前)
        - [代入演算子の前](#代入演算子の前-1)
      - [括弧で囲まれた式](#括弧で囲まれた式)
        - [左丸括弧の前](#左丸括弧の前-12)
        - [左丸括弧の後](#左丸括弧の後-12)
        - [右丸括弧の前](#右丸括弧の前-10)
      - [型キャスト](#型キャスト)
        - [左丸括弧の後](#左丸括弧の後-13)
        - [左丸括弧の後](#左丸括弧の後-14)
        - [左丸括弧の後](#左丸括弧の後-15)
    - [配列](#配列)
      - [配列宣言](#配列宣言)
        - [左角括弧の前](#左角括弧の前)
        - [空の角括弧の間](#空の角括弧の間)
      - [配列割り振り](#配列割り振り)
        - [左角括弧の前](#左角括弧の前-1)
        - [左角括弧の後](#左角括弧の後)
        - [右角括弧の前](#右角括弧の前)
        - [空の角括弧の間](#空の角括弧の間-1)
      - [配列初期化子](#配列初期化子-1)
        - [左波括弧の前](#左波括弧の前-5)
        - [左波括弧の後](#左波括弧の後)
        - [右波括弧の後](#右波括弧の後-1)
        - [コンマの前](#コンマの前-1)
        - [コンマの後](#コンマの後-1)
        - [空の波括弧の間](#空の波括弧の間)
      - [配列要素アクセス](#配列要素アクセス)
        - [左角括弧の前](#左角括弧の前-2)
        - [左角括弧の後](#左角括弧の後-1)
        - [右角括弧の前](#右角括弧の前-1)
    - [パラメータ化された型](#パラメータ化された型)
      - [型参照](#型参照)
        - [左山括弧の前](#左山括弧の前)
        - [左山括弧の後](#左山括弧の後)
        - [コンマの前](#コンマの前-2)
        - [コンマの後](#コンマの後-2)
        - [右山括弧の前](#右山括弧の前)
      - [型引数](#型引数)
        - [左山括弧の前](#左山括弧の前-1)
        - [左山括弧の後](#左山括弧の後-1)
        - [コンマの前](#コンマの前-3)
        - [コンマの後](#コンマの後-3)
        - [右山括弧の前](#右山括弧の前-1)
        - [右山括弧の後](#右山括弧の後)
      - [型パラメータ](#型パラメータ)
        - [左山括弧の前](#左山括弧の前-2)
        - [左山括弧の後](#左山括弧の後-2)
        - [パラメータ内のコンマの前](#パラメータ内のコンマの前-2)
        - [パラメータ内のコンマの後](#パラメータ内のコンマの後-2)
        - [右山括弧の前](#右山括弧の前-2)
        - [右山括弧の後](#右山括弧の後-1)
        - [型制約'&'の前](#型制約の前)
        - [型制約'&'の後](#型制約の後)
      - [ワイルドカード型](#ワイルドカード型)
        - [疑問符の前](#疑問符の前-1)
        - [疑問符の前](#疑問符の前-2)
  - [ブランク行](#ブランク行)
    - [設定方法](#設定方法)
    - [設定値](#設定値)
    - [保持する空き行数](#保持する空き行数)
    - [コンパイル単位内のブランク行](#コンパイル単位内のブランク行)
      - [パッケージ宣言の前](#パッケージ宣言の前)
      - [パッケージ宣言の後](#パッケージ宣言の後)
      - [インポート宣言の前](#インポート宣言の前)
      - [インポート・グループの間](#インポートグループの間)
      - [インポート宣言の後](#インポート宣言の後)
      - [クラス宣言の間](#クラス宣言の間)
    - [型宣言内のブランク行](#型宣言内のブランク行)
      - [最初のメンバー宣言の前](#最初のメンバー宣言の前)
      - [最初のメンバー宣言の後](#最初のメンバー宣言の後)
      - [異なる種類のメンバー宣言の間](#異なる種類のメンバー宣言の間)
      - [メンバー型宣言の間](#メンバー型宣言の間)
      - [フィールド宣言の間](#フィールド宣言の間)
      - [抽象メソッド宣言の間](#抽象メソッド宣言の間)
      - [メソッド/コンストラクター宣言の間](#メソッドコンストラクター宣言の間)
    - [メソッド/コンストラクター宣言内のブランク行](#メソッドコンストラクター宣言内のブランク行)
      - [メソッド/コンストラクター本体の先頭](#メソッドコンストラクター本体の先頭)
      - [メソッド/コンストラクター本体の最後](#メソッドコンストラクター本体の最後)
      - [コード・ブロックの開始](#コードブロックの開始)
      - [コード・ブロックの最後](#コードブロックの最後)
      - [コード・ブロックを含むステートメントの前](#コードブロックを含むステートメントの前)
      - [コード・ブロックを含むステートメントの後](#コードブロックを含むステートメントの後)
      - [switchステートメント・グループの間](#switchステートメントグループの間)
  - [改行](#改行)
    - [空ステートメントの前](#空ステートメントの前)
    - [配列初期化子の左波括弧の後](#配列初期化子の左波括弧の後)
    - [配列初期化子の右波括弧の前](#配列初期化子の右波括弧の前)
    - [ファイルの最後](#ファイルの最後)
    - [制御文内](#制御文内)
      - ['if'文の'else'の前](#if文のelseの前)
      - ['try'ステートメントの'catch'の前](#tryステートメントのcatchの前)
      - ['try'ステートメントの'finally'の前](#tryステートメントのfinallyの前)
      - ['do'ステートメントの'while'の前](#doステートメントのwhileの前)
      - [ラベルの後](#ラベルの後)
      - [if else](#if-else-1)
        - ['then'ステートメントを同じ行に保持](#thenステートメントを同じ行に保持)
        - [単純'if'を1行に保持](#単純ifを1行に保持)
        - ['else'ステートメントを同じ行に保持](#elseステートメントを同じ行に保持)
        - ['else if'を1行に保持](#else-ifを1行に保持)
      - [単純なループ](#単純なループ)
        - [単純な'for'ループ本体を同じ行に保持する](#単純なforループ本体を同じ行に保持する)
        - [単純な'while'ループ本体を同じ行に保持する](#単純なwhileループ本体を同じ行に保持する)
        - [単純な'do while'ループ本体を同じ行に保持する](#単純なdo-whileループ本体を同じ行に保持する)
    - [注釈の後](#注釈の後)
      - [パッケージ](#パッケージ)
      - [型](#型)
      - [enum定数](#enum定数)
      - [フィールド](#フィールド-1)
      - [メソッド](#メソッド-1)
      - [ローカル変数](#ローカル変数-1)
      - [パラメータ](#パラメータ)
      - [型注釈](#型注釈)
    - [波括弧を1行のコードに保持](#波括弧を1行のコードに保持)
      - [ループ本体（'for', 'while', 'do while'）](#ループ本体for-while-do-while)
      - ['if then'ステートメント本体](#if-thenステートメント本体)
      - ['return'または'throw'文節を1行に保持](#returnまたはthrow文節を1行に保持)
      - [ラムダ本文](#ラムダ本文-1)
      - [矢印付きの switch case](#矢印付きの-switch-case)
      - [矢印付きの式/ステートメント](#矢印付きの式ステートメント)
      - [ステートメント内の他のコード・ブロック](#ステートメント内の他のコードブロック)
      - [メソッド宣言](#メソッド宣言-1)
      - [単純なgetterとsetterを1行にまとめる](#単純なgetterとsetterを1行にまとめる)
      - [クラス宣言](#クラス宣言)
      - [匿名クラス宣言](#匿名クラス宣言-1)
      - [列挙宣言](#列挙宣言-1)
      - [列挙定数宣言](#列挙定数宣言-1)
      - [レコード宣言](#レコード宣言-2)
      - [レコード・コンストラクター宣言](#レコードコンストラクター宣言)
      - [注釈宣言](#注釈宣言)
  - [行折り返し](#行折り返し)
    - [ルートの設定項目](#ルートの設定項目)
      - [行の最大幅](#行の最大幅)
      - [折り返しされた行のデフォルト・インデント](#折り返しされた行のデフォルトインデント)
      - [配列初期化子のデフォルト・インデント](#配列初期化子のデフォルトインデント)
      - [すでに折り返された行を結合しない](#すでに折り返された行を結合しない)
      - [外側の式を（ネストされた式を1行に保持）折り返す](#外側の式をネストされた式を1行に保持折り返す)
    - [折り返し設定](#折り返し設定)
      - [折り返しをする条件](#折り返しをする条件)
      - [強制分割の有無](#強制分割の有無)
      - [折り返し時のインデント](#折り返し時のインデント)
    - [クラス宣言](#クラス宣言-1)
      - ['extends'文節](#extends文節)
      - ['implements'文節](#implements文節)
    - [コンストラクター宣言](#コンストラクター宣言-1)
      - [パラメータ](#パラメータ-1)
      - ['throws'文節](#throws文節)
    - [メソッド宣言](#メソッド宣言-2)
      - [宣言](#宣言-1)
      - [パラメータ](#パラメータ-2)
      - ['throws'文節](#throws文節-1)
    - [enum宣言](#enum宣言)
      - [定数](#定数)
      - ['implements'文節](#implements文節-1)
      - [定数引数](#定数引数)
    - [レコード宣言](#レコード宣言-3)
      - [レコード・コンポーネント](#レコードコンポーネント)
      - ['implements'文節](#implements文節-2)
    - [関数呼び出し](#関数呼び出し-1)
      - [引数](#引数)
      - [修飾呼び出し](#修飾呼び出し)
      - [ベースとなる式の最初の行からインデントする](#ベースとなる式の最初の行からインデントする)
      - [明示的コンストラクター呼び出し](#明示的コンストラクター呼び出し)
      - [オブジェクト割り振り引数](#オブジェクト割り振り引数)
      - [修飾オブジェクト割り振り引数](#修飾オブジェクト割り振り引数)
    - [二進式](#二進式)
      - [乗法演算子（*、/、%）](#乗法演算子)
      - [加法演算子（+、-）](#加法演算子-)
      - [文字列連結](#文字列連結)
      - [シフト演算子（<<、>>、>>>）](#シフト演算子)
      - [比較演算子（<, >, <=, >=, ==, !=）](#比較演算子-----)
      - [ビット演算子](#ビット演算子)
      - [論理演算子](#論理演算子)
    - [その他の式](#その他の式)
      - [条件](#条件-1)
      - [連鎖条件](#連鎖条件)
      - [代入](#代入)
      - [配列初期化子](#配列初期化子-2)
    - [ステートメント](#ステートメント)
      - ['for'](#for-1)
      - ['if else'のコンパクト化](#if-elseのコンパクト化)
      - [ループのコンパクト化](#ループのコンパクト化)
      - ['try-with-resources'](#try-with-resources-1)
      - ['multi-catch'](#multi-catch)
      - [矢印付きの 'switch' case](#矢印付きの-switch-case-1)
      - [矢印付きの 'switch' case式](#矢印付きの-switch-case式)
      - [コロン付きの 'switch' case式](#コロン付きの-switch-case式)
      - ['assert' メッセージ](#assert-メッセージ)
    - [パラメータ化された型](#パラメータ化された型-1)
      - [型参照](#型参照-1)
      - [型引数](#型引数-1)
      - [型パラメータ](#型パラメータ-1)
    - [注釈](#注釈-2)
      - [パッケージ](#パッケージ-1)
      - [型](#型-1)
      - [enum定数](#enum定数-1)
      - [フィールド](#フィールド-2)
      - [メソッド](#メソッド-2)
      - [ローカル変数](#ローカル変数-2)
      - [パラメータ](#パラメータ-3)
      - [型注釈](#型注釈-1)
      - [要素-値ペア](#要素-値ペア)
    - [モジュール記述](#モジュール記述)
      - [モジュール・ステートメント](#モジュールステートメント)
  - [コメント](#コメント)
    - [コメントの最大幅](#コメントの最大幅)
      - [コメント開始位置から幅をカウントする](#コメント開始位置から幅をカウントする)
      - [Javadocコメント・フォーマットを使用可能にする](#javadocコメントフォーマットを使用可能にする)
      - [ブロックコメント・フォーマット](#ブロックコメントフォーマット)
      - [行コメント・フォーマットを使用可能にする](#行コメントフォーマットを使用可能にする)
      - [最初の列で行コメントをフォーマット](#最初の列で行コメントをフォーマット)
      - [ヘッダー・コメント・フォーマットを使用可能にする](#ヘッダーコメントフォーマットを使用可能にする)
      - [コードと行コメントの間の空白を保持する](#コードと行コメントの間の空白を保持する)
      - [最初の列で行コメントをインデントしない](#最初の列で行コメントをインデントしない)
      - [最初の列でブロック・コメントをインデントしない](#最初の列でブロックコメントをインデントしない)
      - [行を結合しない](#行を結合しない)
    - [Javadoc](#javadoc)
      - [HTMLタグをフォーマット](#htmlタグをフォーマット)
      - ['pre'タグ内のJavaコード・スニペットをフォーマット](#preタグ内のjavaコードスニペットをフォーマット)
      - [Javadicタグの前のブランク行](#javadicタグの前のブランク行)
      - [異なるタイプのタグ間のブランク行](#異なるタイプのタグ間のブランク行)
      - [カラムでJavadocタグを整列](#カラムでjavadocタグを整列)
      - [@param/@throwsの説明の前で改行する](#paramthrowsの説明の前で改行する)
      - [折り返された@param/@throwsをインデントする](#折り返されたparamthrowsをインデントする)
      - [折り返すときに他のタグの説明をインデントする](#折り返すときに他のタグの説明をインデントする)
      - [/** および */ を別の行にする](#-および--を別の行にする)
      - [ブランク行を除去](#ブランク行を除去)
    - [ブロック・コメント](#ブロックコメント)
      - [/* および */ を別の行にする](#-および--を別の行にする-1)
      - [ブランク行を除去](#ブランク行を除去-1)
  - [off/onタグ](#offonタグ)
    - [off/onタグを使用可能にする](#offonタグを使用可能にする)
    - [offタグ](#offタグ)
    - [onタグ](#onタグ)

## インデント

インデントに関する設定です。

インデントの方式、インデントする項目について設定します。

### タブポリシー

`<setting id="org.eclipse.jdt.core.formatter.tabulation.char"/>`

インデント文字についての設定です。タブ/空白/混合のいずれかが選択可能です。

|value|意味|
|--|--|
|space|スペースのみ|
|tab|タブのみ|
|mixed|混合|

### 折り返しされた行のインデントにスペースを使用

`<setting id="org.eclipse.jdt.core.formatter.use_tabs_only_for_leading_indentations"/>`

行の最大文字数を超えて折り返した際、折り返し後のインデントにスペースを使用するか選択できます。

※タブポリシーが`space`の場合は選択不可

|value|意味|
|--|--|
|true|スペースを使用する|
|false|スペースを使用しない|

### インデントサイズ

`<setting id="org.eclipse.jdt.core.formatter.indentation.size"/>`

スペースいくつでインデントを表現するかを設定します。

※タブポリシーが`tab`の場合は選択不可

### タブサイズ

`<setting id="org.eclipse.jdt.core.formatter.tabulation.size"/>`

エディター上でタブがスペースいくつ分となるかを設定します。

文字列内のタブなども対象です。

### テキストブロックのインデント

`<setting id="org.eclipse.jdt.core.formatter.text_block_indentation"/>`

|value|GUIでの設定値|意味|
|--|--|--|
|3|何もしない|インデントなし|
|2|1つごとにインデント|宣言行からひとつ下げてインデントする|
|0|行折り返しのデフォルト|行折り返し時のインデント位置までインデントする|
|1|列でインデント|宣言時の`"""`と揃えるようにインデントする|

何もしない
```java
    String textBlock = """
first line

second line
""";
```

1つごとにインデント
```java
    String textBlock = """
        first line

        second line
        """;
```

行折り返しのデフォルト（※行折り返し設定に準ずる）
```java
    String textBlock = """
            first line

            second line
            """;
```

列でインデント
```java
    String textBlock = """
                       first line

                       second line
                       """;
```

### インデントされる要素

#### クラス本文内の宣言

`<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_type_header"/>`

クラス内の宣言をインデントするか選択します。

#### 列挙型宣言内の宣言

`<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_enum_declaration_header"/>`

`enum`宣言内の宣言をインデントするか選択します。

#### 列挙型定数内の宣言

`<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_enum_constant_header"/>`

`enum`定数宣言内でインデントするか選択します。

#### 注釈宣言内の宣言

`<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_annotation_declaration_header"/>`

自作アノテーションの宣言内の宣言をインデントするか選択します。

#### レコード宣言内の宣言

`<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_record_header"/>`

レコード宣言内のコンストラクターやメソッドをインデントするか選択します。

#### メソッド/コンストラクター内のステートメント

`<setting id="org.eclipse.jdt.core.formatter.indent_statements_compare_to_body"/>`

メソッドおよびコンストラクター内のステートメントをインデントするか選択します。

#### ブロック内のステートメント

`<setting id="org.eclipse.jdt.core.formatter.indent_statements_compare_to_block"/>`

`if`や`for`など、`{}`で囲まれたブロックをインデントします。

#### switch本文内のステートメント

`<setting id="org.eclipse.jdt.core.formatter.indent_switchstatements_compare_to_switch"/>`

`switch`本文内の宣言に対してインデントします。

#### case本文内のステートメント

`<setting id="org.eclipse.jdt.core.formatter.indent_switchstatements_compare_to_cases"/>`

`case`本文内の宣言/処理に対してインデントします。

#### breakステートメント

`<setting id="org.eclipse.jdt.core.formatter.indent_breaks_compare_to_cases"/>`

`break`宣言をインデントします。

#### 空行

`<setting id="org.eclipse.jdt.core.formatter.indent_empty_lines"/>`

ブランク行をインデントします。

### 列の項目配置

#### フィールド宣言

`<setting id="org.eclipse.jdt.core.formatter.align_type_members_on_columns"/>`

フィールド宣言の各要素の開始位置が揃うようにインデントします。

`true`の場合
```java
    int[]  myArray        = { 1, 2, 3,
            4, 5, 6 };
    String stringWithTabs = "1	2	3	4";
    String textBlock      = """
            first line

            second line
            """;
```

`false`の場合
```java
    int[] myArray = { 1, 2, 3, 4, 5,
            6 };
    String stringWithTabs = "1	2	3	4";
    String textBlock = """
            first line

            second line
            """;
```

#### 変数宣言

`<setting id="org.eclipse.jdt.core.formatter.align_variable_declarations_on_columns"/>`

ローカル変数宣言の各要素の開始位置が揃うようにインデントします。

`true`の場合
```java
        int          i         = 0;
        String       str       = "123456";
        Object       object    = null;
```

`false`の場合
```java
        int i = 0;
        String str = "123456";
        Object object = null;
```

#### 割り当てステートメント

`<setting id="org.eclipse.jdt.core.formatter.align_assignment_statements_on_columns"/>`

変数への代入時、各要素の開始位置が揃うようにインデントします。

`true`の場合
```java
    str     = i + str;
    object  = Arrays.asList(str);
    i      += 2;
```

`false`の場合
```java
    str = i + str;
    object = Arrays.asList(str);
    i += 2;
```

#### 位置合わせにスペースを使用

`<setting id="org.eclipse.jdt.core.formatter.align_with_spaces"/>`

各宣言の位置合わせをする際に、タブ/空白のどちらを使用するか選択します。

なお、タブポリシーが「空白のみ」の場合は設定できません。

`true`の場合：空白を使用します

`false`の場合：タブを使用します

#### 独立したグループを分離するブランク行

`<setting id="org.eclipse.jdt.core.formatter.align_fields_grouping_blank_lines"/>`

位置合わせ時に、ブランク行で分離されたグループを同じ位置とするか設定します。

`0`の場合：ブランク行を挟んでも同じグループとみなし、位置合わせをします。

`1`以上の場合：ブランク行が挿入されている場合は別のグループとみなし、グループ内での位置合わせのみ行います。

## 波括弧の位置

波括弧`{}`の位置についての設定です。

設定値は次のとおりです。

|value|GUIでの設定値|意味|
|--|--|--|
|end_of_line|同じ行|波括弧を同じ行に配置する|
|next_line|次の行|波括弧を次の行に配置する|
|next_line_shifted|インデントされた次の行|波括弧を次の行に配置し、ブロックごとインデントする|
|next_line_on_wrap|次の折り返し行|波括弧前の宣言で折り返しが発生した場合は次の行に配置する|

end_of_line

```java
interface Empty {
}
class Example{
}
```

next_line

```java
interface Empty 
{
}
class Example
{
}
```

next_line_shifted

```java
interface Empty 
    {
    }
class Example
    {
    }
```

### クラスまたはインターフェース宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_type_declaration"/>`

クラスまたはインターフェース宣言の波括弧の位置を指定します。

### 匿名クラス宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_anonymous_type_declaration"/>`

匿名クラスの波括弧の位置を指定します。

### コンストラクター宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_constructor_declaration"/>`

コンストラクター宣言の波括弧の位置を指定します。

### メソッド宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_method_declaration"/>`

メソッド宣言の波括弧の位置を指定します。

### 列挙宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_enum_declaration"/>`

enum宣言の波括弧の位置を指定します。

### 列挙定数本文

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_enum_constant"/>`

enum定数宣言の波括弧の位置を指定します。

### レコード宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_record_declaration"/>`

レコード宣言の波括弧の位置を指定します。

### レコードコンストラクター

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_record_constructor"/>`

レコードコンストラクター宣言の波括弧の位置を指定します。

### 注釈型宣言

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_annotation_type_declaration"/>`

注釈型宣言の波括弧の位置を指定します。

### ブロック

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_block"/>`

`for`, `if`, `try`などブロックの波括弧の位置を指定します。

### caseステートメント内のブロック

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_block_in_case"/>`

`case`内ブロックの波括弧の位置を指定します。

### switchステートメント

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_switch"/>`

`switch`内ブロックの波括弧の位置を指定します。

### 配列初期化子

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_array_initializer"/>`

配列初期化子の波括弧の位置を指定します。

### 空の配列初期化子を1行に保持

`<setting id="org.eclipse.jdt.core.formatter.keep_empty_array_initializer_on_one_line"/>`

空の配列初期化子を1行に保持します。配列初期化子の設定が「同じ行」となっている場合は本項目を設定できません。

サンプルコードは、配列初期化子の設定を「次の行」としています。

`true`の場合
```java
class Example {
    int[] emptyArray = new int[] {};
}
```

`false`の場合
```java
class Example {
    int[] emptyArray = new int[] 
    {};
}
```

### ラムダ本文

`<setting id="org.eclipse.jdt.core.formatter.brace_position_for_lambda_body"/>`

ラムダ式本文の波括弧の位置を指定します。

## 丸括弧の位置

丸括弧`()`についての設定です。

設定値は次のとおりです。

|value|GUIでの設定値|意味|
|--|--|--|
|common_lines|コンテンツと同じ行|括弧直前の宣言と同じ行に括弧を配置|
|separate_lines_if_wrapped|折り返されている場合は別の行|折り返しが発生（折り返し文字数の超過および開発者が明示的に改行）している場合、`左丸括弧`,`引数`,`右丸括弧`をそれぞれ別の行に配置する|
|separate_lines_if_not_empty|空でない場合は別の行|丸括弧内に宣言がある場合は別の行に右丸括弧を配置|
|separate_lines|別の行|`左丸括弧`,`引数`,`右丸括弧`をそれぞれ別の行に配置する|
|preserve_positions|位置を保持|何もしない|

common_lines

```java
class Example {
    void foo() {
    }

    void bar(int p) {
    }
}
```

separate_lines_if_wrapped

```java
// フォーマット前
class Example {
    void foo() {
    }

    void bar(int p
    ) {
    }
}

// フォーマット後
class Example {
    void foo() {
    }

    void bar(
        int p
    ) {
    }
}
```

separate_lines_if_not_empty

```java
class Example {
    void foo() {
    }

    void bar(
        int p
    ) {
    }
}
```

separate_lines

```java
class Example {
    void foo(
    ) {
    }

    void bar(
        int p
    ) {
    }
}
```

### メソッド/コンストラクター宣言

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_method_delcaration"/>`

メソッド/コンストラクター宣言の丸括弧の位置を設定します。

### メソッド/コンストラクター呼び出し

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_method_invocation"/>`

メソッド/コンストラクター呼び出しの丸括弧の位置を設定します。

### 列挙定数宣言

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_enum_constant_declaration"/>`

列挙定数宣言の丸括弧の位置を設定します。

### レコード宣言

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_record_declaration"/>`

レコード宣言の丸括弧の位置を設定します。

### 注釈

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_annotation"/>`

注釈宣言の丸括弧の位置を設定します。

### ラムダ宣言

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_lambda_declaration"/>`

ラムダ宣言の丸括弧の位置を設定します。

### if, while および do while ステートメント

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_if_while_statement"/>`

if, while および do while ステートメントの丸括弧の位置を設定します。

### for ステートメント

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_for_statment"/>`

forステートメントの丸括弧の位置を設定します。

### switchステートメント

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_switch_statement"/>`

switchステートメントの丸括弧の位置を設定します。

### try文節

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_try_clause"/>`

tryの丸括弧の位置を設定します。

### catch文節

`<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_catch_clause"/>`

catchの丸括弧の位置を設定します。

## 空白

空白を挿入、または削除する設定です。

GUIではすべての設定項目がチェックボックス、設定値としては`insert` or `do not insert`です。

`insert`の場合、フォーマット前の状態にかかわらず空白を挿入します。

`do not insert`の場合、フォーマット前の状態にかかわらず空白を削除します。

### 宣言

#### クラス

##### クラスの左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_type_declaration"/>`

##### 匿名クラスの左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_anonymous_type_declaration"/>`

##### implement節内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_superinterfaces"/>`

##### implement節内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_superinterfaces"/>`

##### permits節内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_permitted_types"/>`

##### permits節内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_permitted_types"/>`

#### フィールド

##### 複数フィールド宣言内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_multiple_field_declarations"/>`

##### 複数フィールド宣言内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_multiple_field_declarations"/>`

#### ローカル変数

##### 複数ローカル宣言内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_multiple_local_declarations"/>`

##### 複数ローカル宣言内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_multiple_local_declarations"/>`

#### コンストラクター

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_constructor_declaration"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_constructor_declaration"/>`

※丸括弧の中身が空の場合を除く

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_constructor_declaration"/>`

※丸括弧の中身が空の場合を除く

##### 空の丸括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_parens_in_constructor_declaration"/>`

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_constructor_declaration"/>`

##### パラメータ内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_constructor_declaration_parameters"/>`

##### パラメータ内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_constructor_declaration_parameters"/>`

##### 'throws'節内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_constructor_declaration_throws"/>`

##### 'throws'節内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_constructor_declaration_throws"/>`

#### メソッド

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_method_declaration"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_method_declaration"/>`

※丸括弧の中身が空の場合を除く

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_method_declaration"/>`

※丸括弧の中身が空の場合を除く

##### 空の丸括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_parens_in_method_declaration"/>`

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_method_declaration"/>`

##### パラメータ内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_method_declaration_parameters"/>`

##### パラメータ内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_method_declaration_parameters"/>`

##### 可変引数パラメータ内の省略符号の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_ellipsis"/>`

##### 可変引数パラメータ内の省略符号の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_ellipsis"/>`

##### 'throws'節内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_method_declaration_throws"/>`

##### 'throws'節内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_method_declaration_throws"/>`

#### ラベル

##### コロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_labeled_statement"/>`

##### コロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_colon_in_labeled_statement"/>`

#### 注釈

##### @の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_at_in_annotation"/>`

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_annotation"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_annotation"/>`

##### コンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_annotation"/>`

##### コンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_annotation"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_annotation"/>`

#### 列挙型（Enum）

##### 宣言の左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_enum_declaration"/>`

##### 定数間のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_enum_declarations"/>`

##### 定数間のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_enum_declarations"/>`

##### 定数引数の左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_enum_constant"/>`

##### 定数引数の左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_enum_constant"/>`

※丸括弧の中身が空の場合を除く

##### 定数引数の空の丸括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_parens_in_enum_constant"/>`

##### 定数引数のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_enum_constant_arguments"/>`

##### 定数引数のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_enum_constant_arguments"/>`

##### 定数引数の右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_enum_constant"/>`

##### 定数本文の左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_enum_constant"/>`

#### 注釈型

##### @の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_at_in_annotation_type_declaration"/>`

##### @の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_at_in_annotation_type_declaration"/>`

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_annotation_type_declaration"/>`

##### 注釈型メンバーの左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_annotation_type_member_declaration"/>`

##### 注釈型メンバーの丸括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_parens_in_annotation_type_member_declaration"/>`

#### レコード

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_record_declaration"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_record_declaration"/>`

##### レコード・コンポーネントのコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_record_components"/>`

##### レコード・コンポーネントのコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_record_components"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_record_declaration"/>`

##### 宣言の左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_record_declaration"/>`

##### レコード・コンストラクターの左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_record_constructor"/>`

#### ラムダ

##### 矢印演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_lambda_arrow"/>`

##### 矢印演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_lambda_arrow"/>`

### 制御ステートメント

#### ブロック

`if`, `else-if`, `else`, `for`, `while`, `do`, `synchronized`, `try`, `catch`ブロックの波括弧についての設定です。

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_closing_brace_in_block"/>`

##### 右波括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_block"/>`

※`else`や`do while`など、右波括弧（`}`）のあとに処理が続くものを対象とする設定です。

`insert`の場合
```java
if (condition){
    return foo;
} else{
    return bar;
}
```

`do not insert`の場合
```java
if (condition){
    return foo;
}else{
    return bar;
}
```

#### if else

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_if"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_if"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_if"/>`

#### for

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_for"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_for"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_for"/>`

##### 初期化内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_for_inits"/>`

##### 初期化内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_for_inits"/>`

##### インクリメント内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_for_increments"/>`

##### インクリメント内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_for_increments"/>`

##### セミコロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_semicolon_in_for"/>`

##### セミコロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_semicolon_in_for"/>`

##### コロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_for"/>`

##### コロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_colon_in_for"/>`

#### switch

##### case内のコロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_case"/>`

##### default内のコロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_default"/>`

##### caseの矢印の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_arrow_in_switch_case"/>`

##### caseの矢印の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_arrow_in_switch_case"/>`

##### defaultの矢印の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_arrow_in_switch_default"/>`

##### defaultの矢印の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_arrow_in_switch_default"/>`

##### case式のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_switch_case_expressions"/>`

##### case式のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_switch_case_expressions"/>`

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_switch"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_switch"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_switch"/>`

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_switch"/>`

#### whileおよびdo while

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_while"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_while"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_while"/>`

#### synchronized

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_synchronized"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_synchronized"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_synchronized"/>`

#### try-with-resources

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_try"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_try"/>`

##### セミコロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_semicolon_in_try_resources"/>`

##### セミコロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_semicolon_in_try_resources"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_try"/>`

#### catch

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_catch"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_catch"/>`

##### 右丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_catch"/>`

#### assert

##### コロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_assert"/>`

##### コロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_colon_in_assert"/>`

#### return

##### 括弧で囲まれた式の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_parenthesized_expression_in_return"/>`

#### throw

##### 括弧で囲まれた式の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_parenthesized_expression_in_throw"/>`

#### セミコロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_semicolon"/>`

### 式

#### 関数呼び出し

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_method_invocation"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_method_invocation"/>`

##### 右丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_method_invocation"/>`

##### 空の丸括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_parens_in_method_invocation"/>`

##### メソッド引数内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_method_invocation_arguments"/>`

##### メソッド引数内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_method_invocation_arguments"/>`

##### オブジェクト割り振り引数内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_allocation_expression"/>`

##### オブジェクト割り振り引数内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_allocation_expression"/>`

##### 明示的コンストラクター呼び出し内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_explicitconstructorcall_arguments"/>`

##### 明示的コンストラクター呼び出し内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_explicitconstructorcall_arguments"/>`

#### 単項演算子

##### 後置演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_postfix_operator"/>`

##### 後置演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_postfix_operator"/>`

##### 接頭演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_prefix_operator"/>`

##### 接頭演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_prefix_operator"/>`

##### 単項演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_unary_operator"/>`

##### 単項演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_unary_operator"/>`

##### 否定演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_not_operator"/>`

#### 2項演算子

##### 乗法演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_multiplicative_operator"/>`

##### 乗法演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_multiplicative_operator"/>`

##### 加法演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_additive_operator"/>`

##### 加法演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_additive_operator"/>`

##### 文字列連結演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_string_concatenation"/>`


##### 文字列連結演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_string_concatenation"/>`

##### シフト演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_shift_operator"/>`

##### シフト演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_shift_operator"/>`

##### 関係演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_relational_operator"/>`

##### 関係演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_relational_operator"/>`

##### ビット演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_bitwise_operator"/>`

##### ビット演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_bitwise_operator"/>`

##### 論理演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_logical_operator"/>`

##### 論理演算子の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_logical_operator"/>`

#### 条件

##### 疑問符の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_question_in_conditional"/>`

##### 疑問符の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_question_in_conditional"/>`

##### コロンの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_colon_in_conditional"/>`

##### コロンの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_colon_in_conditional"/>`

#### 歳入

##### 代入演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_assignment_operator"/>`

##### 代入演算子の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_assignment_operator"/>`

#### 括弧で囲まれた式

##### 左丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_parenthesized_expression"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_parenthesized_expression"/>`

##### 右丸括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_parenthesized_expression"/>`

#### 型キャスト

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_cast"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_cast"/>`

##### 左丸括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_closing_paren_in_cast"/>`

### 配列

#### 配列宣言

##### 左角括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_bracket_in_array_type_reference"/>`

##### 空の角括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_brackets_in_array_type_reference"/>`

#### 配列割り振り

##### 左角括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_bracket_in_array_allocation_expression"/>`

##### 左角括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_bracket_in_array_allocation_expression"/>`

##### 右角括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_bracket_in_array_allocation_expression"/>`

##### 空の角括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_brackets_in_array_allocation_expression"/>`

#### 配列初期化子

##### 左波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_array_initializer"/>`

##### 左波括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_brace_in_array_initializer"/>`

##### 右波括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_brace_in_array_initializer"/>`

##### コンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_array_initializer"/>`

##### コンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_array_initializer"/>`

##### 空の波括弧の間

`<setting id="org.eclipse.jdt.core.formatter.insert_space_between_empty_braces_in_array_initializer"/>`

#### 配列要素アクセス

##### 左角括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_bracket_in_array_reference"/>`

##### 左角括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_bracket_in_array_reference"/>`

##### 右角括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_bracket_in_array_reference"/>`

### パラメータ化された型

#### 型参照

##### 左山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_angle_bracket_in_parameterized_type_reference"/>`

##### 左山括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_angle_bracket_in_parameterized_type_reference"/>`

##### コンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_parameterized_type_reference"/>`

##### コンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_parameterized_type_reference"/>`

##### 右山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_angle_bracket_in_parameterized_type_reference"/>`

#### 型引数

##### 左山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_angle_bracket_in_type_arguments"/>`

##### 左山括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_angle_bracket_in_type_arguments"/>`

##### コンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_type_arguments"/>`

##### コンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_type_arguments"/>`

##### 右山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_angle_bracket_in_type_arguments"/>`

##### 右山括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_closing_angle_bracket_in_type_arguments"/>`

#### 型パラメータ

##### 左山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_angle_bracket_in_type_parameters"/>`

##### 左山括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_angle_bracket_in_type_parameters"/>`

##### パラメータ内のコンマの前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_type_parameters"/>`

##### パラメータ内のコンマの後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_type_parameters"/>`

##### 右山括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_angle_bracket_in_type_parameters"/>`

##### 右山括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_closing_angle_bracket_in_type_parameters"/>`

##### 型制約'&'の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_and_in_type_parameter"/>`

##### 型制約'&'の後

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_and_in_type_parameter"/>`

#### ワイルドカード型

##### 疑問符の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_before_question_in_wildcard"/>`

##### 疑問符の前

`<setting id="org.eclipse.jdt.core.formatter.insert_space_after_question_in_wildcard"/>`


## ブランク行

ソースコード内のブランク行についての設定です。

ブランク行とは、行中に文字・記号が存在しない行です。スペース（インデント）のみある場合はブランク行とみなされます。コメント行はブランク行ではありません。

```java
/**
 * インターフェース
 */ 
interface Empty {
    
}

@interface SomeAnnotationType {
}
```

上記コードの場合、5行目および7行目がブランク行です。

※GUIでは、「ブランク行」「空行」と表記揺れがありますが、設定項目についてはそのまま呼称します。説明の際は「ブランク行」で統一します。

### 設定方法

ブランク行の数は、3つのパラメータによって決定します。

1. 保持する空き行数
2. 項目ごとのブランク行の数（以下、`行数`と呼称）
3. 項目ごとの行間詰めの有無（以下、`行間詰め`と呼称）

`保持する空き行数`は、フォーマット前のソースコードに存在するブランク行のうち、フォーマット後にいくつ残すかを規定します。

フォーマット前
```java
public class Example {

    protected void initialize(int value) {


        // コメント行1



        // コメント行2
        Pair pair = new Pair();
    }
}
```

`保持する空き行数`を0にしてフォーマット
```java
public class Example {
    protected void initialize(int value) {
        // コメント行1
        // コメント行2
        Pair pair = new Pair();
    }
}
```

`保持する空き行数`を1にしてフォーマット
```java
public class Example {

    protected void initialize(int value) {

        // コメント行1

        // コメント行2
        Pair pair = new Pair();
    }
}
```


`行間詰め`が設定されている項目では`保持する空き行数`を無視し、ブランク行の数を0にします。

`行数`が設定されている項目では`行数`と`保持する空き行数`を比較して数値の大きい方を採用します。

`行間詰め`と`行数`が設定されている項目は、`保持する空き行数`で設定されたブランク行を0にした上で`行数`分だけブランク行を挿入します。

### 設定値

「ブランク行」配下の設定項目は、すべて次の設定値を持ちます。

|設定値のキー|設定値の中身|
|--|--|
|value|任意の数値|

例
```xml
`<setting id="org.eclipse.jdt.core.formatter.number_of_empty_lines_to_preserve"/>`
```

GUIで設定した場合、次のように設定値が決まります。

- `行間詰め`が設定されていない場合、設定値は`空き行数`の値となる
- `行間詰め`が設定されている場合、設定値は「`空き行数`の値に1を加算し、負数にした値」となる

例1
```
空き行数: 2
行間詰め: OFF

設定値 = 2
```

例2
```
空き行数: 1
行間詰め: ON

設定値 = -2
```

### 保持する空き行数

`<setting id="org.eclipse.jdt.core.formatter.number_of_empty_lines_to_preserve"/>`

上記で解説した`保持する空き行数`の設定です。

フォーマット後に保持するブランク行の値を設定します。


### コンパイル単位内のブランク行

#### パッケージ宣言の前

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_package"/>`

#### パッケージ宣言の後

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_after_package"/>`

#### インポート宣言の前

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_imports"/>`

#### インポート・グループの間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_between_import_groups"/>`

#### インポート宣言の後

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_after_imports"/>`

#### クラス宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_between_type_declarations"/>`

### 型宣言内のブランク行

#### 最初のメンバー宣言の前

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_first_class_body_declaration"/>`

#### 最初のメンバー宣言の後

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_after_last_class_body_declaration"/>`

#### 異なる種類のメンバー宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_new_chunk"/>`

#### メンバー型宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_member_type"/>`

#### フィールド宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_field"/>`

#### 抽象メソッド宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_abstract_method"/>`

#### メソッド/コンストラクター宣言の間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_method"/>`

### メソッド/コンストラクター宣言内のブランク行

#### メソッド/コンストラクター本体の先頭

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_beginning_of_method_body"/>`

#### メソッド/コンストラクター本体の最後

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_end_of_method_body"/>`

#### コード・ブロックの開始

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_beginning_of_code_block"/>`

#### コード・ブロックの最後

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_end_of_code_block"/>`

#### コード・ブロックを含むステートメントの前

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_before_code_block"/>`

#### コード・ブロックを含むステートメントの後

`<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_after_code_block"/>`

#### switchステートメント・グループの間

`<setting id="org.eclipse.jdt.core.formatter.blank_lines_between_statement_group_in_switch"/>`

## 改行

### 空ステートメントの前

`<setting id="org.eclipse.jdt.core.formatter.put_empty_statement_on_new_line"/>`

空のステートメントの前に改行を挿入します。

### 配列初期化子の左波括弧の後

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_before_closing_brace_in_array_initializer"/>`

配列初期化子の左丸括弧`{`の後に改行を挿入します。

### 配列初期化子の右波括弧の前

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_opening_brace_in_array_initializer"/>`

配列初期化子の右波括弧`}`の前に改行を挿入します。

### ファイルの最後

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_at_end_of_file_if_missing"/>`

ファイルの最後に改行を挿入します。

### 制御文内

#### 'if'文の'else'の前

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_before_else_in_if_statement"/>`

`if`における`else`（`else if`を含む）の前に改行を挿入します。

#### 'try'ステートメントの'catch'の前

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_before_catch_in_try_statement"/>`

`try`における`catch`の前に改行を挿入します。

#### 'try'ステートメントの'finally'の前

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_before_finally_in_try_statement"/>`

`try`における`finally`の前に改行を挿入します。

#### 'do'ステートメントの'while'の前

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_before_while_in_do_statement"/>`

`do while`文の`while`の前に改行を挿入します。

#### ラベルの後

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_label"/>`

`label`の後に改行を挿入します。

#### if else

##### 'then'ステートメントを同じ行に保持

`<setting id="org.eclipse.jdt.core.formatter.keep_then_statement_on_same_line"/>`

`if`に合致した際の処理を`if`文と同じ位置に配置します。

##### 単純'if'を1行に保持

`<setting id="org.eclipse.jdt.core.formatter.keep_imple_if_on_one_line"/>`

`if`文が`else`節を持たない場合、`if`に合致した際の処理を`if`文と同じ位置に配置します。

##### 'else'ステートメントを同じ行に保持

`<setting id="org.eclipse.jdt.core.formatter.keep_else_statement_on_same_line"/>`

`else`以降を同じ行に保持する。

##### 'else if'を1行に保持

`<setting id="org.eclipse.jdt.core.formatter.compact_else_if"/>`

`else if`の、`else`と`if`を同じ行に配置します。（`else if`発生以降でインデントしない）

`true`の場合
```java
    void foo2() {
        if (true) {
            return;
        } else if (false) {
            return;
        } else {
            return;
        }
    }
```

`false`の場合
```java
    void foo2() {
        if (true) {
            return;
        } else
            if (false) {
                return;
            } else {
                return;
            }
    }
```

#### 単純なループ

##### 単純な'for'ループ本体を同じ行に保持する

`<setting id="org.eclipse.jdt.core.formatter.keep_simple_for_body_on_same_line"/>`

処理が1行のみのfor文を1行に配置します。

##### 単純な'while'ループ本体を同じ行に保持する

`<setting id="org.eclipse.jdt.core.formatter.keep_simple_while_body_on_same_line"/>`

処理が1行のみのwhile文を1行に配置します。

##### 単純な'do while'ループ本体を同じ行に保持する

`<setting id="org.eclipse.jdt.core.formatter.keep_simple_do_while_body_on_same_line"/>`

処理が1行のみのdo while文を1行に配置します。

### 注釈の後

#### パッケージ

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_package"/>`

パッケージのアノテーションの後に改行します。

#### 型

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_type"/>`

クラスのアノテーションの後に改行します。

#### enum定数

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_enum_constant"/>`

enum定数のアノテーションの後に改行します。

#### フィールド

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_field"/>`

フィールドのアノテーションの後に改行します。

#### メソッド

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_method"/>`

メソッドのアノテーションの後に改行します。

#### ローカル変数

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_local_variable"/>`

ローカル変数のアノテーションの後に改行します。

#### パラメータ

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_annotation_on_parameter"/>`

メソッド引数のアノテーションの後に改行します。

#### 型注釈

`<setting id="org.eclipse.jdt.core.formatter.insert_new_line_after_type_annotation"/>`

変数型のアノテーションの前に改行します。

### 波括弧を1行のコードに保持

波括弧によって囲まれたブロックをフォーマットする際、開始`{`と終了`}`を同じ行に配置するかを設定します。

別の行
```java
class Example {
}
```

同じ行
```java
class Example {}
```

|value|GUIでの設定値|意味|
|--|--|--|
|one_line_never|なし|必ず別の行に配置する|
|one_line_if_empty|空の場合|ブロック内に宣言がない場合、同じ行に配置する|
|one_line_if_single_item|最大で1つの項目の場合|ブロック内の宣言が1つかつ幅制限に収まる場合、同じ行に配置する|
|one_line_always|幅制限に収まる場合|幅制限に収まる（行幅を超過していない）場合、同じ行に配置する|
|one_line_preserve|状態を保持|フォーマット前の配置を保持する|

#### ループ本体（'for', 'while', 'do while'）

`<setting id="org.eclipse.jdt.core.formatter.keep_loop_body_block_on_one_line"/>`

`for`, `while`, `do while`の波括弧を1行に保持します。

#### 'if then'ステートメント本体

`<setting id="org.eclipse.jdt.core.formatter.keep_if_then_body_block_on_one_line"/>`

`if`文の処理を1行に保持します。

#### 'return'または'throw'文節を1行に保持

`<setting id="org.eclipse.jdt.core.formatter.format_guardian_clause_on_one_line"/>`

`if`文に含まれている`return`および`throw`を1行に保持します。

#### ラムダ本文

`<setting id="org.eclipse.jdt.core.formatter.keep_lambda_body_block_on_one_line"/>`

ラムダ式の本文を1行に保持します。

#### 矢印付きの switch case

`<setting id="org.eclipse.jdt.core.formatter.keep_switch_case_with_arrow_on_one_line"/>`

矢印付きの`switch case`を1行に保持します。

#### 矢印付きの式/ステートメント

`<setting id="org.eclipse.jdt.core.formatter.keep_switch_body_block_on_one_line"/>`

`switch`ブロックを1行に保持します。

#### ステートメント内の他のコード・ブロック

`<setting id="org.eclipse.jdt.core.formatter.keep_code_block_on_one_line"/>`

上記の設定に含まれないブロックを1行に保持します。

#### メソッド宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_method_body_on_one_line"/>`

メソッド宣言を1行に保持します。

#### 単純なgetterとsetterを1行にまとめる

`<setting id="org.eclipse.jdt.core.formatter.keep_simple_getter_setter_on_one_line"/>`

getter/setterを1行に保持します。

#### クラス宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_type_declaration_on_one_line"/>`

クラス宣言を1行に保持します。

#### 匿名クラス宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_anonymous_type_declaration_on_one_line"/>`

匿名クラス宣言を1行に保持します。

#### 列挙宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_enum_declaration_on_one_line"/>`

`enum`宣言を1行に保持します。

#### 列挙定数宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_enum_constant_declaration_on_one_line"/>`

`enum`定数宣言を1行に保持します。

#### レコード宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_record_declaration_on_one_line"/>`

レコード宣言を1行に保持します。

#### レコード・コンストラクター宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_record_constructor_on_one_line"/>`

レコードコンストラクター宣言を1行に保持します。

#### 注釈宣言

`<setting id="org.eclipse.jdt.core.formatter.keep_annotation_declaration_on_one_line"/>`

型注釈宣言を1行に保持します。


## 行折り返し

### ルートの設定項目

#### 行の最大幅

`<setting id="org.eclipse.jdt.core.formatter.lineSplit"/>`

折り返しを行う文字数を設定します。

#### 折り返しされた行のデフォルト・インデント

`<setting id="org.eclipse.jdt.core.formatter.continuation_indentation"/>`

折り返しが発生した際、元の宣言からいくつインデントするかを設定します。

#### 配列初期化子のデフォルト・インデント

`<setting id="org.eclipse.jdt.core.formatter.continuation_indentation_for_array_initializer"/>`

配列初期化子を折り返した際、元の宣言からいくつインデントするかを設定します。

#### すでに折り返された行を結合しない

`<setting id="org.eclipse.jdt.core.formatter.join_wrapped_lines"/>`

フォーマット前に折り返されている行がある場合、フォーマッターによって折り返しを削除（＝行の結合）するか選択します。

`true`の場合：結合しない

`false`の場合：結合する

#### 外側の式を（ネストされた式を1行に保持）折り返す

`<setting id="org.eclipse.jdt.core.formatter.wrap_outer_expressions_when_nested"/>`

処理が行幅を超える場合、キリのよい演算子で折り返しをするか選択します。

`true`の場合
```java
public int expression = (111111 + 222222 + 333333) * (444444 + 555555 + 666666) * (777777
        * 888888 * 999999 * 000000);
```

`false`の場合
```java
public int expression = (111111 + 222222 + 333333) * (444444 + 555555 + 666666)
        * (777777 * 888888 * 999999 * 000000);
```

### 折り返し設定

折り返し設定は、次の3つの設定項目からなります。

- 折り返しをする条件
- 強制分割の有無
- 折り返し時のインデント

また、折り返し設定の設定値は数値です。3項目それぞれで選択した値を加算したものが設定値となります。

例）`必要な場合は折り返す`（16）、`強制分割ON`（1）、`列でインデント`（2）を設定した場合、設定値は19となります。

折り返しの動作は上記3つの設定項目より定まります（※）。そのため、本項では上記3つの設定項目のサンプルコードを記載し、項目ごとのサンプルコードは省略いたします。（どういったコードに適用されるかのみ記載します）

※`演算子の前で折り返す`という設定をもつ項目もあります。これは`true`or`false`で設定します。

`true`の場合
```java
class Example {
    double d = 1.11111111 * 2.22222222 * 3.33333333 * 4.44444444 * 5.55555555 
            * 6.66666666;
}
```

`false`の場合
```java
class Example {
    double d = 1.11111111 * 2.22222222 * 3.33333333 * 4.44444444 * 5.55555555 * 
            6.66666666;
}
```

#### 折り返しをする条件

|GUIでの設定値|意味|値|
|--|--|--|
|折り返しなし|折り返しをしない|0|
|必要な場合は折り返す|行幅の制限を超えた場合は折り返す|16|
|最初の要素（必要な場合は他も）を折り返す|複数要素を列挙する場合に、最初の要素で折り返し、以降は行幅を超えた場合に折り返す|32|
|すべての要素を折り返し、各要素で改行する|すべての要素を折り返し、各要素で改行する|48|
|すべての要素を折り返し、最初の要素以外のすべての要素をインデントする|すべての要素を折り返し、要素以外のすべての要素をインデントする|64|
|必要時以外は最初の要素以外のすべての要素を折り返す|最初の要素は折り返さず、以降の要素はすべて折り返す。ただし、行幅を超える場合は最初の要素も折り返す|80|

`折り返しなし`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}
```

`必要な場合は折り返す`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4,
        int arg5, int arg6) {
    }
}
```

`最初の要素（必要な場合は他も）を折り返す`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(
        int arg1, int arg2, int arg3, int arg4, int arg5,
        int arg6) {
    }
}
```

`すべての要素を折り返し、各要素で改行する`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(
        int arg1,
        int arg2,
        int arg3,
        int arg4,
        int arg5,
        int arg6) {
    }
}
```

`すべての要素を折り返し、最初の要素以外のすべての要素をインデントする`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(
        int arg1,
            int arg2,
            int arg3,
            int arg4,
            int arg5,
            int arg6) {
    }
}
```

`必要時以外は最初の要素以外のすべての要素を折り返す`
```java
// フォーマット前
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}

// フォーマット後
class Example {
    void foo(int arg1,
        int arg2,
        int arg3,
        int arg4,
        int arg5,
        int arg6) {
    }
}
```


#### 強制分割の有無

行幅に余裕がある場合でも折り返し設定を適用します。

|GUIでの設定値|意味|値|
|--|--|--|
|OFF（選択状態にしない）|強制分割を行わない|0|
|ON（選択状態にする）|行幅超過の有無によらず強制分割を行う|1|


#### 折り返し時のインデント

|GUIでの設定値|意味|値|
|--|--|--|
|デフォルト・インデント|要素が折り返された場合は、その宣言から2つインデントした位置に配置する|0|
|1つごとにインデント|要素が折り返された場合はその宣言に対してインデントする|4|
|列でインデント|要素が折り返された場合は、同じ階層の要素とインデント位置を揃える|2|

`デフォルト・インデント`
```java
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4,
            int arg5, int arg6) {
    }
}
```

`1つごとにインデント`
```java
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4,
        int arg5, int arg6) {
    }
}
```

`列でインデント`
```java
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4,
             int arg5, int arg6) {
    }
}
```
※折り返した引数の開始位置が、1行目の引数の位置と揃っている


### クラス宣言

#### 'extends'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_superclass_in_type_declaration"/>`

対象：`extends`宣言以降の項目

```java
class Example extends OtherClass {
}
```

#### 'implements'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_superinterfaces_in_type_declaration"/>`

対象：`implements`宣言以降の項目

```java
class Example implements I1, I2, I3 {
}
```

### コンストラクター宣言

#### パラメータ

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_parameters_in_constructor_declaration"/>`

対象：コンストラクターの引数

```java
class Example {
    Example(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
        this();
    }
}
```

#### 'throws'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_throws_clause_in_constructor_declaration"/>`

対象：`throws`宣言以降の項目

```java
class Example {
    Example() throws FirstException, SecondException, ThirdException {
        return Other.doSomething();
    }
}
```


### メソッド宣言

#### 宣言

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_method_declaration"/>`

対象：メソッド宣言の戻り値以降

```java
class Example {
    public String a_method_with_a_long_name() {
    }
}
```

#### パラメータ

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_parameters_in_method_declaration"/>`

対象：メソッドの引数

```java
class Example {
    void foo(int arg1, int arg2, int arg3, int arg4, int arg5, int arg6) {
    }
}
```


#### 'throws'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_throws_clause_in_method_declaration"/>`

対象：`throws`宣言以降の項目

```java
class Example {
    int foo() throws FirstException, SecondException, ThirdException {
        return Other.doSomething();
    }
}
```

### enum宣言

#### 定数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_enum_constants"/>`

対象：`enum`定数

```java
enum Example {
    CANCELLED, RUNNING, WAITING, FINISHED
}
```

#### 'implements'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_superinterfaces_in_enum_declaration"/>`

対象：`implements`宣言以降の項目

```java
enum Example implements A, B, C {
}
```

#### 定数引数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_enum_constant"/>`

対象：`enum`定数の引数

```java
enum Example {
    GREEN(0, 255, 0)
}
```

### レコード宣言


#### レコード・コンポーネント

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_record_components"/>`

対象：レコード・コンポーネント（レコードの引数）

```java
record Example(int firstNumber, int secondNumbere, String string) {
}
```

#### 'implements'文節

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_superinterfaces_in_record_declaration"/>`

対象：`implements`宣言以降の項目

```java
record Example(int first, int second) implements InterfaceA, InterfaceB, InterfaceC {
}
```


### 関数呼び出し

#### 引数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_method_invocation"/>`

対象：関数呼び出しの引数

```java
class Example {
    void foo() {
        Other.bar(100, nested(200, 300, 400, 500, 600, 700, 800, 900));
    }
}
```

#### 修飾呼び出し

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_selector_in_method_invocation"/>`

対象：メソッドチェーン

```java
class Example {
    String foo() {
        return new StringBuilder(Arrays.asList(11111111, 22222222, 3333333, 44444444))
                .append("TextTextText").append(11111111 + 2222222 + 33333333).toString();
    }
}
```

#### ベースとなる式の最初の行からインデントする

`<setting id="org.eclipse.jdt.core.formatter.align_selector_in_method_invocation_on_expression_first_line"/>`

最初のメソッド呼び出しと以降折り返した際のメソッド呼び出しで開始位置を揃える。

`true`の場合
```java
class Example {
    String foo() {
        return new StringBuilder(Arrays
                .asList(11111111, 22222222, 3333333, 44444444))
                .append("TextTextText")
                .append(11111111 + 2222222 + 33333333)
                .toString();
    }
}
```

`false`の場合
```java
class Example {
    String foo() {
        return new StringBuilder(Arrays
                .asList(11111111, 22222222, 3333333, 44444444))
                        .append("TextTextText")
                        .append(11111111 + 2222222 + 33333333)
                        .toString();
    }
}
```

#### 明示的コンストラクター呼び出し

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_explicit_constructor_call"/>`

対象：コンストラクター呼び出し

```java
class Example extends AnotherClass {
    Example() {
        super(100, 200, 300, 400, 500, 600, 700);
    }
}
```

#### オブジェクト割り振り引数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_allocation_expression"/>`

対象：オブジェクトをインスタンス化する際のコンストラクター引数

```java
class Example {
    SomeClass foo() {
        return new SomeClass(100, 200, 300, 400, 500, 600, 700, 800, 900);
    }
}
```

#### 修飾オブジェクト割り振り引数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_qualified_allocation_expression"/>`

対象：修飾オブジェクトをインスタンス化する際のコンストラクター引数

```java
class Example {
    SomeClass foo() {
        return SomeOtherClass.new SomeClass(100, 200, 300, 400, 500);
    }
}
```


### 二進式

二進式の折り返し設定では、`演算子の前で折り返す`という設定項目（選択値は`true` or `false`）があります。


#### 乗法演算子（*、/、%）
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_multiplicative_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_multiplicative_operator"/>`

対象：乗算、除算、剰余演算処理

```java
class Example {
    double d = 1.11111111 * 2.22222222 * 3.33333333 * 4.44444444 * 5.55555555 * 6.66666666;
}
```

#### 加法演算子（+、-）
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_additive_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_additive_operator"/>`

対象：加算、減算処理

```java
class Example {
    int i = 11111111 + 22222222 + 33333333 + 44444444 + 55555555 + 66666666;
}
```


#### 文字列連結
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_string_concatenation"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_string_concatenation"/>`

対象：文字列連結処理

```java
class Example {
    String concatenatedString = "one two three four " + "five six seven eight " + "nine ten eleven twelve";
}
```


#### シフト演算子（<<、>>、>>>）
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_shift_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_shift_operator"/>`

対象：シフト演算処理

```java
class Example {
    int shiftedInteger = 0xCAFEFACE >>> 0x00000001 >>> 0x00000002 << 0x00000003 >>> 0x00000004;
}
```


#### 比較演算子（<, >, <=, >=, ==, !=）
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_relational_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_relational_operator"/>`

対象：比較演算処理

```java
class Example {
    boolean firstIsGreater = 11111111 > 1.11111111;
}
```

#### ビット演算子
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_bitwise_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_bitwise_operator"/>`

対象：ビット演算処理

```java
class Example {
    int bitAritmetic = 0xCAFEFACE | 0x01010101 & 0x02020202 ^ 0x03030303 ^ 0x04040404 | 0x05050505;
}
```

#### 論理演算子
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_logical_operator"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_logical_operator"/>`

対象：論理演算処理

```java
class Example{
    boolean multipleConditions = conditionOne && conditionTwo || conditionThree && conditionFour || conditionFive;
}
```


### その他の式

#### 条件
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_conditional_expression"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_conditional_operator"/>`

対象：三項演算子内の条件

```java
class Example extends AnotherClass {
    int foo(boolean argument) {
        boolean someValue = number1 == number2 && condition ? someAnser : someAnser2;
        return argument ? 100000 : 200000;
    }
}
```

#### 連鎖条件

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_conditional_expression_chain"/>`

対象：ネストした三項演算子内の条件

```java
class Example extends AnotherClass {
    boolean foo() {
        boolean someValue = condition1() ? value1 : condition2() ? value2 : condition3 ? value3 : value4;
        return someValue;
    }
}
```


#### 代入
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_assignment"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_assignment_operator"/>`

対象：代入処理

```java
class Example {
    private static final String string = "TextTextTextTextTextText";
}
```

#### 配列初期化子

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_array_initializer"/>`

対象：配列初期化子

```java
class Example {
    int[] fArray = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 };
}
```



### ステートメント

#### 'for'

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_for_loop_header"/>`

対象：for文

```java
class Example {
    void foo(int argument) {
        for (int counter = 0; counter < argument; counter++) {
            doSomething(counter);
        }
    }
}
```

#### 'if else'のコンパクト化

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_compact_if"/>`

対象：波括弧`{}`によるブロックを使用せずに`if`を記述

```java
class Example {
    int foo(int argument) {
        if (argument == 0)
            return 0;
        if (argument == 1)
            return 42;
        else
            return 43;
    }
}
```

#### ループのコンパクト化

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_compact_loops"/>`

対象：波括弧`{}`によるブロックを使用せずにループ処理（`for`, `while`, `do while`）を記述

```java
class Example {
    int foo(int argument) {
        while (!stop)
            doSomething();
        for (String s : myStrings)
            System.out.println(s);
        do
            doSomethingElse();
        while (!stop);
    }
}
```


#### 'try-with-resources'

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_resources_in_try"/>`

対象：`try-with-resources`宣言

```java
class Example {
    void foo() {
        try (FileReader reader1 = new FileReader("file1"); FileReader reader2 = new FileReader("file2")) {
        }
    }
}
```

#### 'multi-catch'
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_union_type_in_multicatch"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_or_operator_multicatch"/>`

対象：`catch`句

```java
class Example {
    void foo() {
        try {
        } catch (IllegalArgumentException | NullPointerException | ClassCastException e) {
            e.printStackTrace();
        }
    }
}
```


#### 矢印付きの 'switch' case
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_switch_case_with_arrow"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_switch_case_arrow_operator"/>`

対象：`case`句の矢印以降

```java
class Example {
    boolean foo(Color color) {
        boolean b = switch (color) {
        case RED, GREEN, BLACK, BLUE, CYAN, ORANGE, WHITE, PINK -> true;
        default -> false;
        };
    }
}
```

#### 矢印付きの 'switch' case式

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_switch_case_with_arrow"/>`

対象：`case`句

```java
class Example {
    boolean foo(Color color) {
        boolean b = switch (color) {
        case RED, GREEN, BLACK, BLUE, CYAN, ORANGE, WHITE, PINK -> true;
        default -> false;
        };
    }
}
```

#### コロン付きの 'switch' case式

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_switch_case_with_colon"/>`

対象：`case`句

```java
class Example {
    boolean foo(Color color) {
        switch (color) {
        case RED, GREEN, BLACK, BLUE, CYAN, ORANGE, WHITE, PINK: return true;
        default:
            return false;
        }
    }
}
```


#### 'assert' メッセージ
`<setting id="org.eclipse.jdt.core.formatter.alignment_for_assertion_message"/>`

`<setting id="org.eclipse.jdt.core.formatter.wrap_before_assertion_message_operator"/>`

対象：`assert`のメッセージ

```java
class Example {
    void foo() {
        assert this.field : "field does not have expected value - please investigate";
    }
}
```


### パラメータ化された型

#### 型参照

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_parameterized_type_references"/>`

対象：型参照

```java
class Example {
    Map<String, ? extends java.lang.Object> map = new HashMap<String, java.lang.Object>();
}
```

#### 型引数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_type_arguments"/>`

対象：型引数

```java
class Example {
    void foo(Some someArgument) {
        someArgument.<String, SomeElement, Example> bar();
    }
}
```

#### 型パラメータ

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_type_parameters"/>`

対象：型パラメータ

```java
class Example<S, T extends Element & List, U> {
}
```


### 注釈


#### パッケージ

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_package"/>`

対象：パッケージ宣言

```java
@PackageAnnotation1
@PackageAnnotation2
@PackageAnnotation3
@PackageAnnotation4
package org.example;
```

#### 型

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_type"/>`

対象：クラス宣言

```java
@ClassAnnotation1
@ClassAnnotation2
@ClassAnnotation3
@ClassAnnotation4
public class Example {
}
```

#### enum定数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_enum_constant"/>`

対象：enum定数

```java
public class Example {
    public enum SomeEnum {
        @EnumConstantAnnotation1
        @EnumConstantAnnotation2
        @EnumConstantAnnotation3
        SOME_VALUE,
        @EnumConstantAnnotation1
        @EnumConstantAnnotation4
        OTHER_VALUE
    }
}
```

#### フィールド

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_field"/>`

対象：フィールド宣言

```java
class Example{
    @FieldAnnotation1
    @FieldAnnotation2
    @FieldAnnotation3
    @FieldAnnotation4
    private int foo = 0;
}
```

#### メソッド

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_method"/>`

対象：メソッド宣言

```java
class Example{
    @MethodAnnotatoin1
    @MethodAnnotation2
    @MethodAnnotation3
    @MethodAnnotation4
    public void bar() {
    }
}
```

#### ローカル変数

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_local_variable"/>`

対象：ローカル変数宣言

```java
public class Example {
    public void bar2() {
        @VariableAnnotation1
        @VariableAnnotation2
        @VariableAnnotation4
        String localVariable = "";
    }
}
```

#### パラメータ

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_parameter"/>`

対象：メソッド引数

```java
public class Example {
    public void bar2(@ParamAnnotation1 @ParamAnnotation2 @ParameterAnnotation3 String param) {
    }
}
```

#### 型注釈

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_type_annotations"/>`

対象：型注釈

```java
public class Example {
    @FieldAnnotation
    private @TypeAnnotation1 @TypeAnnotation2 @TypeAnnotation3 String foo;

    @MethodAnnotation
    public @TypeAnnotation1 @TypeAnnotation2 @TypeAnnotation3 String bar() {
        return "";
    }
}
```

#### 要素-値ペア

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_arguments_in_annotation"/>`

対象：アノテーション内のkey-value

```java
@MyAnnotation(value1 = "this is an example",
        value2 = "of an annotation",
        value3 = "with several arguments",
        value4 = "which may need to be wrapped")
class Example {
}

```


### モジュール記述

#### モジュール・ステートメント

`<setting id="org.eclipse.jdt.core.formatter.alignment_for_module_statements"/>`

対象：モジュール・ステートメント

```java
module example.module0 {
    provides example.other.module1.SomeService with example.module0.Service1, example.module0.Service2;
}
```



## コメント

### コメントの最大幅

`<setting id="org.eclipse.jdt.core.formatter.comment.line_length"/>`

コメントをフォーマットする際に折り返す行幅を設定します。以下、コメントをフォーマットする設定がされている場合には本項目の折り返し設定が適用されます。

#### コメント開始位置から幅をカウントする

`<setting id="org.eclipse.jdt.core.formatter.comment.count_line_length_from_starting_position"/>`

コメントのカウント開始位置を設定します。

`true`の場合：コメント開始位置から文字数をカウントする

`false`の場合：行の開始位置から文字数をカウントする（空白を文字数に含む）

#### Javadocコメント・フォーマットを使用可能にする

`<setting id="org.eclipse.jdt.core.formatter.comment.format_javadoc_comments"/>`

Javadocの内容をフォーマットします。フォーマット内容については[Javadoc](#javadoc)に準拠します。

#### ブロックコメント・フォーマット

`<setting id="org.eclipse.jdt.core.formatter.comment.format_block_comments"/>`

ブロックコメントの内容をフォーマットします。フォーマット内容については[ブロック・コメント](#ブロック・コメント)に準拠します。

#### 行コメント・フォーマットを使用可能にする

`<setting id="org.eclipse.jdt.core.formatter.comment.format_line_comments"/>`

行コメントの内容をフォーマットします。

#### 最初の列で行コメントをフォーマット

`<setting id="org.eclipse.jdt.core.formatter.format_line_comment_starting_on_first_column"/>`

行コメントの折り返し設定を反映し、インデントを揃えます。

#### ヘッダー・コメント・フォーマットを使用可能にする

`<setting id="org.eclipse.jdt.core.formatter.comment.format_header"/>`

パッケージ宣言に対するコメントをフォーマットします。フォーマット内容については[Javadoc](#javadoc)および[ブロック・コメント](#ブロック・コメント)に準拠します。

#### コードと行コメントの間の空白を保持する

`<setting id="org.eclipse.jdt.core.formatter.comment.preserve_white_space_between_code_and_line_comments"/>`

コードの末尾にコメントを配置した場合、入力した空白を保持します。

#### 最初の列で行コメントをインデントしない

`<setting id="org.eclipse.jdt.core.formatter.never_indent_line_comments_on_first_column"/>`

コメントをインデントしません。

（通常、インデントサイズはコメントを配置したブロックのインデントに準拠します）

#### 最初の列でブロック・コメントをインデントしない

`<setting id="org.eclipse.jdt.core.formatter.never_indent_block_comments_on_first_column"/>`

ブロックコメントをインデントしません。

#### 行を結合しない

`<setting id="org.eclipse.jdt.core.formatter.join_lines_in_comments"/>`

複数行に渡ってコメントが記載されている場合、コメントの改行を保持するか選択します。

`true`の場合：改行を保持する（行を結合しない）

`false`の場合：改行を保持しない（行を結合する）


### Javadoc

#### HTMLタグをフォーマット

`<setting id="org.eclipse.jdt.core.formatter.comment.format_html"/>`

Javadoc内のHTMLタグをフォーマットします。

#### 'pre'タグ内のJavaコード・スニペットをフォーマット

`<setting id="org.eclipse.jdt.core.formatter.comment.format_source_code"/>`

Javadoc内で`<pre></pre>`に囲まれた部分をフォーマットします。

フォーマット内容はJavaのフォーマット設定に準拠します。

#### Javadicタグの前のブランク行

`<setting id="org.eclipse.jdt.core.formatter.comment.insert_new_line_before_root_tags"/>`

Javadoc内で説明箇所とタグ（`@param`など）の間にブランク行を挿入します。

`true`の場合
```java
// フォーマット前

    /** The following is some sample code which illustrates source formatting
     * within javadoc comments:
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000. */
    int foo(int first, int second) throws Exception;

// フォーマット後

    /** The following is some sample code which illustrates source formatting
     * within javadoc comments:
     * 
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000. */
    int foo(int first, int second) throws Exception;
```

#### 異なるタイプのタグ間のブランク行

`<setting id="org.eclipse.jdt.core.formatter.comment.insert_new_line_between_different_tags"/>`

Javadoc内で異なるタグ（`@param`と`@return`など）の間にブランク行を挿入します。

`true`の場合
```java
// フォーマット前

    /** The following is some sample code which illustrates source formatting
     * within javadoc comments:
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000. */
    int foo(int first, int second) throws Exception;

// フォーマット後

    /** The following is some sample code which illustrates source formatting
     * within javadoc comments:
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     *
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     *
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000. */
    int foo(int first, int second) throws Exception;
```

#### カラムでJavadocタグを整列

`<setting id="org.eclipse.jdt.core.formatter.comment.indent_root_tags"/>`

`<setting id="org.eclipse.jdt.core.formatter.comment.align_tags_names_descriptions"/>`

`<setting id="org.eclipse.jdt.core.formatter.comment.align_tags_descriptions_grouped"/>`

名前と説明を揃える

|設定項目|設定値|
|--|--|
|`indent_root_tags`|`false`|
|`align_tags_names_descriptions`|`true`|
|`align_tags_descriptions_grouped`|`false`|

タグのパラメータ名および説明の開始位置を揃えます。

```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param  first
     *                       The first parameter. For an optimum result, this
     *                       should be an odd number between 0 and 100.
     * @param  second
     *                       The second parameter.
     * @throws Exception
     *                       when the foo operation cannot be performed for one
     *                       reason or another.
     * @return           The result of the foo operation, usually an even number
     *                   within 0 and 1000.
     */
    int foo(int first, int second) throws Exception;
```

タイプ別にグループ化された説明を揃える

|設定項目|設定値|
|--|--|
|`indent_root_tags`|`false`|
|`align_tags_names_descriptions`|`false`|
|`align_tags_descriptions_grouped`|`true`|

同じタグが複数ある場合、説明の開始位置を揃えます。

```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *                   The first parameter. For an optimum result, this should
     *                   be an odd number between 0 and 100.
     * @param second
     *                   The second parameter.
     * @throws Exception
     *                       when the foo operation cannot be performed for one
     *                       reason or another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

説明をタグの幅に合わせる

|設定項目|設定値|
|--|--|
|`indent_root_tags`|`true`|
|`align_tags_names_descriptions`|`false`|
|`align_tags_descriptions_grouped`|`false`|

タグの位置（文字数）によって説明の開始位置を決定します。

```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

整列しない

|設定項目|設定値|
|--|--|
|`indent_root_tags`|`false`|
|`align_tags_names_descriptions`|`false`|
|`align_tags_descriptions_grouped`|`false`|

列で整列しません。フォーマットはされますが、位置の調整を行いません。

```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *     The first parameter. For an optimum result, this should be an odd
     *     number between 0 and 100.
     * @param second
     *     The second parameter.
     * @throws Exception
     *     when the foo operation cannot be performed for one reason or another.
     * @return The result of the foo operation, usually an even number within 0
     * and 1000.
     */
    int foo(int first, int second) throws Exception;
```


#### @param/@throwsの説明の前で改行する

`<setting id="org.eclipse.jdt.core.formatter.comment.insert_new_line_for_parameter"/>`

タグ名の後に改行し、説明は次の行に配置します。

`insert`の場合
```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

`do not insert`の場合
```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first The first parameter. For an optimum result, this should be
     *            an odd number between 0 and 100.
     * @param second The second parameter.
     * @throws Exception when the foo operation cannot be performed for one
     *             reason or another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

#### 折り返された@param/@throwsをインデントする

`<setting id="org.eclipse.jdt.core.formatter.comment.indent_parameter_description"/>`

タグ名の次の行以降に配置された説明をインデントします。

`true`の場合
```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *            The first parameter. For an optimum result, this should be an
     *            odd number between 0 and 100.
     * @param second
     *            The second parameter.
     * @throws Exception
     *             when the foo operation cannot be performed for one reason or
     *             another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

`false`の場合
```java
    /**
     * Descriptions of parameters and return values are best appended at end of
     * the javadoc comment.
     * 
     * @param first
     *        The first parameter. For an optimum result, this should be an odd
     *        number between 0 and 100.
     * @param second
     *        The second parameter.
     * @throws Exception
     *         when the foo operation cannot be performed for one reason or
     *         another.
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo(int first, int second) throws Exception;
```

#### 折り返すときに他のタグの説明をインデントする

`<setting id="org.eclipse.jdt.core.formatter.comment.indent_tag_description"/>`

`@param`,`@throws`以外のタグにおいて、折り返しが発生した際にインデントします。

`true`の場合
```java
    /**
     * @return The result of the foo operation, usually an even number within 0
     *             and 1000.
     */
    int foo();
```

`false`の場合
```java
    /**
     * @return The result of the foo operation, usually an even number within 0
     *         and 1000.
     */
    int foo();
```


#### /** および */ を別の行にする

`<setting id="org.eclipse.jdt.core.formatter.comment.new_lines_at_javadoc_boundaries"/>`

Javadocの開始`/**`および終了`*/`を本文と別の行に配置します。

#### ブランク行を除去

`<setting id="org.eclipse.jdt.core.formatter.comment.clear_blank_lines_in_javadoc_comment"/>`

Javadoc内のブランク行を除去します。ただし、他の設定によって項目間に挿入されているブランク行は除去されません。

### ブロック・コメント

#### /* および */ を別の行にする

`<setting id="org.eclipse.jdt.core.formatter.comment.new_lines_at_block_boundaries"/>`

ブロックコメントの開始`/*`および終了`*/`を本文と別の行に配置します。

`true`の場合
```java
    /*
     * These possibilities include: <ul><li>Formatting of header
     * comments.</li><li>Formatting of Javadoc tags</li></ul>
     */
    int bar2();
```

`false`の場合
```java
    /* These possibilities include: <ul><li>Formatting of header
     * comments.</li><li>Formatting of Javadoc tags</li></ul> */
    int bar2();
```

#### ブランク行を除去

`<setting id="org.eclipse.jdt.core.formatter.comment.clear_blank_lines_in_block_comment"/>`

ブランク行を除去します。

## off/onタグ

off/onタグを使用すると、任意の場所でフォーマッターを無効化/有効化できます。

- offタグを配置すると、以降のソースコードおよびコメントはフォーマットされません
- onタグを配置すると、以降のソースコードおよびコメントはフォーマットされます

※onタグの使用方法

フォーマッターはデフォルトで有効化されています。そのため、すべてのファイルの先頭にonタグを配置する必要はありません。

offタグによってフォーマッターを無効化した後、フォーマットを再開したい場合にonタグを使用します。

### off/onタグを使用可能にする

`<setting id="org.eclipse.jdt.core.formatter.use_on_off_tags"/>`

off/onタグを使用可能にします。どのような文字列をoff/onタグにするか、それぞれ設定可能です。

フォーマット前のコード
```java
void method1()   {  doSomething();  }

// @formatter:off
void method2()   {  doSomething();  }
// @formatter:on

void method3()   {  doSomething();  }

/* @formatter:off                                           */
              void
              foo()
              ;
```

`true`の場合
```java
void method1() {
    doSomething();
}

// @formatter:off
void method2()   {  doSomething();  }
// @formatter:on

void method3() {
    doSomething();
}

/* @formatter:off                                           */
              void
              foo()
              ;
```

`false`の場合
```java
void method1() {
    doSomething();
}

// @formatter:off
void method2() {
    doSomething();
}
// @formatter:on

void method3() {
    doSomething();
}

/* @formatter:off                                           */
void foo();
```

### offタグ

`<setting id="org.eclipse.jdt.core.formatter.disabling_tag"/>`

offタグの文字列を規定します。

本項目で設定した文字列がコメント上に配置されている場合、フォーマッターを無効化します。

### onタグ

`<setting id="org.eclipse.jdt.core.formatter.enabling_tag"/>`

onタグの文字列を規定します。

本項目で設定した文字列がコメント上に配置されている場合、フォーマッターを有効化します。
