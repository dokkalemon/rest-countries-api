<template>
    <header class="full-width">
        <div class="header container px-30">
            <h2>Where in the world?</h2>
            <button><i class="fas fa-sun"></i> Light Mode</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    components: {
        
    }
}
</script>

<style scoped lang="scss">
//import var.scss
@import '../styles/var.scss';

    header {
        background-color: $dark-element;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.413);
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
</style>