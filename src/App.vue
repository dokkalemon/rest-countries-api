<template>
  <div id="app">
    <Header />
    <Setting />
    
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Setting from '@/components/Setting.vue'

export default {
  name: 'App',
  components: {
    Header,
    Setting
  
  }
}
</script>

<style lang="scss">
//importa global.scss
@import './styles/global.scss'

</style>
