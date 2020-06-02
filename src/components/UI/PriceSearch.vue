<template>
    <div class="form-group price-search" style="margin-top: 30px">
        <div class="filters-group" style="display: flex; flex-grow: 1;">
            <input type="text" class="filter-search rl mr-2" placeholder="от" v-model="formData.priceFilter.priceFrom">
            <input type="text" class="filter-search mr-2" placeholder="до">
            <select class="filter-search rr">
                <option>р / месяц</option>
                <option>$ / месяц</option>
            </select>
        </div>
        <div style="display: flex; flex-grow: 2; margin-left: 20px">
            <add-button @changeFilterButton="onChangeFilter" button-text="Добавить метраж" style="width: 100%"/>
        </div>
    </div>
</template>
<script>
    import AddButton from "./AddButton";
    export default {
        name: 'PriceSearch',
        props: {
            formData: Object
        },
        components: {AddButton},
        methods: {
            onChangeFilter(){
                this.$emit('onChangeFilter')
            }
        }
    }
</script>
