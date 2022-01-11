<template>
  <div id="app" class="app">
    <Header/>
    <Setting @selectContinent="filterByContinent" @selectingCountry="userCountry"/>
    <Main :countryArray="filterCountry"/>

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
        this.getCountry();
    },

    data() {
        return {
            allCountry: [],
            selectCountry: [],
            userCountrySelect: '',
        }
    },

    computed: {
      //filtered the country by the input
      filterCountry() {
        if (this.userCountrySelect === '') {
          return this.selectCountry
        }

        return this.selectCountry.filter(item => {
          return item.name.toLowerCase().includes(this.userCountrySelect.toLowerCase())
        })

      }


    },
      

    methods: {
      //take a data from API
      getCountry() {
        axios.get('https://restcountries.com/v2/all')
        .then(result=>{
          this.allCountry = result.data;

          for (let i = 0; i < this.allCountry.length; i++) {
            this.selectCountry.push(this.allCountry[i])
          }
        })
        .catch(err=>{
          console.log(err);
        })
      },


      //Filter Country by Continent
      filterByContinent(dato) {

         this.selectCountry = [];
        for (let i = 0; i < this.allCountry.length; i++) {
          
          if (this.allCountry[i].region.toLowerCase() === dato) {
            this.selectCountry.push(this.allCountry[i])
          }
        } 
      },

      //take info from input with emit
      userCountry(dato){
        this.userCountrySelect = dato;
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
