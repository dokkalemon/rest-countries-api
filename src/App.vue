<template>
  <div id="app" class="app" :class="{light: lightMode}">
    <Header @colorChange="changeColor" :color="lightMode"/>
    <Setting @filteredContinent="takeFilterContinent" @filterCountry="inputCountry" :color="lightMode" />
    <Main :countryArray="filteringCountry" :allMainCountry="allCountry" :color="lightMode"/>
    <Warning v-show="filteringCountry.length === 0" :color="lightMode"/>

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
            lightMode: false,
            
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
      },

      //Change Color
      changeColor() {
        if (this.lightMode === false) {
          this.lightMode = true
        } else {
          this.lightMode = false
        }
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

.light {
  background-color: $light-back
}

.active {
  background-color: $light-back;
}

</style>
