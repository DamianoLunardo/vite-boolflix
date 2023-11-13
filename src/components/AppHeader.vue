<script>
import { store } from "../store";

export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container">
    <div class="header">
      <div class="title">BOOLFLIX</div>
      <div class="nav-bar">
        <ul class="nav-list">
          <li><a href="#">Home</a></li>
          <li><a href="#">Serie TV</a></li>
          <li><a href="#">Film</a></li>
          <li><a href="#">Originali</a></li>
          <li><a href="#">Aggiunti di recente</a></li>
          <li><a href="#">La mia lista</a></li>
        </ul>
      </div>
      <div>
        <input v-model="store.query" type="text" placeholder="Cerca..." />
      </div>
    </div>
  </div>
</template>

<style lang="scss">

.header {
  display: flex;
  justify-content: space-between;
  padding-top: 40px;
}

.title {
  color: red;
  font-size: 30px;
  font-weight: bold;
}
.nav-list {
  list-style: none;
  display: flex;
  align-items: center;
  text-align: center;
}

a {
  text-decoration: none;
  color: white;
  padding: 0 5px;
  font-weight: bold;
  font-size: 10px;
  &:hover {
    color: red;
}
}

</style>
