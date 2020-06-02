<template>
    <div id="app">
        <search-form @sendForm="onSendForm" :form-data="formData"
                     :name-search="nameSearch" :filter-type="filterType"
                     @changeFilter="changeFilterTypeHandler($event)"/>
        <settings-block @changeFilterType="changeFilterTypeHandler($event)" :filter-type="filterType"
                        @changeSearchType="changeSearchTypeHandler($event)"/>

        <div v-if="searchResults" class="ml-30 mt-30">
            <h3>Поисковый запрос:</h3>
            <pre>{{formData}}</pre>
        </div>
    </div>
</template>

<script>
    import SearchForm from './components/SearchForm.vue'
    import SettingsBlock from './components/SettingsBlock.vue'

    export default {
        name: 'App',
        components: {
            SettingsBlock,
            SearchForm
        },
        data() {
            return {
                nameSearch: true,
                filterType: 'priceFilter',
                formData: {
                    propertyName: null,
                    city: null,
                    dealType: null,
                    propertyType: null,
                    priceFilter: {
                        priceFrom: null,
                        priceTo: null,
                        currency: null
                    },
                    areaFilter: {
                        areaFrom: null,
                        areaTo: null
                    },
                },
                searchResults: false
            }
        },
        methods: {
            changeSearchTypeHandler(data) {
                this.nameSearch = data.nameSearch;
                this.searchResults = false;
                if (this.nameSearch) {
                    this.formData = {
                        propertyName: null,
                        city: null,
                        dealType: null,
                        propertyType: null,
                        priceFilter: {
                            priceFrom: null,
                            priceTo: null,
                            currency: null
                        },
                        areaFilter: {
                            areaFrom: null,
                            areaTo: null
                        },
                    }
                }
            },
            changeFilterTypeHandler(data) {
                this.filterType = data.filterType
            },
            onSendForm() {
                this.searchResults = true;
            }
        }
    }
</script>

<style>
    @import "assets/reset.css";
    @import "assets/style.css";
</style>
