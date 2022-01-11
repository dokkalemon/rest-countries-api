<template>
    <section class="info" :class="{active: activeState}">
        <div class="info-container container px-30">
            <div class="back">
                <button @click="$emit('noActiveState', false)"><i class="fas fa-arrow-left"></i> Back</button>
            </div>

            <div class="info-country">
                <div class="flag">
                    <img :src="flag" alt="">
                </div>

                <div class="text">
                    <div class="title">
                        <h2>{{name}}</h2>
                    </div>

                    <div class="info-text">
                        <div class="item-info">
                            <p>Native Name: <span>Belgie</span></p>
                            <p>Population: <span>11319511</span></p>
                            <p>Region <span>Europe</span></p>
                            <p>Sub Region: <span>Western Europe</span></p>
                            <p>Capital: <span>Brussels</span></p>
                        </div>
                        <div class="item-info">
                            <p>Top Level Domain: <span>.be</span></p>
                            <p>Currencies: <span>Euro</span></p>
                            <p>Languages: <span>Dutch, French, German</span></p>
                        </div>
                    </div>
                    <div class="countries-border">
                        <h4>Border Countries: </h4>
                        <button>France</button>
                        <button>Germany</button>
                        <button>Netherlands</button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'CountryInfo',
    props: {
        activeState: Boolean,
        name: String,
        flag: String,
    }
}
</script>

<style scoped lang="scss">
//import var
@import '../styles/var.scss';

.info {
    position: fixed;
    height: 100vh;
    width: 100%;
    background-color: $dark-back;
    top: 0;
    left: -110%;
    padding-top: 100px;
    transition: all 0.5s ease;
    .info-container {
        .back {
            button {
                background-color: $dark-element;
                border: none;
                padding: 15px 45px;
                color: white;
                border-radius: 10px;
                box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.219);
                cursor: pointer;
                transition: all 0.5s ease;
                font-size: 16px;
                i {
                    margin-right: 10px;
                }
                &:hover {
                    background-color: rgba(255, 255, 255, 0.139);
                }
            }
        }
        .info-country {
            margin-top: 70px;
            display: flex;
            .flag {
                height: 370px;
                width: 515px;
                img {
                    height: 100%;
                    width: 100%;
                    object-fit: cover;
                }
            }
            .text {
                margin-left: 100px;
                padding: 10px;
                .title {
                    h2 {
                        color: white;
                        font-weight: 600;
                        font-size: 35px;
                    }
                }
                .info-text {
                    display: flex;
                    .item-info {
                        margin-right: 100px;
                        margin-top: 20px;
                        p {color: white; 
                        font-weight: 600; 
                        font-size: 14px;
                        line-height: 30px;
                        span {font-weight: 300;}
                        }
                        &:last-child {margin-right: 0;}
                    }
                }
                .countries-border {
                    margin-top: 50px;
                    display: flex;
                    align-items: center;
                    h4 {
                        color: white;
                        font-weight: 600;
                        font-weight: 14px;
                    }
                    button {
                        background-color: $dark-element;
                        border: none;
                        padding: 5px 15px;
                        margin-left: 10px;
                        margin-right: 10px;
                        box-shadow: 0 0 10px rgba(0, 0, 0, 0.139);
                        cursor: pointer;
                        transition: all 0.5s ease;
                        color: $dark-text;
                        &:hover {
                            background-color: rgba(255, 255, 255, 0.139);
                        }
                    }
                }
            }
        }
    }
}

.active {
    left: 0;
}

</style>