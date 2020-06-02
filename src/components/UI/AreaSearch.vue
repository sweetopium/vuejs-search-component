<template>
    <div class="form-group area-search" style="margin-top: 30px">
        <div style="display: flex; flex-grow: 1; margin-right: 20px">
            <add-button @changeFilterButton="onChangeFilter" button-text="Добавить цену" style="width: 100%"/>
        </div>
        <div class="filters-group" style="display: flex;">
            <input type="text" class="filter-search rl mr-2" placeholder="от">
            <input type="text" class="filter-search" placeholder="до">
            <div class="badge rr">
                <span>М<sup>2</sup></span>
            </div>
        </div>


    </div>
</template>
<script>
    import AddButton from "./AddButton";
    export default {
        name: 'AreaSearch',
        components: {AddButton},
        methods: {
            onChangeFilter(){
                this.$emit('onChangeFilter')
            }
        }
    }
</script>
