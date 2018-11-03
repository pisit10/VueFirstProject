<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <!--<HelloWorld msg="Pisit Imlerthiran"/>
    <HelloWorld msg="Pisit Imlerthiran 1"/>
    <HelloWorld msg="Pisit Imlerthiran 2"/>
    <hello-world msg="Pisit Imlerthiran 3"/>
    <button-icon @buttonText="popup" name="Edit" icon="fa fa-edit"/>
    <button-icon name="Delete" icon="fa fa-pen"/>
    <button-icon @buttonText="popup"/>-->
    <navbar></navbar>
    <div class="container">
      <div class="col-md-8"> 
        <button class="btn btn-success" @click="isNew =!isNew">Click</button>
      </div>
      <recipe-form v-if="isNew" @saveReceipe="addRecipe"></recipe-form>
       <input type="text" class="form-control" v-model="searchText">
       <ul>
         <li v-for="(receipe,index) in filterList" :key="index + receipe.title" >
           {{receipe}}

         </li>
       </ul>
       
      <!--<RecipeForm @saveReceipe="addRecipe" />-->
    </div>

  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import ButtonIcon from './components/ButtonIcon.vue'
import Navbar from './layout/navbar.vue';
import RecipeForm from './components/RecipeForm.vue'

export default {
  name: 'app',
  components: {
    /*HelloWorld, ButtonIcon,*/ 
    Navbar, RecipeForm
  },
  data() {
    return {
        receipes : [],
        isNew : false,
        searchText : ''
    }
  },
  mounted()
  {
    if(localStorage.getItem('receipes'))
    {
      this.receipes = JSON.parse(localStorage.getItem('receipes'))
    }
  },
  computed:{
      filterList() // Search
      {
          return this.receipes.filter((value) => {
          return value.title.toLowerCase().indexOf( this.searchText.toLowerCase() ) > -1
        })
      }
  },
  methods: {
    setReceipeStorage() 
    {
       localStorage.setItem('receipes', JSON.stringify(this.receipes))
    },

    addRecipe(receipe)
    {
       //alert(receipe)
       //console.log(receipe);
       this.receipes.push(receipe);
       this.setReceipeStorage();
       this.isNew = false;
    },

    searchRecipe() // not use
    {
        //alert('searchRecipe');
        this.receipes = this.receipes.filter((value) => {
          return value.title.toLowerCase().indexOf( this.searchText.toLowerCase() ) > -1
        })
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
