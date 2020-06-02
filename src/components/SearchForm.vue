<template>
    <div class="search-form-wrapper">
        <div class="search-form">
            <form @submit.prevent="sendForm">
                <div class="form-group" v-if="nameSearch">
                    <input type="text" class="name-search" v-model="formData.propertyName"
                           placeholder="Введите название объекта (бизнес-центра, торгового центра, новостройки, логопарка)">
                    <search-button button-text="Найти"/>
                </div>
                <div class="filters" v-if="!nameSearch">
                    <div class="form-group with-selectors">
                        <select class="param-selector rl mr-2" v-model="formData.city">
                            <option :value="null" disabled>Выбрать город</option>
                            <option>Москва</option>
                            <option>Новосибирск</option>
                            <option>Омск</option>
                        </select>
                        <select class="param-selector mr-2" v-model="formData.dealType">
                            <option :value="null" disabled>Выбрать тип</option>
                            <option>Купить</option>
                            <option>Продать</option>
                            <option>Снять</option>
                        </select>
                        <select class="param-selector" v-model="formData.propertyType">
                            <option :value="null" disabled>Выбрать тип</option>
                            <option>Офис</option>
                            <option>Квартира</option>
                            <option>Склад</option>
                        </select>
                        <search-button button-text="Найти"/>
                    </div>
                    <div class="form-group price-search mt-30" v-if="filterType === 'priceFilter'">
                        <div class="filters-group filters-left">
                            <input type="text" class="filter-search rl mr-2" placeholder="от"
                                   v-model="formData.priceFilter.priceFrom">
                            <input type="text" class="filter-search mr-2" placeholder="до"
                                   v-model="formData.priceFilter.priceTo">
                            <select class="filter-search rr" v-model="formData.priceFilter.currency">
                                <option :value="null" disabled>Выбрать валюту</option>
                                <option>р / месяц</option>
                                <option>$ / месяц</option>
                            </select>
                        </div>
                        <div class="button-right">
                            <add-button @changeFilterButton="changeFilterHandler('areaFilter')"
                                        button-text="Добавить метраж" class="w-100"/>
                        </div>
                    </div>
                    <div class="form-group area-search mt-30" v-if="filterType === 'areaFilter'">
                        <div class="button-left">
                            <add-button @changeFilterButton="changeFilterHandler('priceFilter')"
                                        button-text="Добавить цену" class="w-100" />
                        </div>
                        <div class="filters-group filters-right" >
                            <input type="text" class="filter-search rl mr-2" placeholder="от"
                                   v-model="formData.areaFilter.areaFrom">
                            <input type="text" class="filter-search" placeholder="до"
                                   v-model="formData.areaFilter.areaFrom">
                            <div class="badge rr">
                                <span>М<sup>2</sup></span>
                            </div>
                        </div>
                    </div>
                </div>
            </form>
        </div>
    </div>
</template>
<script>
    import SearchButton from "./UI/SearchButton";
    import AddButton from "./UI/AddButton";
    export default {
        name: 'SearchFormWrapper',
        components: {SearchButton, AddButton},
        props: {
            nameSearch: Boolean,
            filterType: String,
            formData: Object
        },
        methods: {
            changeFilterHandler(val) {
                this.$emit('changeFilter', {filterType: val})
            },
            sendForm() {
                this.$emit('sendForm')
            }
        }
    }
</script>
