<template>
    <main class="full-width">
        <div class="main container px-30">
            <Card />
            
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