<template>
  <div>
    <header>
      <h1>Calculator</h1>
      <span class="author">BY <a href="#" target="_blank">Tirmisu</a></span>
    </header>
    <main class="main" id="main">
      <calc></calc>
    </main>
  </div>
</template>

<script>
import calc from "./views/calc.vue";
export default {
  components: { calc },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Pacifico');

html {
  font-size: 62.5%;  /* =10px*/
}

body {
  background-color: #f4f1f1;
}

header {
  font-size: 1.8rem;
  font-family: 'Pacifico', cursive;
}

header .author {
  font-size: 1.5rem;
}

header .author a {
  text-decoration: none;
}

header, .main {
  margin: 4rem auto;
  text-align: center;
}

.main {
  border: .8rem solid #f67373;
  width: 34rem;
  height: 44rem;
  font-size: 1.6rem;
  border-radius: 1rem;
  background-color: #f67373;
  box-shadow: 1rem 1rem .5rem #ccc;
}

</style>

<style lang="less" scoped>

</style>
