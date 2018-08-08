<template>
  <footer>
      <div class="links">
        <div class="links-wrapper">
            <a href="#">Помощь</a>
            <a href="#">Обратная связь</a>
            <a href="#">Разработчикам</a>
            <a href="#">Условия использования</a>
        </div>
      </div> 
      <span class="copyright">
         © 2001–2017  ООО «Яндекс»
      </span>
  </footer>
</template>
<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
footer {
  display: flex;
  justify-content: space-between;
  padding: 20px $appHorizontalPadding 25px $appHorizontalPadding;
  @media #{$mobile} {
    padding: 20px $mobileHorizontalPadding 25px $mobileHorizontalPadding;
    flex-direction: column;
  }
}
.links {
  overflow: hidden;
  &-wrapper {
    margin: -6px;
    display: flex;
    @media screen and (max-width: 700px) {
      flex-direction: column;
      margin-bottom: 30px;
    }
    a {
      margin: 6px;
      font-family: $fontFamily;
      font-size: 12px;
      color: #858585;
      letter-spacing: 0.01px;
      text-align: left;
      text-decoration: none;
    }
  }
}
.copyright {
  font-family: $fontFamily;
  font-size: 12px;
  color: #858585;
  letter-spacing: 0.01px;
  text-align: left;
}
</style>
