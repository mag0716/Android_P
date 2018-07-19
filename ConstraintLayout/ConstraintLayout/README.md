# ConstraintLayout Sample

* ConstraintLayout の機能を試すサンプルプロジェクト

## [WIP] virtual_layout

* Linear
* Flow

を試すサンプル

## layer

* [Layer](https://developer.android.com/reference/android/support/constraint/helper/Layer)
  * View の集まりに対して見た目を操作する
  * transforms をサポート
    * rotation
    * scale
    * translation
* 複数の View をまとめて背景を指定する
* Group と違ってサイズがあるのでクリックイベントなども設定することができた

## decorators

* `ConstraintHelper` を利用して、カスタム Decorator を試すサンプル
  * `updatePostLayout` で指定された View に対して背景色を指定する Decorator
  * 最終目標は https://www.youtube.com/watch?v=ytZteMo4ETk&t=24m55s のアニメーション

### 疑問点

* 試した MetaballsDecorator だと、通常のカスタム View でも対応ができるが、どういった場合に、`ConstraintHelper` を使えばよいのか？
* `ConstraintHelper#onDraw` はどういった場合に利用する？
* https://www.youtube.com/watch?v=ytZteMo4ETk&t=24m55s のアニメーションはどう実装すればよいか？