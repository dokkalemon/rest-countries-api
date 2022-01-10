<template>
    <main class="full-width">
        <div class="main container px-30">
            <Card v-for="(item, index) in arrayCountry" :key="`state-${index}`"
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


export default {
    name: 'Main',
    components: {
        Card
    },

    props: {
        arrayCountry: Array
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