<template>
  <div id="app" class="app">
    <Header/>
    <Setting/>
    <Main :countryArray="allCountry"/>

  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Setting from '@/components/Setting.vue'
import Main from '@/components/Main.vue'
/* import axios from 'axios' */

export default {
  name: 'App',
  components: {
    Header,
    Setting,
    Main
  },

    created() {
        this.getCountry();
    },

    data() {
        return {
            allCountry: [],
            
        }
    },

    computed: {
   

    },
      

    methods: {
    



    







    },





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

}

.active {
  background-color: $light-back;
}

</style>
