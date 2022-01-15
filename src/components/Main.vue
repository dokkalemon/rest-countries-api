<template>
    <main class="full-width">
        <div class="main container px-30">
            <Card 
            v-for="(item, index) in countryArray" :key="`country-${index}`"
            :name="item.name"
            :flag="item.flag"
            :population="item.population"
            :region="item.region"
            :capital="item.capital"
            @activeState="activeFunction"
            class="country-info"
            />

            <CountryInfo v-show="selectedCountry.length = 1" :activeState="active" @noActiveState="noActive"
            :selectedCountryObj="selectedCountry"
            />
            
        </div>
    </main>
</template>

<script>
import Card from '@/components/Card.vue'
import CountryInfo from '@/components/CountryInfo.vue'
/* import axios from 'axios' */

export default {
    name: 'Main',
    components: {
        Card,
        CountryInfo
    },

    created() {
       this.getCountry('italy')
    },

    props: {
        countryArray: Array,
    },

    data() {
        return {
            active: false,
            selectedCountry: {},
            prova: [],
        }
    },

    methods: {
        activeFunction(dato) {
            this.active = true;
            this.getCountry(dato)

        },

        noActive() {
            this.active = false;
        },

        getCountry(country) {
                      for (let i = 0; i < this.countryArray.length; i++) {
                if (country.toLowerCase().includes(this.countryArray[i].name.toLowerCase())) {
                    this.selectedCountry = this.countryArray[i]

                }  
            }    
        },
    }
}





</script>

<style scoped lang="scss">
//import var.scss
@import '../styles/var.scss';

.main {
    display: flex;
    flex-wrap: wrap;
    justify-content: start;
}


</style>