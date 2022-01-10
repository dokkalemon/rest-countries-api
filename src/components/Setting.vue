<template>
     <section class="setting full-width">
        <div class="setting-container container px-30">

            <div class="setting-input">
                <i class="fas fa-search"></i>
                <input type="text" placeholder="Search for a country...">
            </div>

            <select name="" id="">
                <option selected hidden>Filter by Region</option>
                <option value="africa">Africa</option>
                <option value="america">America</option>
                <option value="asia">Asia</option>
                <option value="europe">Europe</option>
                <option value="oceania">Oceania</option>
            </select>
        </div>
    </section>   






</template>

<script>
export default {
    name: 'Setting'
}
</script>

<style scoped lang="scss"> 
//import var.scss
@import '../styles/var.scss';

    .setting-container {
        height: 55px;
        margin-top: 45px;
        margin-bottom: 45px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        .setting-input {
            height: 100%;
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
            }
        }
        select {
            height: 100%;
            width: 185px;
            background-color: $dark-element;
            border: none;
            border-radius: 10px;padding: 10px;
            color: $dark-text;
            font-size: 14px;
        }
    }
</style>