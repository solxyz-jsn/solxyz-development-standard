# 設定項目の説明

本ドキュメントでは、Checkstyleの設定項目について解説します。

Solxyz Standardでは、[Googleが提供しているCheckstyle設定](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml)を引用し、一部カスタマイズを行なっています。

また、Checkstyleで設定できる項目は多岐に渡ります。そのため、本ドキュメントではSolxyz StandardのCheckstyle設定ファイルにある項目のみ取り扱います。あらかじめご了承ください。

その他の設定項目については、[Checkstyleリファレンス - Checks](https://checkstyle.sourceforge.io/checks.html)をご参照ください。

## 目次

- [設定項目の説明](#設定項目の説明)
  - [目次](#目次)
  - [Checker](#checker)
    - [BeforeExecutionExclusionFileFilter](#beforeexecutionexclusionfilefilter)
    - [FileTabCharacter](#filetabcharacter)
    - [LineLength](#linelength)
    - [TreeWalker](#treewalker)
      - [OuterTypeFilename](#outertypefilename)
      - [IllegalTokenText](#illegaltokentext)
      - [AvoidEscapedUnicodeCharacters](#avoidescapedunicodecharacters)
      - [AvoidStarImport](#avoidstarimport)
      - [OneTopLevelClass](#onetoplevelclass)
      - [NoLineWrap](#nolinewrap)
      - [EmptyBlock](#emptyblock)
      - [NeedBraces](#needbraces)
      - [LeftCurly](#leftcurly)
      - [RightCurly](#rightcurly)
      - [SuppressionXpathSingleFilter](#suppressionxpathsinglefilter)
      - [WhitespaceAfter](#whitespaceafter)
      - [WhitespaceAround](#whitespacearound)
      - [OneStatementPerLine](#onestatementperline)
      - [MultipleVariableDeclarations](#multiplevariabledeclarations)
      - [ArrayTypeStyle](#arraytypestyle)
      - [MissingSwitchDefault](#missingswitchdefault)
      - [FallThrough](#fallthrough)
      - [UpperEll](#upperell)
      - [ModifierOrder](#modifierorder)
      - [EmptyLineSeparator](#emptylineseparator)
      - [SeparatorWrap](#separatorwrap)
      - [PackageName](#packagename)
      - [TypeName](#typename)
      - [MemberName](#membername)
      - [ParameterName](#parametername)
      - [LambdaParameterName](#lambdaparametername)
      - [CatchParameterName](#catchparametername)
      - [LocalVariableName](#localvariablename)
      - [PatternVariableName](#patternvariablename)
      - [ClassTypeParameterName](#classtypeparametername)
      - [RecordComponentName](#recordcomponentname)
      - [RecordTypeParameterName](#recordtypeparametername)
      - [MethodTypeParameterName](#methodtypeparametername)
      - [InterfaceTypeParameterName](#interfacetypeparametername)
      - [NoFinalizer](#nofinalizer)
      - [GenericWhitespace](#genericwhitespace)
      - [Indentation](#indentation)
      - [AbbreviationAsWordInName](#abbreviationaswordinname)
      - [NoWhitespaceBeforeCaseDefaultColon](#nowhitespacebeforecasedefaultcolon)
      - [OverloadMethodsDeclarationOrder](#overloadmethodsdeclarationorder)
      - [VariableDeclarationUsageDistance](#variabledeclarationusagedistance)
      - [CustomImportOrder](#customimportorder)
      - [MethodParamPad](#methodparampad)
      - [NoWhitespaceBefore](#nowhitespacebefore)
      - [ParenPad](#parenpad)
      - [OperatorWrap](#operatorwrap)
      - [AnnotationLocation](#annotationlocation)
      - [NonEmptyAtclauseDescription](#nonemptyatclausedescription)
      - [InvalidJavadocPosition](#invalidjavadocposition)
      - [JavadocTagContinuationIndentation](#javadoctagcontinuationindentation)
      - [SummaryJavadoc](#summaryjavadoc)
      - [JavadocParagraph](#javadocparagraph)
      - [RequireEmptyLineBeforeBlockTagGroup](#requireemptylinebeforeblocktaggroup)
      - [AtclauseOrder](#atclauseorder)
      - [JavadocMethod](#javadocmethod)
      - [MissingJavadocMethod](#missingjavadocmethod)
      - [MissingJavadocType](#missingjavadoctype)
      - [MethodName](#methodname)
      - [SingleLineJavadoc](#singlelinejavadoc)
      - [EmptyCatchBlock](#emptycatchblock)
      - [CommentsIndentation](#commentsindentation)

## Checker

チェックルールを記載するルートのモジュールです。

すべてのモジュールは、`Checker`の子孫の要素となります。

### BeforeExecutionExclusionFileFilter

すべてのチェックから除外するファイルをパスパターンで指定します。

<https://checkstyle.sourceforge.io/config_filefilters.html#BeforeExecutionExclusionFileFilter>

### FileTabCharacter

ソースコード内にタブ文字が使われていないことを検証します。

<https://checkstyle.sourceforge.io/config_whitespace.html#FileTabCharacter>

### LineLength

一行の文字数が指定の値を超えていないことを検証します。

<https://checkstyle.sourceforge.io/config_sizes.html#LineLength>

### TreeWalker

`TreeWalker`モジュールは、Javaの構文解析が必要なチェックの親モジュールです。

ほとんどのチェックは本モジュールに所属します。

#### OuterTypeFilename

型の宣言（`class`,`interface`,`enum`,`record`）とファイル名が一致していることを検証します。

<https://checkstyle.org/config_misc.html#OuterTypeFilename>

#### IllegalTokenText

リテラルに任意の値が含まれていないことを検証します。

※Unicodeエスケープ値とは、`\u221e`（無限を表す記号をUnicodeで表記したときの値）のようなものを指します。

<https://checkstyle.org/config_coding.html#IllegalTokenText>

#### AvoidEscapedUnicodeCharacters

Unicodeエスケープ値を使用していないことを検証します。

<https://checkstyle.org/config_misc.html#AvoidEscapedUnicodeCharacters>

#### AvoidStarImport

`*`を使用してのimport宣言が含まれないことを検証します。

<https://checkstyle.org/config_imports.html#AvoidStarImport>

#### OneTopLevelClass

型の宣言（`class`,`interface`,`enum`,`record`）がひとつのファイルにひとつだけであることを検証します。

<https://checkstyle.org/config_design.html#OneTopLevelClass>

#### NoLineWrap

対象のステートメントが改行されていないことを検証します。

<https://checkstyle.org/config_whitespace.html#NoLineWrap>

#### EmptyBlock

空のブロックがないことを検証します。

<https://checkstyle.org/config_blocks.html#EmptyBlock>

#### NeedBraces

ブロックが波括弧で囲まれていることを検証します。

<https://checkstyle.org/config_blocks.html#NeedBraces>

#### LeftCurly

波括弧が行末に配置されていることを検証します。

<https://checkstyle.org/config_blocks.html#LeftCurly>

#### RightCurly

`if-else`,`try-catch-finally`の閉じ波括弧が指定の位置にあることを検証します。

※「閉じ波括弧が次のステートメントと同じ行」の例

```java
    // OK
    if (condition) {

    } else {

    }

    //NG
    if (condition) {

    } 
    else {

    }
```

<https://checkstyle.org/config_blocks.html#RightCurly>

#### SuppressionXpathSingleFilter

XPATHでチェックを抑制するフィルターです。

<https://checkstyle.org/config_filters.html#SuppressionXpathSingleFilter>

#### WhitespaceAfter

指定のステートメントの後に空白があることを検証します。

<https://checkstyle.org/config_whitespace.html#WhitespaceAfter>

#### WhitespaceAround

ステートメントの前後に空白があることを検証します。

<https://checkstyle.org/config_whitespace.html#WhitespaceAround>

#### OneStatementPerLine

1行にひとつのステートメントしかないことを検証します。

<https://checkstyle.org/config_coding.html#OneStatementPerLine>

#### MultipleVariableDeclarations

変数宣言が独立していること（ひとつの変数宣言でひとつの変数）を検証します。

```java
// OK
int i;
int j;

// NG
int i,j;
```

<https://checkstyle.org/config_coding.html#MultipleVariableDeclarations>

#### ArrayTypeStyle

配列の型宣言が指定のスタイルであることを検証します。

デフォルトはJavaスタイル（型の後に`[]`をつける）です。

```java
  int[] nums; // Javaスタイル
  String strings[]; // Cスタイル
```

<https://checkstyle.org/config_misc.html#ArrayTypeStyle>

#### MissingSwitchDefault

`Switch`文（式）に`default`ステートメントがあることを検証します。

<https://checkstyle.org/config_coding.html#MissingSwitchDefault>

#### FallThrough

switch内にフォールスルーを含まないことを検証します。

フォールスルーとは、`break`を含まないcaseブロックです。

<https://checkstyle.org/config_coding.html#FallThrough>

#### UpperEll

longリテラルで使用する「L」が大文字であることを検証します。

```java
// OK
long hoge = 1000000L;

// NG
long hoge = 1000000l;
```

<https://checkstyle.org/config_misc.html#UpperEll>

#### ModifierOrder

修飾子の順序が規定のとおりになっていることを検証します。

修飾子の優先順

1. public
1. protected
1. private
1. abstract
1. default
1. static
1. sealed
1. non-sealed
1. final
1. transient
1. volatile
1. synchronized
1. native
1. strictfp

<https://checkstyle.org/config_modifier.html#ModifierOrder>

#### EmptyLineSeparator

空行による区切りがステートメントの前に挿入されている/されていないことを検証します。

<https://checkstyle.org/config_whitespace.html#EmptyLineSeparator>

#### SeparatorWrap

行折り返しが指定のステートメントで行われていないことを検証します。

<https://checkstyle.org/config_whitespace.html#SeparatorWrap>

#### PackageName

パッケージ名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#PackageName>

#### TypeName

型名が指定のパターンに準拠していることを確認します。

<https://checkstyle.org/config_naming.html#TypeName>

#### MemberName

インスタンス変数（`static`でないフィールド変数）名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#MemberName>

#### ParameterName

メソッドの引数が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#ParameterName>

#### LambdaParameterName

ラムダ式の引数が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#LambdaParameterName>

#### CatchParameterName

catch句の引数が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#CatchParameterName>

#### LocalVariableName

ローカル変数名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#LocalVariableName>

#### PatternVariableName

パターン変数名が指定のパターンに準拠していることを検証します。

パターン変数とは、`instanceof`演算子で任意の変数がその型に代入可能と判定された際、自動でその型の変数を作成して変数を代入する機能および作成した変数のことです。

これにより、`(String) obj`のような型変換をするだけのボイラープレートコードが削減できます。

```java
// パターン変数なし
void foo(Object obj) {
    if (obj instanceof String) {               
      String str = (String) obj;            
      System.out.println(str.toUpperCase());  
    }
}

// パターン変数あり
void foo(Object obj) {
    if (obj instanceof String str) {               
      System.out.println(str.toUpperCase());  
    }
}
```

<https://checkstyle.org/config_naming.html#PatternVariableName>

#### ClassTypeParameterName

クラスの型パラメータ名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#ClassTypeParameterName>

#### RecordComponentName

レコードコンポーネント名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#RecordComponentName>

#### RecordTypeParameterName

レコードの型パラメータ名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#RecordTypeParameterName>

#### MethodTypeParameterName

メソッドの型パラメータ名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#MethodTypeParameterName>

#### InterfaceTypeParameterName

インターフェースの型パラメータ名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#InterfaceTypeParameterName>

#### NoFinalizer

`finalize`メソッドをオーバーライドしていないことを検証します。

<https://checkstyle.org/config_coding.html#NoFinalizer>

#### GenericWhitespace

山括弧`<>`周辺の空白が規則にしたがっていることを検証します。（規則は固定）

主に、`<`の後と`>`の前に空白がないことを検証します。

その他の規則についてはリファレンスをご参照ください。

<https://checkstyle.org/config_whitespace.html#GenericWhitespace>

#### Indentation

インデントがルールに準拠していることを検証します。

<https://checkstyle.org/config_misc.html#Indentation>

#### AbbreviationAsWordInName

識別子名に大文字が指定の数以上連続しないことを検証します。

変数名などに略語を使用する場合、大文字で連続した名前をつけます。（例：`static_web_apps` → `SWA`）

連続する大文字の数が指定より多い場合に違反とします。

<https://checkstyle.org/config_naming.html#AbbreviationAsWordInName>

#### NoWhitespaceBeforeCaseDefaultColon

switchブロックのコロンの前に空白がないことを検証します。

<https://checkstyle.org/config_whitespace.html#NoWhitespaceBeforeCaseDefaultColon>

#### OverloadMethodsDeclarationOrder

オーバーロードされたメソッドがグループ化されている（並んでいる）ことを検証します。

オーバーロードするメソッドの中に違う名前のメソッドが入っている場合に違反となります。

<https://checkstyle.org/config_coding.html#OverloadMethodsDeclarationOrder>

#### VariableDeclarationUsageDistance

変数宣言とその変数の使用箇所が指定の距離以上離れていないことを検証します。

<https://checkstyle.org/config_coding.html#VariableDeclarationUsageDistance>

#### CustomImportOrder

インポート宣言が、指定の順序であることを検証します。

<https://checkstyle.org/config_imports.html#CustomImportOrder>

#### MethodParamPad

メソッド呼び出しおよびメソッド定義のスペースが規定どおりになっていることを検証します。

メソッドとパラメータの`()`間のスペースに関するポリシーを規定できます。

<https://checkstyle.org/config_whitespace.html#MethodParamPad>

#### NoWhitespaceBefore

<https://checkstyle.org/config_whitespace.html#NoWhitespaceBefore>

#### ParenPad

丸括弧`()`の中のスペースが規定どおりになっていることを検証します。

左丸括弧`(`のあとのスペース、右丸括弧`)`の前のスペースに関するポリシーを規定できます。

<https://checkstyle.org/config_whitespace.html#ParenPad>

#### OperatorWrap

演算子で行を折り返す方法が規定どおりになっていることを確認します。

```java
// +のあとに折り返し
int num = 1 + 2 + 3 +
        4 + 5;

// +の前に折り返し
int num = 1 + 2 + 3 
        + 4 + 5;
```

<https://checkstyle.org/config_whitespace.html#OperatorWrap>

#### AnnotationLocation

アノテーションの位置が規定どおりになっていることを検証します。

<https://checkstyle.org/config_annotation.html#AnnotationLocation>

#### NonEmptyAtclauseDescription

Javadocのブロックタグの説明があることを検証します。

<https://checkstyle.org/config_javadoc.html#NonEmptyAtclauseDescription>

#### InvalidJavadocPosition

Javadocが正しい位置にあることを検証します。

<https://checkstyle.org/config_javadoc.html#InvalidJavadocPosition>

#### JavadocTagContinuationIndentation

Javadocのブロックタグのインデントが規定どおりになっていることを検証します。

<https://checkstyle.org/config_javadoc.html#JavadocTagContinuationIndentation>

#### SummaryJavadoc

Javadocに指定のパターンが含まれていないことを検証します。

<https://checkstyle.org/config_javadoc.html#SummaryJavadoc>

#### JavadocParagraph

Javadocが次のルールに準拠していることを検証します。

- 段落間に1つの空白行が入っていること
- `<p>`を使う際は文章の直前に配置する

<https://checkstyle.org/config_javadoc.html#JavadocParagraph>

#### RequireEmptyLineBeforeBlockTagGroup

Javadocにブロックタグがある場合、ブロックタグの前に空白行を挿入されていることを検証します。

<https://checkstyle.org/config_javadoc.html#RequireEmptyLineBeforeBlockTagGroup>

#### AtclauseOrder

Javadocのブロックタグの順序が規定どおりになっていることを検証します。

<https://checkstyle.org/config_javadoc.html#AtclauseOrder>

#### JavadocMethod

メソッドのJavadocが規定どおりになっていることを検証します。

<https://checkstyle.org/config_javadoc.html#JavadocMethod>

#### MissingJavadocMethod

メソッドのJavadocが存在することを検証します。

<https://checkstyle.org/config_javadoc.html#MissingJavadocMethod>

#### MissingJavadocType

型宣言のJavadocが存在することを検証します。

<https://checkstyle.org/config_javadoc.html#MissingJavadocType>

#### MethodName

メソッド名が指定のパターンに準拠していることを検証します。

<https://checkstyle.org/config_naming.html#MethodName>

#### SingleLineJavadoc

Javadocを1行で書く際、ブロックタグを含まないことを検証します。

<https://checkstyle.org/config_javadoc.html#SingleLineJavadoc>

#### EmptyCatchBlock

空のcatchブロックがないことを検証します。

<https://checkstyle.org/config_blocks.html#EmptyCatchBlock>

#### CommentsIndentation

コメントがコメント対象と同じインデントであることを検証します。

<https://checkstyle.org/config_misc.html#CommentsIndentation>
