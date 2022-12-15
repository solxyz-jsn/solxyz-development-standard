# Change Log

## [0.1.0] - 2022-12-14

### Remove

- SuppressionFilter
- RequireEmptyLineBeforeBlockTagGroup
- SuppressionXpathFilter

### Update

- LineLength
  - 最大値を120文字に変更
- AvoidStarImport
  - `<property name="allowStaticMemberImports" value="true"/>`を追加
- EmptyLineSeparator
  - `PACKAGE_DEF`を削除
- Indentation
  - すべてのインデントを4に変更
- CustomImportOrder
  - `<property name="customImportOrderRules" value="STATIC###STANDARD_JAVA_PACKAGE###SPECIAL_IMPORTS###THIRD_PARTY_PACKAGE"/>`に変更
  - `<property name="standardPackageRegExp" value="^(java|javax)\."/>`を追加
  - `<property name="specialImportsRegExp" value="^(org|jp)\."/>`を追加
  - `<property name="thirdPartyPackageRegExp" value="^com\."/>`を追加
- SummaryJavadoc
  - `<property name="period" value=""/>`を追加
