<template>
  <div id="app" class="app">
    <Header/>
    <Setting @filteredContinent="takeFilterContinent" @filterCountry="inputCountry" />
    <Main :countryArray="filteringCountry"/>
    <Warning v-show="filteringCountry.length === 0"/>

  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Setting from '@/components/Setting.vue'
import Main from '@/components/Main.vue'
import Warning from '@/components/Warning.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Setting,
    Main,
    Warning
  },

    created() {
        this.getCountry();
        
    },

    data() {
        return {
            allCountry: [],
            continentFilter: '',
            countryFilter: '',
            
        }
    },

    computed: {
        filteringContinent() {
          if (this.continentFilter === '') {
            return this.allCountry
          }

          return this.allCountry.filter( item => {
            return item.region.toLowerCase().includes(this.continentFilter.toLowerCase())
          })
        },

        filteringCountry() {
          if (this.countryFilter === '') {
            return this.filteringContinent
          }

          return this.filteringContinent.filter( item => {
            return item.name.toLowerCase().includes(this.countryFilter.toLowerCase())
          })

        }




    },
      

    methods: {

      //take data from API
      getCountry() {
        axios.get('https://restcountries.com/v2/all')
        .then(result=>{
          this.allCountry = result.data;
        })
        .catch(err=>{
          console.log(err);
        })
      },

      //take a filter for continent
      takeFilterContinent(dato) {
        this.continentFilter = dato;
      },


      //take a user input country
      inputCountry(dato) {
        this.countryFilter = dato
      }






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
