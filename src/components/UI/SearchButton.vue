<template>
    <div class="component-wrapper">
        <button type="submit" class="search-button">{{buttonText}}</button>
    </div>
</template>
<script>
    export default {
      name: 'SearchButton',
      props: {
        buttonText: String
      }
    }
</script>
