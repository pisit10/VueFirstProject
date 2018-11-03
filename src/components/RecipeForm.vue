<template>
    <div>
        <form @submit.prevent="" class="">
        <!-- Form Name -->
        <legend>Receipt Form</legend>
          <!--<pre>
              {{receipe}}
          </pre>-->
        
        <!-- Text input-->
        <div class="form-group row">
        <label class="col-md-4 control-label" for="txtTitle">Title</label>  
        <div class="col-md-4">
        <input id="txtTitle" name="Title" type="text" v-model="receipe.title" class="form-control input-md">
            
        </div>
        </div>

        <!-- Text input-->
        <div class="form-group row">
        <label class="col-md-4 control-label" for="txtimg_url">Image Url</label>  
        <div class="col-md-4">
        <input id="txtimg_url" name="imgUrl" type="text" v-model="receipe.image_url" class="form-control input-md">
            
        </div>
        </div>

        <!-- Text input-->
        <div class="form-group row">
        <label class="col-md-4 control-label" for="txtDesc">Description</label>  
        <div class="col-md-4">
        <input id="txtDesc" name="description" type="text" v-model="receipe.description" class="form-control input-md">
            
        </div>
        </div>

        
        <div class="row" >
            <div class="col-8" >
                <button class="btn btn-primary float-right" @click="addIngredient" >
                    <i class="fa fa-plus-circle"></i> more Ingredient
                </button>
          </div>
        </div>
      
        <!-- Text input-->
        <div class="form-group row">
        <label class="col-md-4 control-label" for="textinput">Ingredient</label>  
        <div class="col-md-4"> 
            <div v-for="(ingredient,index) in receipe.ingredient" :key="index" >
                <input v-model="receipe.ingredient[index]" type="text" class="form-control input-md">
            </div>
        </div>
        </div>

        <!-- Button (Double) -->
        <div class="form-group row">
        <label class="col-md-4 col-lg-4 control-label" for="submit-btn"></label>
        <div class="col-md-4 col-lg-8">
            <button id="submit-btn" name="submit-btn" class="btn btn-success" @click="save">Submit </button>
            <button id="cancel-btn" name="cancel-btn" class="btn btn-danger">Cancel </button>
        </div>
        </div>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                receipe: {
                    title: '',
                    description : '',
                    image_url : '',
                    ingredient : ['']
                }
            }
        },
        methods: {
            addIngredient() {
                this.receipe.ingredient.push('')
            },
            save()
            {
                //alert("saveReceipe");
                this.$emit('saveReceipe',this.receipe)
            }
        },
    }
</script>

<style scoped>

</style>