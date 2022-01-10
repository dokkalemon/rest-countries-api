<template>
  <div id="app" class="app">
    <Header />
    <Setting @search="takeCountry"/>
    <Main :arrayCountry="filterCountry"/>

  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Setting from '@/components/Setting.vue'
import Main from '@/components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Setting,
    Main
  },

    created() {
        this.getCountry()
    },

    data() {
        return {
            country: [],
            searchedCountry: '',
            setContinent: '',
        }
    },

    computed: {

      filterCountry() {
        if (this.searchedCountry === '') {
          return this.country
        }

        return this.country.filter( item => {
          return item.name.toLowerCase().includes(this.searchedCountry.toLowerCase())
        })
      }

    
 
    },

    methods: {
        getCountry() {
            axios.get('https://restcountries.com/v2/all')
            .then(result=>{
                this.country = result.data;
            })
            .catch(err=>{
            console.log(err);
          })
        },

        takeCountry(dato) {
          this.searchedCountry = dato;
        },

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
