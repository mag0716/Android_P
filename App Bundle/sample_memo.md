# Sample メモ

リファレンスに記載の内容を試してみたり、疑問になった点をメモ

## TODO

* bundletool 使ってみる
* Play Console 使ってみる

## 実際に試したこと

### 署名時に誤った情報を渡したらどうなる？

#### パスワードが誤っている

```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:packageReleaseBundle'.
> java.util.concurrent.ExecutionException: java.lang.RuntimeException: jarsignerfailed with exit code 1 :
  jarsignerエラー: java.lang.RuntimeException: キーストアのロード: Keystore was tampered with, or password was incorrect

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org
```

#### エイリアスが誤っている

```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:packageReleaseBundle'.
> java.util.concurrent.ExecutionException: java.lang.RuntimeException: jarsignerfailed with exit code 1 :
  jarsigner: 次の証明書チェーンが見つかりません: androiddebugkeystore。androiddebugkeystoreは、秘密鍵および対応する公開鍵証明書チェーンを含む有効なKeyStore鍵エントリを参照する必要があります。

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org
```

#### `bundletool get-device-spec`

* --output オプションが必須
* --output で指定したファイルがすでに存在している場合は失敗する
```
[BT:0.4.1] Error: File 'emulator.json' already exists.
java.lang.IllegalArgumentException: File 'emulator.json' already exists.
	at com.google.common.base.Preconditions.checkArgument(Preconditions.java:204)
	at com.android.tools.build.bundletool.utils.files.FilePreconditions.checkFileDoesNotExist(FilePreconditions.java:32)
	at com.android.tools.build.bundletool.commands.GetDeviceSpecCommand.execute(GetDeviceSpecCommand.java:137)
	at com.android.tools.build.bundletool.BundleToolMain.main(BundleToolMain.java:80)
	at com.android.tools.build.bundletool.BundleToolMain.main(BundleToolMain.java:44)

```

## 疑問に思ったこと

* .aab が署名されているかどうかはどうやって確認する？
  * .apk の場合は、`jarsigner -verify -verbose -certs hoge.apk`
* internal test track を実案件でどう運用するのがよいか？
  * 署名ファイルは何をもらっておけばよいか？
  * クライアント側では何をしてもらう必要があるのか？
* 端末が日本語設定でアプリをインストール後、英語に設定変更した場合、英語用のリソースはどうやってダウンロードされる？
* CI サーバで、bundletool をどうやって管理すべきか？
