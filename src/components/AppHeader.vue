<script>
import { store } from '../store';

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
</style>
