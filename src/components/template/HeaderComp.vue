<template>
  <header>
    <div class="menuesquerdo">
      <span> <RouterLink to="/">Home</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/times">Times</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/jogadores">Jogadores</RouterLink></span>
    </div>
    <div class="menudireito">
      <span class="item-sair">Sair</span>
    </div>
  </header>
</template>
<style>
header {
  height: 10%;
  background-color: rgb(82, 65, 94);
  color: rgb(252, 244, 244);
  font-size: 1.3em;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 20px;
}
header span {
  padding: 0 20px;
}
</style>
