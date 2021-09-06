<template>
       <base-card>
              <base-button @click = "setSelectedTab('stored-resources')">Stored Resources</base-button>
              <base-button @click = "setSelectedTab('add-new-resources')">Add Resource</base-button>
       </base-card>
       <component :is = "selectedTab "></component>
</template>

<script>
       import StoredResources from './StoredResources'
       import AddNewResources from './AddNewResources'
export default {
       data(){
              return {
                     selectedTab: 'stored-resources',
                     storedResources:[
                            { id : 'official-guide',
                             title: 'Official Guide',
                            description: 'The official Vue.js documentation',
                            link: 'https://vuejs.org' 
                            },
                            { id : 'google-know-how',
                             title: 'How to optimize google',
                            description: 'The  official know-how tool for optimizing and monetizing google activity',
                            link: 'https://google.com' },
                     ],
                     
              }
       },
       provide(){
              return{
                     myResources: this.storedResources,
                     addResources: this.addResources,
                     deleteResource: this.removeResources,
              };
       },
       components:{
                     StoredResources,
                     AddNewResources,
       },
       methods: {
              setSelectedTab(tab){
                     this.selectedTab = tab;
              },
              addResources(title, description, url){
                     const newResources = {
                            id : new Date().toISOString(),
                            title: title,
                            description: description,
                            link: url,
                     }
                     this.storedResources.unshift(newResources);
                     this.selectedTab = 'stored-resources'
              },
              removeResources(resId ){
                     // This would work for Provided and Injected Data.
                     const resIndex = this.storedResources.findIndex( res => res.id === resId );
                     this.storedResources.splice(resIndex, 1)


                     // This wouldn't work for P & I Data.  
                     // this.storedResources = this.storedResources.filter(res => res.id !== resId)
              }
       },

}
</script>
<style scoped>

</style>