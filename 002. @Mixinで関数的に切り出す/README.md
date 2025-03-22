## @Mixin -> StyledComponent的な感じ。関数に切り出す。
```html
<html>
  <body>
    <div class="three-dot-spinner">
      <div class="bounce1"></div>
      <div class="bounce2"></div>
      <div class="bounce3"></div>
    </div>
  </body>
</html>
```
```scss
/* STEP1. Mixin関数定義 */
@mixin customAnimation(
  $name,
  $duration: 1s, /* デフォルト値 */
  $iteration-count: infinite /* デフォルト値 */
){  
  animation-name: $name;
  animation-duration: $duration;
  animation-iteration-count: $iteration-count;
}

.three-dot-spinner {
  text-align: center;
    
  & div {
    display: inline-block;
    width: 18px;
    height: 18px;
    background-color: black;
    border-radius: 50%;
    /* STEP2. Mixin関数は@includeで呼び出す */
    @include customAnimation(
      $name: sk-bouncedelay
    );
  }
  
  & .bounce1 {
    animation-delay: -0.32s; /*他より0.32秒早く開始*/
  }
  & .bounce2 {
    animation-delay: -0.16s; /*他より0.32秒早く開始*/
  }
  
}

/* STEP3. Animationを定義する */
@keyframes sk-bouncedelay {
  from, 80%, to {
    transform: scale(0);
  }
  40% {
    transform: scale(1);
  }
}
```