<template>
    <header class="full-width" :class="{light: color}">
        <div class="header container px-30">
            <h2>Where in the world?</h2>
            <button type="button" @click="$emit('colorChange', true)" v-show="color === false"><i class="fas fa-sun"></i> Light Mode</button>
            <button type="button" @click="$emit('colorChange', true)" v-show="color === true"><i class="fas fa-moon"></i> Dark Mode</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        color: Boolean
    }

}
</script>

<style scoped lang="scss">
//import var.scss
@import '../styles/var.scss';

    header {
        background-color: $dark-element;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.413);
        position: fixed;
        top: 0; 
        z-index: 999;
        .header {
            height: 80px;
            display: flex;
            align-items: center;
            h2 {
                color: $dark-text;
                font-weight: 600;
                flex-grow: 1;
            }
            button {
                background-color: transparent;
                border: none;
                color: $dark-text;
                font-size: 16px;
                cursor: pointer;
                padding: 10px;
                transition: all 0.5s ease;
                border-radius: 20px;
                &:hover {
                    background-color: rgba(255, 255, 255, 0.036);
                }
            }
        }
    }

    .active {
        background-color: $light-element;
        h2 {
            color: $light-text !important;
        }
        button {
            color: $light-text !important;
        }
    }

    .light {
        background-color: $light-back;
        .header {
            h2 {
            color: $light-text
            }
            button {
                color: $light-text;
            }
        }
    }




@media screen and (max-width: 375px) {
    header {
        .header {
            h2 {
                font-size: 18px;
            }
        }
    }
}

</style>