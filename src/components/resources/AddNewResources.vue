<template>
       <base-dialog v-if ="inputIsInvalid"  title="Invalid Input"  @close = "cancelError">
              <template #default>
                     <p>Ooops! It seems one of your input is wrong</p>
                     <p>Please check your inputs and enter a few valid characters</p>
              </template>
              <template #actions>
                     <base-button  @click="cancelError">Noted. Thanks.</base-button>
              </template>
       </base-dialog>
       <base-card>
              <form @submit.prevent = "submitData">
                     <div class="form-control">
                            <label for="title">Title</label>
                            <input type="text" id="title" name="title" ref="titleInput">
                     </div>
                     <div class="form-control">
                            <label for="description">Description</label>
                            <textarea name="description" id="description" rows="4" type  ="text" ref="descriptionInput"></textarea> 
                     </div>
                     <div class="form-control">
                            <label for="link">Link</label>
                            <input type="url" name="link"  ref="linkInput">
                     </div>
                     <div class="form-control">
                            <base-button type= "submit">Add Resources</base-button>
                     </div>
              </form>
       </base-card>
</template>

<script>
export default {
       inject: ['addResources'],
       data(){
              return{
                     inputIsInvalid: false,
              }
       },
       methods: {
            submitData(){
                   const enteredTitle = this.$refs.titleInput.value;
                   const enteredDescription = this.$refs.descriptionInput.value;
                   const enteredLink = this.$refs.linkInput.value;
                   if (  
                          enteredTitle.trim() === '' ||  enteredDescription.trim() === '' || enteredLink.trim() === ''){
                          this.inputIsInvalid = true; 
                          return;
                     }

              this.addResources(enteredTitle, enteredDescription, enteredLink)
            },

              cancelError(){
                     this.inputIsInvalid = false;
              }
       }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>