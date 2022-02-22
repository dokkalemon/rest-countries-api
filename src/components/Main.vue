<template>
    <main class="full-width" :class="{light: color}">
        <div class="main container px-30">
            <Card 
            v-for="(item, index) in countryArray" :key="`country-${index}`"
            :name="item.name"
            :flag="item.flag"
            :population="item.population"
            :region="item.region"
            :capital="item.capital"
            @activeState="activeFunctionCard"
            class="country-info"
            />

            <CountryInfo v-show="selectedCountry.length = 1" :activeState="active" @noActiveState="noActive"
            :selectedCountryObj="selectedCountry" :borderCountryArray="borderCountry"
            @activeState="activeFunctionCountryInfo" :color="color"
            />
            
        </div>
    </main>
</template>

<script>
import Card from '@/components/Card.vue'
import CountryInfo from '@/components/CountryInfo.vue'


export default {
    name: 'Main',
    components: {
        Card,
        CountryInfo
    },

    props: {
        countryArray: Array,
        allMainCountry: Array,
        color: Boolean
    },

    data() {
        return {
            active: false,
            selectedCountry: {},
            borderCountrySigle: [],
            borderCountry: []
            
            
        }
    },

    methods: {
        activeFunctionCard(dato) {
            this.active = true;
            this.getCountry(dato, this.countryArray)
        },

        activeFunctionCountryInfo(dato) {
            this.active = true;
            this.getCountry(dato, this.allMainCountry)
        },

        noActive() {
            this.active = false;
        },

        //select a country from array
        getCountry(country, array) {
            for (let i = 0; i < array.length; i++) {
                if (country.toLowerCase().includes(array[i].name.toLowerCase())) {
                    this.selectedCountry = array[i];
                    this.borderCountry = [];
                    this.getBorders(i, array)
                }
            }
        },

        //add country borders in a variable
        getBorders(state, array) {
                if (array[state].borders !== undefined) {
                    this.borderCountrySigle = array[state].borders;
                    this.transformBorders()
                } else {
                    this.borderCountrySigle = undefined;
                }
        },

        //trasform alpha3Code to Country Name
        transformBorders() {
            for (let i = 0; i < this.borderCountrySigle.length; i++) {
                for (let j = 0; j < this.allMainCountry.length; j++) {
                    if (this.borderCountrySigle[i] === this.allMainCountry[j].alpha3Code) {
                        this.borderCountry.push(this.allMainCountry[j].name)
                    }
                }
            }            
        }
    }
}





</script>

<style scoped lang="scss">
//import var.scss
@import '../styles/var.scss';

.main {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
}

.light {
    background-color: $light-back;
}

@media screen and (max-width: 375px) {
    .main {
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-items: center;
    }
}




</style>