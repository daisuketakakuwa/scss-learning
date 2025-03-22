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

@mixin customAnimation(
  $name,
  $duration: 1s,
  $iteration-count: infinite
){
  /* 共通のPREFIX animation- 部分を省略できる。 */
  animation: {
    name: $name;
    duration: $duration;
    iteration-count: $iteration-count;
  }
}

.three-dot-spinner {
  text-align: center;
    
  & div {
    display: inline-block;
    width: 18px;
    height: 18px;
    background-color: black;
    border-radius: 50%;
    /* STEP1. Animationさせたい要素に定義 */
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

/* STEP2. Animationを定義する */
@keyframes sk-bouncedelay {
  from, 80%, to {
    transform: scale(0);
  }
  40% {
    transform: scale(1);
  }
}

```