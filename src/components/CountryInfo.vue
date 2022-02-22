<template>
    <section class="info" :class="{active: activeState, light: color}">
        <div class="info-container container px-30">
            <div class="back">
                <button @click="$emit('noActiveState', false)"><i class="fas fa-arrow-left"></i> Back</button>
            </div>
            <div class="info-country">
                <div class="flag">
                    <img :src="selectedCountryObj.flag" alt="">
                </div>
                <div class="text">
                    <div class="title">
                        <h2>{{selectedCountryObj.name}}</h2>
                    </div>
                    <div class="info-text">
                        <div class="item-info">
                            <p>Native Name: <span>{{selectedCountryObj.nativeName}}</span></p>
                            <p>Population: <span>{{selectedCountryObj.population}}</span></p>
                            <p>Region <span>{{selectedCountryObj.region}}</span></p>
                            <p>Sub Region: <span>{{selectedCountryObj.subregion}}</span></p>
                            <p>Capital: <span>{{selectedCountryObj.capital}}</span></p>
                        </div>
                        <div class="item-info">
                            <p>Top Level Domain: <span v-for="(item, index) in selectedCountryObj.topLevelDomain" :key="`domain-${index}`">{{item}}</span></p>
                            <p>Currencies: <span v-for="(item, index) in selectedCountryObj.currencies" :key="`curr-${index}`">{{item.name}}</span></p>
                            <p>Languages: <span v-for="(item, index) in selectedCountryObj.languages" :key="`lang-${index}`">{{item.name}} </span></p>
                        </div>
                    </div>
                    <div class="countries-border">
                        <h4>Border Countries: </h4>
                        <div class="button">
                            <button v-for="(item, index) in borderCountryArray" :key="`borders-${index}`" @click="$emit('activeState', item)">{{item}}</button>
                        </div>
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
        selectedCountryObj: Object,
        borderCountryArray: Array,
        color: Boolean,
        
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
    left: -200%;
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
                width: 600px;
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
                    width: 100%;
                    display: flex;
                    align-items: flex-start;
                    h4 {
                        color: white;
                        font-weight: 600;
                        font-weight: 14px;
                        width: 190px;
                    }
                    
                    .button {
                        width: 100%;
                        display: flex;
                        justify-content: flex-start;
                        align-items: center;
                        flex-wrap: wrap;
                        
                            button {
                            background-color: $dark-element;
                            border: none;
                            padding: 5px 15px;
                            margin-left: 5px;
                            margin-right: 5px;
                            box-shadow: 0 0 10px rgba(0, 0, 0, 0.139);
                            cursor: pointer;
                            transition: all 0.5s ease;
                            color: $dark-text;
                            margin-bottom: 5px;
                            &:hover {
                                background-color: rgba(255, 255, 255, 0.139);
                            }
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

.light {
    background-color: $light-back;
    .info-container {
        .back {
            button {
                background-color: $light-back;
                color: $light-text;
            }
        }
        .info-country {
            .text {
                .title {
                    h2 {color: $light-text;}
                }
                .info-text {
                    .item-info {
                        p {color: $light-text}

                    }
                }
            .countries-border {
                h4 {color: $light-text}
                .button {
                    button {
                        background-color: $light-back;
                        color: $light-text;
                    }
                }
            }
            }
        }
    }
}

@media screen and (max-width: 375px) {
   
.info {
    .info-container {
        .back {
            button {
                padding: 10px 20px;
                border-radius: 5px;
                i {
                    margin-right: 10px;
                }
                &:hover {
                    background-color: rgba(255, 255, 255, 0.139);
                }
            }
        }

        .info-country {
            margin-top: 30px;
            display: flex;
            flex-direction: column;
            .flag {
                height: 230px;
                width: 100%;
                img {
                    height: 100%;
                    width: 100%;
                }
            }
            .text {
                margin-left: 0px;
                margin-top: 20px;
                padding: 10px;
                width: 600px;
                .title {
                    h2 {
                        color: white;
                        font-weight: 600;
                        font-size: 23px;
                    }
                }
                .info-text {
                    display: flex;
                    flex-direction: column;
                    .item-info {
                        p {color: white; 
                            font-weight: 600; 
                            font-size: 14px;
                            line-height: 20px;
                        span {
                            font-weight: 300;}
                        }
                        &:last-child {margin-right: 0;}
                    }
                }
                .countries-border {
                    margin-top: 20px;
                    width: 50.5%;
                    display: flex;
                    flex-direction: column;
                    .button {
                        margin-top: 5px;
                        button {
                            margin-left: 0;
                            padding: 7px 7px;
                        }
                    }
                    }
                }
            }
        }

    }
}



</style>