---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# Flutter環境構築

<!-- Presentation slides for developers -->

<!-- <div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div> -->

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# 目次

<br/>
<br/>

- 導入
- 環境構築の流れ
- アプリの立ち上げ
- まとめ


<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
ul {
  font-size: 24px;
}
</style>

<!--
Here is another comment.
-->

---
transition: slide-up
level: 2
---

# 導入

<br>

#### ＜目的＞
環境構築が面倒でFlutterを触るところまでいかない。

→「環境構築からアプリが立ち上がるところまで確認しよう！」

<br>

#### ＜本日のゴール＞

<br>

- 環境構築の流れを知る
- セットアップ後に動作確認する方法を知る


<style>
  h4 {
    font-weight: bold;
  }
</style>

---

# 環境構築の流れ

- FlutterSDKをインストール<br>
- Android Studioのインストール
- Xcodeのインストール

<br>

（GitとVSCodeのインストールが前提）

<br>

・ macOSの場合は[こちら](https://zenn.dev/flutteruniv/books/flutter-textbook/viewer/get-started)を参考に
<br>
・Windowsの場合は[こちら](https://zenn.dev/kazutxt/books/flutter_practice_introduction/viewer/06_chapter1_environment)を参考に

---


# FlutterSDKのインストール

- 公式サイトからFlutterSDKをインストール<br>
　- プラットフォームの選択 → https://gyazo.com/8ddc41827d702c8d42f65da1e0861614<br>
　- デバイスの選択 → https://gyazo.com/62f51b217afd1940468e91a067622f78<br>
　- SDKのインストール → https://gyazo.com/b8b3a377966ca4e07300dcdca9f9fb3a<br>
　- ホーム直下に「~/development/」フォルダを作成し、解凍したflutterフォルダを配置<br>

```zsh
  ~/development/
    flutter
```
　　 - Flutterの実行確認とパスの設定

  ```zsh
    ~/development/flutter/bin/flutter --version

    // zshの場合
    echo export PATH=\"\$PATH:\$HOME/development/flutter/bin\" >> ~/.zshrc
    source ~/.zshrc

    // bashの場合
    echo export PATH=\"\$PATH:\$HOME/development/flutter/bin\" >> ~/.bash_profile
    source ~/.bash_profile
  ```

---


# FlutterSDKのインストール

- Apple Siliconの場合はRosetta2のインストールも必要

```zsh
sudo softwareupdate --install-rosetta --agree-to-license
```

---


# Android Studioのインストール

- `flutter doctor`で開発環境の情報を出力し、必要事項をチェックしていく。(https://gyazo.com/2c8d2abcc651ca9dbb9d20100e498be1)

- [こちら](https://codeforfun.jp/how-to-install-android-studio-windows-and-mac/)を参考にAndroid Studioをインストール（https://developer.android.com/studio）<br>
　- SDK Managerを選択 (https://gyazo.com/7e4c22bbab016e53de30e962bf3fc911)<br>
　- SDK ToolsからAndroid SDK Command-line toolを選択し、applyする (https://gyazo.com/1994564f905bfa9d95e4601216ae1801)<br>
　- licenseエラーの対応 → `flutter doctor --android-licenses`を行い、同意操作をyで進める。
　- `flutter doctor`を再度行い、チェックがついたらOK

```
[!] Android toolchain - develop for Android devices (Android SDK version 32.1.0-rc1)
! Some Android licenses not accepted. To resolve this, run: flutter doctor --android-licenses
```

---

# Xcodeのインストール

- こちらも同様に、`flutter doctor`で開発環境の情報を出力し、必要事項をチェックしていく。(https://gyazo.com/2c8d2abcc651ca9dbb9d20100e498be1)

- Mac App Storeからインストール（https://apps.apple.com/jp/app/xcode/id497799835?mt=12）<br>
（[開発者向けサイト](https://developer.apple.com/download/applications/)からバージョンを選んでダウンロード）<br>
　- インストール後、下記コマンドを実行

```zsh
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer // コマンドラインツールのディレクトリ指定
sudo xcodebuild -runFirstLaunch // Xcode関連パッケージのインストール
sudo xcodebuild -license // ライセンスの同意

xcodebuild -downloadPlatform iOS // シミュレータのインストール

sudo gem install cocoapods // CocoaPodsのインストール
```

<br>

- `flutter doctor`を再度行い、チェックがついたらOK


---

# エミュレータの立ち上げ

- Android Studioで[View Device Manager](https://gyazo.com/a90d04f78f70394738a1f133a737b50d)を開く
- [+ボタン](https://gyazo.com/d18153f70215d8583a42469d835a47e9)からエミュレータの追加を行う
- [デバイス](https://gyazo.com/2a59d75f3a128ab316681bfee7fcbdc9)を選択する
- [APIバージョン](https://gyazo.com/dd008431d17a5f363f24014323047427)を選択する
- [設定情報](https://gyazo.com/6108f9afcc2bfe292db8aa5d0f74f266)を確認して終了
- 立ち上げたいエミュレータで[三角ボタン](https://gyazo.com/dacb67f874fe1deaf4f17bcb3cd1994b)を押す


---

# Flutterアプリの作成

- `flutter create アプリ名`
　- https://gyazo.com/e00f289388f92b69d341051f49e3e186
- [エミュレータ](https://gyazo.com/4476d751ae19c6b6490ade6d4b7ce511)が立ち上がっていることを確認
- `flutter run`
- エミュレータでアプリが起動したことを確認 https://gyazo.com/f79b54b2b71c574c09743f9a8988c66f


---

# 参考

- https://zenn.dev/flutteruniv/books/flutter-textbook/viewer/get-started
- https://zenn.dev/kazutxt/books/flutter_practice_introduction/viewer/06_chapter1_environment
- https://codeforfun.jp/how-to-install-android-studio-windows-and-mac/
- https://qiita.com/ch0c0bana0/items/36ea0fb9d6857f6dac5e
- https://zenn.dev/peter_norio/articles/22d17e9ae33ab3
- [Flutter実践開発](https://www.amazon.co.jp/Flutter%E5%AE%9F%E8%B7%B5%E9%96%8B%E7%99%BA-%E2%94%80%E2%94%80-iPhone%EF%BC%8FAndroid%E4%B8%A1%E5%AF%BE%E5%BF%9C%E3%82%A2%E3%83%97%E3%83%AA%E9%96%8B%E7%99%BA%E3%81%AE%E3%83%86%E3%82%AF%E3%83%8B%E3%83%83%E3%82%AF-%E6%B8%A1%E9%83%A8-%E9%99%BD%E5%A4%AA/dp/4297139936)

---

おわり