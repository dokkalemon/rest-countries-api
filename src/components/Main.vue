<template>
    <main class="full-width">
        <div class="main container px-30">
            <Card v-for="(item, index) in country" :key="`state-${index}`"
            :name="item.name"
            :population="item.population"
            :region="item.region"
            :capital="item.capital"
            :flag="item.flag"
            />
            
        </div>
    </main>
</template>

<script>
import Card from '@/components/Card.vue'
import axios from 'axios';

export default {
    name: 'Main',
    components: {
        Card
    },

    created() {
        this.getCountry()
    },

    data() {
        return {
            country: [],
        }
    },

    methods: {
        getCountry() {
            axios.get('https://restcountries.com/v2/all')
            .then(result=>{
                this.country = result.data;
                console.log(this.country);
            })

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