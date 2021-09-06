<template>
       <ul>
              <learning-resource
               v-for= "learningResource in myResources" 
               :key= "learningResource.id"  
               :id = 'learningResource.id'
               :title = 'learningResource.title'
               :description = 'learningResource.description' 
               :link= 'learningResource.link'
                ></learning-resource>
       </ul>
</template>
<script>
import LearningResource from './LearningResource.vue'
export default {
       components:{
              LearningResource
       },
       inject : [ 'myResources' ]
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>