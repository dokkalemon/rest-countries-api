<template>
    <section class="card ">
        <div class="card-container">
            <div class="flag">
                <img :src="flag" alt="">
            </div>

            <div class="info">
                <div class="name">
                    <h4>{{name}}</h4>
                </div>
                <div class="other">
                    <p>Population: <span>{{population}}</span></p>
                    <p>Region: <span>{{region}}</span></p>
                    <p>Capital: <span>{{capital}}</span></p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Card',
    props: {
        name: String,
        flag: String,
        population: Number,
        region: String,
        capital: String,
    }
}
</script>

<style scoped lang="scss">
//import vars.scss
@import '../styles/var.scss';

.card {
    width: calc(100% / 4);
    height: 310px;
    margin-bottom: 70px;
    padding: 0px 35px;
    .card-container {
        cursor: pointer;
        background-color: $dark-element;
        height: 100%;
        width: 100%;
        border-radius: 5px;
        overflow: hidden;
        .flag {
            height: 150px;
            width: 100%;
            img {
                height: 100%;
                width: 100%;
                object-fit: cover;
            }
        }
        .info {
            height: 100%;
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            margin-left: 10px;
            .name {
                h4 {
                    color: $dark-text;
                    font-weight: 600;
                    font-size: 18px;
                    margin-bottom: 10px;
                }
            }
            .other {
                p {color: $dark-text; font-weight: 600; font-size: 14px}
                span {font-weight: 300;}
            }
        }
    }
}





</style>