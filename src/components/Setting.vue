<template>
     <section class="setting full-width" :class="{light: color}">
        <div class="setting-container container px-30">
            <div class="setting-input">
                <i class="fas fa-search"></i>
                <input type="text" placeholder="Search for a country..." v-model="userCountry" @keyup="$emit('filterCountry', userCountry)">
            </div>
            <select name="" id="" v-model="filterContinent" @click="$emit('filteredContinent', filterContinent)">
                <option selected hidden value="" >Filter by Region</option>
                <option value="africa">Africa</option>
                <option value="americas">Americas</option>
                <option value="asia">Asia</option>
                <option value="europe">Europe</option>
                <option value="oceania">Oceania</option>
            </select>
        </div>
    </section>   
</template>

<script>
export default {
    name: 'Setting',
    props: {
        color: Boolean,
    },

    data() {
        return {
            filterContinent: '',
            userCountry: '',
        }
    }
}

</script>

<style scoped lang="scss"> 
//import var.scss
@import '../styles/var.scss';

    .setting-container {
        margin-top: 45px;
        margin-bottom: 45px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-top: 80px;
        .setting-input {
            height: 55px;
            width: 450px;
            border-radius: 10px;
            background-color: $dark-element;
            display: flex;
            align-items: center;
            
            i {
                margin: 0 10px 0 30px;
                font-size: 16px;
                color: $dark-text;
            }
            input {
                background-color: transparent;
                border: none;
                outline: none;
                color: $dark-text;
                font-size: 14px;
                width: 100%;height: 100%;
            }
        }
        select {
            height: 55px;
            width: 185px;
            background-color: $dark-element;
            border: none;
            border-radius: 10px;
            padding: 15px;
            color: $dark-text;
            font-size: 14px;
        }
    }

    .active {
        .setting-container {
            .setting-input {
                background-color: $light-element;
                i {
                    color: $light-text;
                }
                input {
                    color: $light-text;
                }
            }

            select {
                background-color: $light-element;
                color: $light-text;
            }
        }
    }

.light {
    background-color: $light-back;

    .setting-input {
        background-color: $light-back;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.146);
        i {
            color: $light-text;
        }
        input {
            color: $light-text;
        }

    }
        select {
            background-color: $light-back;
            color: $light-text;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.146);
        }
}

    @media screen and (max-width: 375px) {
    .setting-container {
        flex-direction: column;
        align-items: flex-start;
        .setting-input {
            margin-bottom: 50px;
            width: 100%;
        }
        
    }
}
</style>