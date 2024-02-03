# 画像ファイルを画面に表示する

前回、ようやく画面に何かを表示するという偉業を成し遂げました。とはいえ、やはり文字だけというのは寂しいですよね…。今回は、画像ファイルを読み込んで画面に表示する方法を学びます。

好きな画像を用意してください。もしなければ、次の画像をダウンロードしてください。

[![いちご](/assets/ichigo.png)](/assets/ichigo.png)

画像をプロジェクトファイルに追加します。この例では、 `assets` フォルダに `ichigo.png` という名前で保存します。

::: warning
標準では、ビルド時に出力ディレクトリに画像ファイルはコピーされません。画像ファイルを出力ディレクトリにコピーするには、プロジェクトファイルに次のような設定を追加するか、お使いのIDEでファイルのプロパティを適切に設定してください。

```xml
<ItemGroup>
  <None Update="assets\ichigo.png">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
</ItemGroup>
```
:::
