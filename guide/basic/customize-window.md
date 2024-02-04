# ウィンドウをカスタマイズする

ウィンドウのサイズやタイトルバーのテキストを変更したり、フルスクリーンにしたりと、細かい設定を行うための方法を示します。

前回、コンソールの機能を使うために `ConsoleLayer` のインスタンスをシーンのコンストラクタで受け取りました。同様に、ウィンドウの機能を使うために `IWindow` のインスタンスを引数に追加するように書き換えましょう。

`MainScene.cs` を次のように書き換えてください。


```csharp
using Promete;
using Promete.Windowing;// [!code ++]

public class MainScene(ConsoleLayer console) : Scene// [!code --]
public class MainScene(ConsoleLayer console, IWindow window) : Scene// [!code ++]
{
    public override void OnStart()
    {
        console.Print("Hello, world!");
    }
}
```

## サイズを変更する

まずはウィンドウのサイズを変更してみましょう。`OnStart` メソッドの中に処理を追加します。

```cs
window.Size = (300, 300);
```

この状態でビルドして実行すると、ウィンドウのサイズが変更されていることが確認できます。

![リサイズされたウィンドウ](/assets/resized-window.png)

## タイトルバーのテキストを変更する

次に、FPS（秒間フレーム数）をタイトルバーに表示してみましょう。FPSは常に変動する値なので、毎フレームごとに取得および表示したいですね…。

これまで `OnStart` メソッドの中に処理を記述していましたが、ここで `OnUpdate` メソッドをオーバーライドし、処理を記述していきます。

`MainScene` クラスに `OnUpdate` メソッドを追加します。

```csharp
public override void OnUpdate()
{
    window.Title = $"{window.FramePerSeconds} fps";
}
```

これで、毎フレームごとにタイトルバーのテキストが更新されるようになります。

![FPSを表示したウィンドウ](/assets/fps-window.png)

他にも、ウィンドウの位置を変更したり、フルスクリーンにしたりと、さまざまなカスタマイズが可能です。詳しくは[APIリファレンス](/api/Promete.Windowing.IWindow)を参照してください。

さて、次のページでは、いよいよ好きな画像をウィンドウ上に表示するための方法を説明します！
