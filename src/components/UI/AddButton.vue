<template>
    <div class="component-wrapper" @click="changeFilterClick">
        <button class="filter-button">{{buttonText}}</button>
    </div>
</template>
<script>
    export default {
        name: 'AddButton',
        props: {
            buttonText: String
        },
        methods: {
            changeFilterClick() {
               this.$emit('changeFilterButton')
            }
        }
    }
</script>
