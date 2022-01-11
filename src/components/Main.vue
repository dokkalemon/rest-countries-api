<template>
    <main class="full-width">
        <div class="main container px-30">
            <Card v-for="(item, index) in countryArray" :key="`country-${index}`"
            :name="item.name"
            :flag="item.flag"
            :population="item.population"
            :region="item.region"
            :capital="item.capital"
            />
            
        </div>
    </main>
</template>

<script>
import Card from '@/components/Card.vue'


export default {
    name: 'Main',
    components: {
        Card
    },

    props: {
        countryArray: Array
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