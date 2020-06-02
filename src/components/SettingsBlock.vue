<template>
    <div class="search-settings-block">
        <div class="search-switcher">
            <a :class="{'active-switcher': !nameSearch, 'inactive-switcher': nameSearch}"
               @click="changeSearchType(nameSearch = !nameSearch)">Основной поиск</a>
            <label class="switch">
                <input type="checkbox" v-model="nameSearch" @change="changeSearchType()">
                <span class="slider round"></span>
            </label>
            <a :class="{'active-switcher': nameSearch, 'inactive-switcher': !nameSearch}"
               @click="changeSearchType(nameSearch = !nameSearch)">Искать по названию</a>
        </div>
            <div class="search-selectors" v-if="!nameSearch">
                <a href="#" class="mr-30"
                   :class="{'active-selector': filterType === 'priceFilter',
                   'inactive-selector': filterType !== 'priceFilter'}"
                   @click="changeFilterType('priceFilter')">Цена</a>
                <a href="#" :class="{'active-selector': filterType === 'areaFilter',
                   'inactive-selector': filterType !== 'areaFilter'}" @click="changeFilterType('areaFilter')">Метраж</a>
            </div>
    </div>
</template>
<script>
    export default {
        name: 'SettingsBlock',
        components: {},
        props: {
            filterType: String
        },
        data() {
            return {
                nameSearch: true
            }
        },
        methods: {
            changeSearchType() {
                this.$emit('changeSearchType', {nameSearch: this.nameSearch})
            },
            changeFilterType(filterType) {
                this.$emit('changeFilterType', {filterType: filterType})
            }
        }
    }
</script>
