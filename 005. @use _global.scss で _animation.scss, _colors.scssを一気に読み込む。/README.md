### マスタ定義的なscssファイルを作る
- animation用のmixin -> `_animation.scss`
- テーマ色定義用 -> `_colors.scss`

これらを各ファイルから毎回以下のように読み込むのは冗長。
```scss
@use 'animation' as a;
@use 'colors' as c;
```
**1つのファイルを@useで読み込めば全部読み込めれば楽だな -> 共通の名前空間を作ってあげる。**<br>

以下 `_global.scss`を定義。
```scss
@forward "animation";
@forward "colors";
```

各ファイルからは`_global.scss`を読み込むだけで、`_animation.scss`も`_colors.scss`も読み込める👍
```scss
@use "global" as *;
```