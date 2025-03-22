```html
<html>
  <body>
    <button 
      class="mobile-menu-icon"
      onclick="document.querySelector('body').classList.toggle('menu-open')"
     >
      <span></span>
      <span></span>
      <span></span>
    </button>
  </body>
</html>
```
```scss
/* STEP1. 入れ物としてbutton要素 */
.mobile-menu-icon {
  /* ButtonのDefaultのスタイル(黒枠グレー背景色)を消す */
  background-color: transparent; /* none ではなく transparent */
  border: none;
  cursor: pointer;
  
  /* STEP2. 3本の黒線のスタイル */
  & > span {
    background-color: black;
    width: 35px;
    height: 2px;
    display: block;
    margin-bottom: 9px;
    
    &:last-child {
      margin-bottom: 0px;
    }
    
    transition: 0.5s all;
    
  }
}

/* STEP3. Clickしたらこのクラスを付与してスタイル変更 */
.menu-open {
  background-color: black;
  
  & .mobile-menu-icon {
    & > span {
      background-color: white;
      
      /* STEP4. ３本の棒のトランジションを定義 */
      &:nth-child(1) {
        /* 
          真ん中の高さに移動 -> translateY(11px)
          回転 -> rotate(135deg)
        */
        transform: translateY(11px) rotate(135deg); 
      }
      
      &:nth-child(3) {
        /* 
          真ん中の高さに移動 -> translateY(-11px)
          回転 -> rotate(-135deg)
        */
        transform: translateY(-11px) rotate(-135deg);
      }
      
      &:nth-child(2) {
        /* 左側に消えていくように */
        /* ・左側にスライド -> translateX(-18px)
           ・消えていく -> scale(0)
        */
        transform: translateX(-18px) scale(0);
      }
      
    }
  }
}
```