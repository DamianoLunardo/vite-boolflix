<script setup>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


const components = {
    AppHeader,
    AppMain
}
</script>

<template>
    <div class="container">
 <AppHeader />
<AppMain />       
    </div>

</template>

<style lang="scss">
@use './styles/general.scss' as *;

</style>
