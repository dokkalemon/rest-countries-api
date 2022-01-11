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
            
            />

            <CountryInfo :activeState="active" @noActiveState="noActive"/>
            
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
        countryArray: Array
    },

    data() {
        return {
            active: false,
            proof: '',
        }
    },

    methods: {
        activeFunction(dato) {
            this.active = dato;
        },

        noActive(dato) {
            this.active = dato;
            console.log(dato);
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
    justify-content: start;
}


</style>