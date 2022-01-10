<template>
  <div id="app" class="app">
    <Header />
    <Setting />
    <Main />

  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Setting from '@/components/Setting.vue'
import Main from '@/components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Setting,
    Main
  },

  data() {
    return {
    
    }
  }




}
</script>

<style lang="scss">
//importa global.scss
@import './styles/global.scss';

//import var.scss
@import './styles/var.scss';

.app {
  min-height: 100vh;
  background-color: $dark-back;
  border: 1px solid red;
}

.active {
  background-color: $light-back;
}

</style>
