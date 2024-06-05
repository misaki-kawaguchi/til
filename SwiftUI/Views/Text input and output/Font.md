# Font

## Fontサイズ

```
struct ContentView: View {
    var body: some View {
        VStack {
            // タイトル
            Text("largeTitle").font(.largeTitle) // 34pt
            Text("title").font(.title) // 28pt
            Text("title2").font(.title2) // 22pt
            Text("title3").font(.title3) // 20pt

            // 見出し
            Text("headline").font(.headline) //
            Text("subheadline").font(.subheadline) // 15pt

            // 本文
            Text("body").font(.body) // 17pt

            // 吹き出し
            Text("callout").font(.callout) // 16pt

            // キャプション
            Text("caption").font(.caption) // 12pt
            Text("caption2").font(.caption2) // 11pt

            // 脚注
            Text("footnote").font(.footnote) // 13pt
        }
        .padding()
    }
}

```

<div align="center">
    <img src ="https://github.com/misaki-kawaguchi/til/assets/60394359/92d40bf5-0893-4cab-be15-9480fe7f030c" width=33%>
</div>
