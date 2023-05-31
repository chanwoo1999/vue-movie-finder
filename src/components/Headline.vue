<template>
  <div class="container">
    <h1>
      <span>MOVIE FINDER</span><br />
      THE OPEN<br />
      MOVIE DATABASE
    </h1>
    <p>
      <strong>"MOVIE FINDER"</strong> 에서 당신이 찾던 모든 영화/시리즈/에피소드를 검색해보세요!
    </p>
  </div>
</template>

<style lang="scss" scoped>
@import "~/scss/main";

.container {
  padding-top: 40px;
}
h1 {
  line-height: 1;
  font-family: "Oswald";
  font-size: 80px;
  text-align: center;
  color: $white;
  span {
    color: $primary;
    text-align: center;
    font-size: 120%;
  }
}
p {
  text-align: center;
  margin: 30px 0;
  color: $white;
}
</style>