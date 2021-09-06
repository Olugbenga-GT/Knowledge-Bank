<template>
       <TheHeader title="Knowledge Bank"/>
       <the-added-resources></the-added-resources>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue'
import TheAddedResources from './components/resources/TheAddedResources.vue'
export default {

       components: {
          TheAddedResources,
          TheHeader,
       }, 

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {box-sizing: border-box;}
html {font-family: 'Roboto', sans-serif;}
body {margin: 0;}
</style>